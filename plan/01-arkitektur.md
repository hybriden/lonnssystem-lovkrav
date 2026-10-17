# Arkitektur

Lønnssystemet bygges i .NET 10 med PostgreSQL, en ren C#-domenekjerne for alle beregninger, og en React-frontend. Valget ble tatt 17.10.2026 (se [LOGG.md](LOGG.md)). Alternativet var en TypeScript-monorepo etter mønsteret i paperboy; det ble valgt bort fordi `decimal`, XSD-verktøyene og utviklerens erfaring veier tyngre for et lønnssystem.

## Teknologivalg

| Lag | Valg | Hvorfor |
| --- | --- | --- |
| Språk og kjøretid | C# 14 på .NET 10 (LTS) | `decimal` gir eksakt pengeregning. Utvikleren har mange års erfaring og skal gjennomgå det modellene skriver. |
| Domenekjerne | `Lonn.Domain`: rent bibliotek uten I/O, klokke eller database | Alle regler i kartleggingen er funksjoner fra data til data. De testes tabelldrevet uten infrastruktur. |
| Parametre | `Lonn.Parametre`: årsversjonerte satser som data | Satsene i `docs/16-satser-2026.md` endres hvert år og G skifter 1. mai. Kode og satser skal kunne endres uavhengig. |
| Database | PostgreSQL 16 med EF Core 10 og Npgsql | Transaksjoner, delvise unike indekser for invarianter, drift i EØS. Cloudflare D1 og lignende ble valgt bort fordi bokføringsforskriften § 7-5 krever lagring i Norge, EØS, Storbritannia eller Sveits. |
| API | ASP.NET Core Minimal API med OpenAPI | Ett skjema per endepunkt, generert TypeScript-klient til frontend. |
| Integrasjoner | `Lonn.Integrasjoner`: Skatteetaten, NAV, Enhetsregisteret, Maskinporten | Hver klient har et grensesnitt i domenet, en ekte implementasjon og en opptaksbasert testimplementasjon. |
| XML | XSD-genererte klasser og `XmlReaderSettings` med skjemavalidering | A-melding v2.3 er XML med XSD fra Skatteetaten. Meldingen valideres mot XSD før sending. |
| Frontend | React 19, Vite, TypeScript, norsk brukertekst, Liquid Glass-designet fra harmonix | Designsystemet (tokens, radier, typeskala, glass, UI-kit) porteres fra eierens repo hybriden/harmonix i AP-008; se `docs/design.md` i koderepoet. Generert klient fra OpenAPI, så typer ikke drifter. |
| Autentisering | Argon2id, tjenersidesesjoner i cookie, TOTP, rollebasert tilgang | Fødselsnummer, fagforening og sykefravær er sensitive. Ingen JWT i nettleseren. |
| Tester | xUnit, Verify (snapshots), Testcontainers (Postgres), Playwright for e2e | Domenet testes uten infrastruktur. API testes mot ekte Postgres. |
| Drift | Azure i region Norway East: containerbilde (flerstegs), Azure Database for PostgreSQL Flexible Server, Key Vault for nøkler, migrering før oppstart. Docker Compose lokalt. | Data i Norge oppfyller bff. § 7-5 uten melding til skattekontoret. Sikkerhetskopi i egen lagringskonto med uforanderlighet, adskilt fra originalen og testet årlig (bff. § 7-2). Tjenestevalget dokumenteres i en ADR i AP-005. |
| Lint og format | `dotnet format`, analysatorer på `warning as error`, oxlint og oxfmt i `web/` | Null advarsler i CI. |

## Mappestruktur

