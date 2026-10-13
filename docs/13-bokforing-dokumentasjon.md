# Bokføring og dokumentasjon

Lønnsdokumentasjonen skal vise ytelser og trekk per mottaker og per utbetaling, og oppbevares i 5 år etter regnskapsåret ([bokføringsforskriften § 5-6](https://lovdata.no/forskrift/2004-12-01-1558/§5-6), [bokføringsloven § 13](https://lovdata.no/lov/2004-11-19-73/§13)). Systemet skal også ha en lettfattelig beskrivelse av egen oppbygging og funksjoner.

**Krav til lønnsdokumentasjonen (§ 5-6, endret fra 1.1.2026)**

- Per mottaker: fødselsnummer, navn, skattekommune og tabellnummer eller trekkprosent. Uten skattekort: bostedskommune per 1.11. året før.
- Ved trekkpålegg: når pålegget ble mottatt, og prosent eller beløp per periode.
- Per periode: utbetalingsdato og om mulig perioden ytelsen gjelder, bruttoytelse, godtgjorte timer, naturalytelser, fradrag etter skattebetalingsloven § 5-9, trekkgrunnlag og foretatt trekk.
- For timelønnede: dato for arbeidet, timer per dag og sum timer.
- Dokumentasjonen skal være utstedt senest når ytelsen kan utbetales.

**Sporbarhet og korrigering**

- Fullstendighet, nøyaktighet, toveis sporbarhet og sikring (bokføringsloven § 4); dokumentert kontrollspor for systemgenererte poster (§ 6).
- Etter fristen rettes feil ved full reversering og ny postering, ikke bare differansen (§ 9). Korrigeringsbilag skal vise årsak og referanse (forskriften § 5-12).
- Lukkede perioder skal være sikret mot endring, og lukkefunksjonen skal beskrives (§ 7-6).
- Lønnsopplysningspliktige ytelser skal kunne spesifiseres per periode og konto, og AGA-pliktige ytelser samlet per sats og sone (§ 3-1 nr. 9).

**Oppbevaring**

| Materiale | Tid | Hjemmel |
| --- | --- | --- |
| Lønnsdokumentasjon, spesifikasjoner og bilag | 5 år etter regnskapsåret | Bokføringsloven § 13 |
| Avtaler og korrespondanse | 3 år og 6 måneder | Bokføringsloven § 13 |
| Dokumentasjon av arbeidede timer | 3 år og 6 måneder | Bokføringsforskriften § 7-3 |
| Elektronisk tilgjengelighet | 3 år og 6 måneder | Bokføringsloven § 13 b |
| Fortegnelse over sikkerhetskopier og beskrivelse av lukkefunksjon | 5 år | Bokføringsforskriften §§ 7-2, 7-6 |

- Sikkerhetskopier skal oppbevares adskilt fra originalen og testes minst én gang i året (§ 7-2).
- Elektronisk materiale kan lagres i EØS, Storbritannia eller Sveits når skattekontoret har fått skriftlig melding (§ 7-5). Lagring i for eksempel USA er ikke dekket.

**Kontoplan og avstemming.** NS 4102 er ikke pålagt, men brukes som standard: 5000 lønn, 5092 feriepenger, 5400 AGA, 2600 forskuddstrekk, 2610 utleggstrekk, 2770 skyldig AGA, 2940 skyldige feriepenger, 1579 refusjon fra NAV. Konto 1950 skattetrekkskonto brukes ikke for 2026. Lønn, AGA og trekk avstemmes mot a-meldingen, tilbakemeldingen (A03) og Skatteetatens avstemmingsrapport, som nå hentes via API.

**Sammenstillingsoppgave.** Hver inntektsmottaker skal få en oppgave over årets ytelser, feriepengegrunnlag og forskuddstrekk innen 1. februar året etter ([skatteforvaltningsforskriften § 7-13-2](https://lovdata.no/forskrift/2016-11-23-1360/§7-13-2)). Trekkpliktig og trekkfri del vises hver for seg.
