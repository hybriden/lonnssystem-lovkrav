# Personvern, sikkerhet og integrasjoner

Lønnsbehandling bygger på arbeidsavtalen og rettslige plikter (GDPR art. 6 nr. 1 b og c), ikke samtykke. Fagforeningsmedlemskap og sykefravær er særlige kategorier som krever art. 9 nr. 2 b og [personopplysningsloven § 6](https://lovdata.no/dokument/NL/lov/2018-06-15-38).

**Personvern**

- Fødselsnummer kan brukes fordi lønn krever sikker identifisering (§ 12), men bør ikke vises unødig, stå i URL-er eller logges.
- Systemet skal ikke lagre diagnoser; sykefravær lagres som perioder og ytelser.
- Lagringsbegrensningen viker for lovpålagt oppbevaring (art. 17 nr. 3 b): lønnsbilag i 5 år, timelister i 3,5 år. HR-opplysninger skal som regel slettes når arbeidsforholdet slutter ([Datatilsynet](https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/personalmappe/)). Systemet må derfor ha sletteregler per datakategori.
- Ansatte har rett til innsyn i alle opplysninger om seg selv (art. 15), normalt innen én måned.
- Tilgang bare ved tjenstlig behov, med logging (art. 32). Databehandleravtale med leverandører (art. 28). Overføring utenfor EØS krever grunnlag etter kap. V, og regnskapsmateriale er uansett begrenset til EØS, Storbritannia og Sveits.
- Vanlig lønnsbehandling krever ikke DPIA, men det bør vurderes ved kobling mot tids- og prestasjonsdata.
- Lønnsslipp til privat e-post må være kryptert som fil, med passord som ikke er fødselsdato. Anbefalt er portal med tofaktor eller digital postkasse ([Datatilsynet](https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/kryptering-lonnsslipp/)).

**Integrasjoner**

| Tjeneste | Grensesnitt | Merknad |
| --- | --- | --- |
| A-melding | Skatteetatens REST-API, filopplasting for store filer, scope `skatteetaten:innrapporteringamelding` | Format v2.3; tilbakemelding via Dialogporten |
| Avstemmingsrapport | API (JSON) | Erstatter A06/A07; ny versjon 11.9.2026 |
| Skattekort | API, scope `skatteetaten:skattekorttilarbeidsgiver` | Inntil 1 000 personer per kall; bare polling fra 15.12.2026 |
| Trekkpålegg | Skatteetatens Trekkpålegg-API | Krever at systemet allerede rapporterer a-melding |
| Inntektsmelding sykepenger | NAV API, scope `nav:helseytelser/sykepenger` | Bare sykepenger |
| Oppgjørsrapport refusjon | NAV API (Altinn 3) | Erstatter K27 |
| Enhetsregisteret | Åpent API | Org.nr., underenheter, kommune for AGA-sone |

Alle Skatteetatens og NAVs tjenester bruker Maskinporten og systembruker i Altinn 3 ([Skatteetaten](https://www.skatteetaten.no/en/our-partners/reetablering-altinn/systemleverandor/oppkobling/), [Digdir](https://samarbeid.digdir.no/altinn/systembruker/2542)). Leverandøren registrerer systemet i Altinns systemregister, søker om scopes og godtar bruksvilkårene; kunden godkjenner systembrukeren. Det finnes ingen formell sertifisering. Testing skjer i Skatteetatens testmiljø med testpersoner fra Tenor.