```
lonnssystem/
  Lonnssystem.slnx
  Directory.Build.props          # nullable, warnings as errors, analysatorer
  Directory.Packages.props       # sentral versjonsstyring
  src/
    Lonn.Domain/                 # regler, verdityper, beregningspipeline
    Lonn.Parametre/              # satser per år, kodelister, sonetabell, trekktabeller
    Lonn.Infrastruktur/          # EF Core, migreringer, revisjonslogg, kryptering
    Lonn.Integrasjoner/          # Maskinporten, a-melding, skattekort, NAV, Brreg
    Lonn.Api/                    # Minimal API, autentisering, OpenAPI
  web/                           # React + Vite + TS
  tests/
    Lonn.Domain.Tests/
    Lonn.Parametre.Tests/
    Lonn.Infrastruktur.Tests/
    Lonn.Integrasjoner.Tests/
    Lonn.Api.Tests/
  docs/
    adr/                         # arkitekturbeslutninger
    invariants/                  # reglene som ikke skal brytes, med begrunnelse
  docker-compose.yml
```

Avhengighetsretning: `Api → Infrastruktur → Domain`, `Api → Integrasjoner → Domain`, `Domain → Parametre`. `Domain` refererer ingen andre prosjekter enn `Parametre` og ingen NuGet-pakker utover BCL. Dette håndheves med en arkitekturtest (NetArchTest) i `Lonn.Domain.Tests`.

## Prinsipper som ikke skal brytes

Disse er utgangspunktet for `docs/invariants/` i koderepoet. AP-001 utdyper dem med begrunnelse og eksempler.

**Penger.** Alle beløp er `decimal` pakket i verdityper (`Belop`, `Sats`, `Prosent`). Avrunding skjer bare på navngitte steder med lovhjemmel: `RundNedTilHelKrone` (sbf. § 5-10-4 for trekkgrunnlag), `RundTilNaermesteKrone` for rapportering. Ingen `double` i `Lonn.Domain`.

**Datoer.** `DateOnly` og `YearMonth`-verditype. Ingen `DateTime.Now` i domenet; klokken er en avhengighet. Alle fristberegninger går gjennom én norsk virkedagskalender med bevegelige helligdager.

**Kontantprinsippet.** Rapporteringsperioden for en ytelse er utbetalingsmåneden. Utbetalingsdatoen er obligatorisk på hver lønnskjøring og må ligge i perioden (regel F527). Etterbetaling rapporteres når den betales; feil rettes i måneden feilen gjaldt.

**Lønnsarten styrer alt.** Hver lønnsart har eksplisitte flagg: trekkpliktig, AGA-pliktig, feriepengegrunnlag, pensjonsgivende, OTP-grunnlag, utleggstrekkgrunnlag, tabell- eller prosenttrekk, konto, og a-meldingens fordel og beskrivelse. Ingen beregning ser på navnet på lønnsarten.

**Årsversjonerte parametre.** Hver sats har gyldig-fra-dato. Oppslag skjer alltid med dato, aldri med «gjeldende». G-avhengige grenser (6G, 7,1G, 12G, 3/5G, 1,5G) beregnes fra G på den datoen regelen peker på, som er forskjellig for feriepenger (31.12 i opptjeningsåret) og OTP (utbetalingsdato).

**Lukkede perioder og reversering.** En rapportert periode er låst. Retting etter låsing skjer ved full reversering og ny postering med årsak og referanse (bokføringsloven § 9, bff. § 5-12), aldri ved å endre en post. Revisjonsloggen er append-only.

**Beregningen er en funksjon.** En lønnskjøring beregnes fra (ansattdata, lønnsarter, parametre, skattekort, akkumulatorer per 1. i måneden) til et resultat. Samme input gir samme output, og resultatet lagres sammen med inputene som ble brukt. Da kan en kjøring fra 2026 beregnes på nytt i 2029 under bokettersyn.

**Trekkrekkefølgen** er fast: brutto → fradrag etter sktbl. § 5-9 (pensjon, fagforening) → trekkgrunnlag → forskuddstrekk → utleggstrekk etter dekningsloven § 2-8 → avtalte trekk etter aml. § 14-15 → netto. Forskuddstrekket tas bare så langt kontantlønnen rekker; mangler dekning, varsles det.

**Personvern.** Fødselsnummer krypteres i databasen, maskeres i brukerflaten og står aldri i URL-er eller logger. Fagforeningsmedlemskap og fravær har egne roller. Ingen diagnoser lagres. Sletteregler per datakategori, med bokføringsplikt foran slettekrav.

**Én opplysningspliktig per lønnskjøring, flere per installasjon.** Systemet er flerkunde fra dag én (regnskapsførere har mange klienter). Alle tabeller har `ArbeidsgiverId`, og hver spørring filtrerer på den. Bekreftet av eieren 17.10.2026.

**Ett designsystem, felles komponenter.** Brukerflaten bygges av ett kit (`web/src/components/ui`, portert fra harmonix) og områdekomponenter over det (`web/src/components/app`). En side lager ikke sin egen knapp, tabell eller dialog. Trengs noe nytt, utvides kitet med en variant (`cva`-prop), ikke med en nesten lik komponent ved siden av. Sider importerer ikke Radix eller sonner direkte; det gjør bare kitet. Begrunnelse fra eieren 17.10.2026: en haug med nesten like komponenter er det dyreste å vedlikeholde.

**Dependency injection og riktig granularitet i backend.** Alle avhengigheter kommer gjennom konstruktøren fra `Microsoft.Extensions.DependencyInjection`; ingen `static`-tilstand, ingen service locator, ingen `new` av en tjeneste inne i en annen. Hvert prosjekt registrerer seg selv med én utvidelsesmetode (`AddLonnDomain()`, `AddLonnInfrastruktur()`, `AddLonnIntegrasjoner()`), og containeren bygges med `ValidateOnBuild` og `ValidateScopes` i en test. En tjeneste har ett ansvar og én grunn til å endre seg: én beregner per fagområde (`ForskuddstrekkBeregner`, `ArbeidsgiveravgiftBeregner`, `FeriepengeBeregner`) som `LonnskjoringBeregner` komponerer, ikke én tjeneste per tabell (anemisk) og ikke én tjeneste som gjør alt. Overstiger en tjeneste fem avhengigheter, deles den. Grensesnitt der det finnes to implementasjoner (ekte og opptak for integrasjoner, klokke, kryptering); konkrete klasser for rene beregnere. Ingen generiske repositorier over EF Core: `DbContext` er arbeidsenheten, og lesing skjer i små, navngitte spørringsklasser per bruksområde. Ett valideringsmønster i hele API-et, ikke tre.

## Testing

- `Lonn.Domain.Tests` er tabelldrevne: ett testtilfelle per eksempel i kartleggingen (for eksempel 1 012 kr mot 693 kr gir 319 kr trekkpliktig). Navnene på testene nevner hjemmelen.
- Hver bugfix starter med en test som gjenskaper feilen og feiler før rettingen.
- AP-901 bygger et «gullår»: en testbedrift med ti ansatte kjøres gjennom hele 2026 og sammenlignes mot et fasitdokument. Alle senere endringer må holde gullåret grønt.
- Integrasjoner testes mot opptak (fixtures) i CI og mot Skatteetatens testmiljø med Tenor-testpersoner i AP-904.

## Konvensjoner

- Kode, identifikatorer og commits på engelsk. Domenebegreper som har et norsk juridisk navn beholder det norske navnet som identifikator (`Forskuddstrekk`, `Arbeidsgiveravgift`, `Feriepengegrunnlag`), fordi det er dét revisor og Skatteetaten bruker. Brukertekst på norsk.
- Ingen `enum` i grensesnitt mot frontend; strengkoder fra kodelistene.
- Resultatobjekter ved grenser (`Result<T, Feil>`), unntak bare når kallet ikke kan fortsette.
- Hver pakke i planen ender med lint, build, test grønt, og med `docs/invariants/` oppdatert når den innfører en ny regel.
