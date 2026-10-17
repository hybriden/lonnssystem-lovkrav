# Arbeidspakker

Alle pakkene, gruppert i faser. En pakke kan startes når pakkene i «Avhenger av» er ferdige. Fasene er en anbefalt rekkefølge, ikke en sperre: pakker uten innbyrdes avhengighet kan gå parallelt i egne økter.

Kolonnen «Str» er størrelse: S under en dag, M en til tre dager, L mer enn tre dager for én økt. Kompleksitetsklassene (K1–K4) og modellene er forklart i [03-modelltildeling.md](03-modelltildeling.md). Status vedlikeholdes i hver pakkefil.

## Fase 0: Fundament

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-000](arbeidspakker/AP-000.md) | Repo, verktøykjede og CI | K4 | Fable 5.1 | Fable 5.1 | – | S |
| [AP-001](arbeidspakker/AP-001.md) | Domenemodell, invarianter og ADR-er | K4 | Fable 5.1 | Fable 5.1 + menneske | AP-000 | M |
| [AP-002](arbeidspakker/AP-002.md) | Primitiver: beløp, datoer, virkedagskalender, perioder | K2 | Sonnet 5.5 | Opus 5.5 | AP-001 | S |
| [AP-003](arbeidspakker/AP-003.md) | Parameterregister med årsversjonering og G-skifte | K2 | Sonnet 5.5 | Opus 5.5 | AP-002 | S |
| [AP-004](arbeidspakker/AP-004.md) | Satser 2026 og 2027-forslag som data | K1 | Haiku 5.5 | Sonnet 5.5 | AP-003 | S |
| [AP-005](arbeidspakker/AP-005.md) | Databaseskjema, migreringer og revisjonslogg | K3 | Opus 5.5 | Fable 5.1 | AP-001 | M |
| [AP-006](arbeidspakker/AP-006.md) | Autentisering, roller og tilgangslogg | K3 | Opus 5.5 | Fable 5.1 | AP-005 | M |
| [AP-007](arbeidspakker/AP-007.md) | API-skjelett: Minimal API, feilmodell, OpenAPI, generert klient | K2 | Sonnet 5.5 | Opus 5.5 | AP-006 | S |
| [AP-008](arbeidspakker/AP-008.md) | Web-skjelett: React, ruting, innlogging, designtokens, maskering | K2 | Sonnet 5.5 | Opus 5.5 | AP-007 | M |
| [AP-009](arbeidspakker/AP-009.md) | Avklaring av åpne juridiske spørsmål | K4 | Fable 5.1 | menneske | – | M |

## Fase 1: Grunndata

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-101](arbeidspakker/AP-101.md) | Arbeidsgiver og underenheter med oppslag i Enhetsregisteret | K2 | Sonnet 5.5 | Opus 5.5 | AP-007, AP-102 | M |
| [AP-102](arbeidspakker/AP-102.md) | AGA-sonetabell per kommune og sektorunntak som data | K1 | Haiku 5.5 | Sonnet 5.5 | AP-003 | S |
| [AP-103](arbeidspakker/AP-103.md) | Ansattregister og identiteter (fnr, D-nummer, utenlandsk ID) | K2 | Sonnet 5.5 | Opus 5.5 | AP-006, AP-007 | M |
| [AP-104](arbeidspakker/AP-104.md) | Arbeidsforhold med historikk, permisjon og permittering | K3 | Opus 5.5 | Fable 5.1 | AP-103, AP-105 | L |
| [AP-105](arbeidspakker/AP-105.md) | Kodelister: a-melding, SSB yrkeskatalog, sluttårsaker m.m. | K1 | Haiku 5.5 | Sonnet 5.5 | AP-003 | M |
| [AP-106](arbeidspakker/AP-106.md) | Lønnsartregister med klassifisering og standardsett | K2 | Sonnet 5.5 | Opus 5.5 | AP-105 | M |
| [AP-107](arbeidspakker/AP-107.md) | Arbeidsavtale etter aml. § 14-6 med endringslogg | K2 | Sonnet 5.5 | Opus 5.5 | AP-104 | S |
| [AP-108](arbeidspakker/AP-108.md) | Allmenngjorte minstesatser og kontroll | K2 | Sonnet 5.5 | Opus 5.5 | AP-003, AP-104 | S |

## Fase 2: Beregningsmotor

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-201](arbeidspakker/AP-201.md) | Beregningspipeline for en lønnskjøring | K3 | Opus 5.5 | Fable 5.1 | AP-002, AP-003, AP-106 | M |
| [AP-202](arbeidspakker/AP-202.md) | Forskuddstrekk: tabell, prosent, frikort, trekkfrie perioder | K3 | Opus 5.5 | Fable 5.1 | AP-201, AP-203 | L |
| [AP-203](arbeidspakker/AP-203.md) | Import av trekktabeller fra Skatteetaten | K1 | Haiku 5.5 | Sonnet 5.5 | AP-003 | S |
| [AP-204](arbeidspakker/AP-204.md) | Kildeskatt på lønn (PAYE), Svalbard og Jan Mayen | K2 | Sonnet 5.5 | Opus 5.5 | AP-202 | S |
| [AP-205](arbeidspakker/AP-205.md) | Arbeidsgiveravgift og finansskatt | K3 | Opus 5.5 | Fable 5.1 | AP-201, AP-101 | L |
| [AP-206](arbeidspakker/AP-206.md) | Feriepenger: opptjening, avsetning og utbetaling | K3 | Opus 5.5 | Fable 5.1 | AP-201, AP-202 | L |
| [AP-207](arbeidspakker/AP-207.md) | Naturalytelser: bil, EK, rentefordel, kost og losji, forsikring, aksjer | K2 | Sonnet 5.5 | Opus 5.5 | AP-201, AP-208 | M |
| [AP-208](arbeidspakker/AP-208.md) | Akkumulatorer per ansatt og år | K2 | Sonnet 5.5 | Opus 5.5 | AP-201 | S |
| [AP-209](arbeidspakker/AP-209.md) | Reiseregning og utgiftsgodtgjørelser | K2 | Sonnet 5.5 | Opus 5.5 | AP-201 | M |
| [AP-210](arbeidspakker/AP-210.md) | Pensjon: OTP, eget innskudd, AFP-grunnlag, SPK og KLP | K2 | Sonnet 5.5 | Opus 5.5 | AP-201 | S |
| [AP-211](arbeidspakker/AP-211.md) | Overtid, arbeidstidsgrenser og timeregister | K2 | Sonnet 5.5 | Opus 5.5 | AP-104, AP-106 | M |
| [AP-212](arbeidspakker/AP-212.md) | Trekk i lønn etter aml. § 14-15, forskudd og lån | K2 | Sonnet 5.5 | Opus 5.5 | AP-201 | S |

## Fase 3: Lønnskjøring, dokumentasjon og regnskap

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-301](arbeidspakker/AP-301.md) | Lønnskjøring: livssyklus og statusmaskin | K3 | Opus 5.5 | Fable 5.1 | AP-202, AP-205, AP-206 | L |
| [AP-302](arbeidspakker/AP-302.md) | Lønnsslipp og lønnsdokumentasjon etter bff. § 5-6 | K2 | Sonnet 5.5 | Opus 5.5 | AP-301 | M |
| [AP-303](arbeidspakker/AP-303.md) | Kontering, kontoplan og regnskapseksport (NS 4102, SAF-T) | K3 | Opus 5.5 | Fable 5.1 | AP-301 | L |
| [AP-304](arbeidspakker/AP-304.md) | Periodelås, reversering og korrigering | K3 | Opus 5.5 | Fable 5.1 | AP-301, AP-303 | L |
| [AP-305](arbeidspakker/AP-305.md) | Utbetalingsfil til bank (ISO 20022 pain.001) | K2 | Sonnet 5.5 | Opus 5.5 | AP-301 | S |
| [AP-306](arbeidspakker/AP-306.md) | Betalingsoppdrag for trekk og AGA med KID og forfall | K2 | Sonnet 5.5 | Opus 5.5 | AP-002, AP-301 | M |

## Fase 4: Rapportering og Skatteetaten

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-401](arbeidspakker/AP-401.md) | Maskinporten, systembruker og Altinn systemregister | K3 | Opus 5.5 | Fable 5.1 | AP-006 | M |
| [AP-402](arbeidspakker/AP-402.md) | Skattekort via API | K3 | Opus 5.5 | Fable 5.1 | AP-401, AP-103 | M |
| [AP-403](arbeidspakker/AP-403.md) | A-melding v2.3: bygger med erstatnings- og tilleggsmelding | K3 | Opus 5.5 | Fable 5.1 | AP-301, AP-104, AP-205 | L |
| [AP-404](arbeidspakker/AP-404.md) | A-melding: valideringsregler før innsending | K2 | Sonnet 5.5 | Opus 5.5 | AP-403 | M |
| [AP-405](arbeidspakker/AP-405.md) | A-melding: innsending, Dialogporten og tilbakemelding (A03) | K3 | Opus 5.5 | Fable 5.1 | AP-401, AP-404 | L |
| [AP-406](arbeidspakker/AP-406.md) | Avstemming mot A03, betalinger og avstemmingsrapport | K2 | Sonnet 5.5 | Opus 5.5 | AP-303, AP-306, AP-405 | M |
| [AP-407](arbeidspakker/AP-407.md) | Fristkalender og varsling | K2 | Sonnet 5.5 | Opus 5.5 | AP-002 | S |

## Fase 5: Fravær og NAV

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-501](arbeidspakker/AP-501.md) | Fraværsregister | K2 | Sonnet 5.5 | Opus 5.5 | AP-104 | M |
| [AP-502](arbeidspakker/AP-502.md) | Arbeidsgiverperiode og egenmelding | K3 | Opus 5.5 | Fable 5.1 | AP-501 | M |
| [AP-503](arbeidspakker/AP-503.md) | Sykepengegrunnlag og refusjon | K3 | Opus 5.5 | Fable 5.1 | AP-502, AP-301 | M |
| [AP-504](arbeidspakker/AP-504.md) | Inntektsmelding for sykepenger via NAVs API | K3 | Opus 5.5 | Fable 5.1 | AP-401, AP-503 | L |
| [AP-505](arbeidspakker/AP-505.md) | NAVs oppgjørsrapport og refusjonsavstemming | K2 | Sonnet 5.5 | Opus 5.5 | AP-205, AP-303, AP-504 | M |
| [AP-506](arbeidspakker/AP-506.md) | Omsorgsdager, foreldrepenger og permittering | K2 | Sonnet 5.5 | Opus 5.5 | AP-501, AP-104 | M |
| [AP-507](arbeidspakker/AP-507.md) | Sykefraværsstatistikk per kvartal | K1 | Haiku 5.5 | Sonnet 5.5 | AP-501 | S |

## Fase 6: Tredjepartstrekk og særgrupper

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-601](arbeidspakker/AP-601.md) | Utleggstrekk: samordnet og gammelt regelverk side om side | K3 | Opus 5.5 | Fable 5.1 | AP-201, AP-306, AP-401 | L |
| [AP-602](arbeidspakker/AP-602.md) | Fagforeningskontingent | K2 | Sonnet 5.5 | Opus 5.5 | AP-201, AP-006 | S |
| [AP-603](arbeidspakker/AP-603.md) | Særgrupper: utenlandske, A1, Svalbard, sjøfolk, styre, barn, dødsfall, valuta | K3 | Opus 5.5 | Fable 5.1 | AP-104, AP-204, AP-205, AP-207, AP-212 | L |

## Fase 7: Personvern og årsavslutning

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-701](arbeidspakker/AP-701.md) | Sletteregler, oppbevaring og innsyn | K3 | Opus 5.5 | Fable 5.1 | AP-005, AP-006 | M |
| [AP-702](arbeidspakker/AP-702.md) | Ansattportal med lønnsslipp og innsyn | K2 | Sonnet 5.5 | Opus 5.5 | AP-302, AP-006, AP-701 | M |
| [AP-703](arbeidspakker/AP-703.md) | Sammenstillingsoppgave innen 1. februar | K2 | Sonnet 5.5 | Opus 5.5 | AP-301, AP-403 | S |
| [AP-704](arbeidspakker/AP-704.md) | Lønnskartlegging etter kjønn | K2 | Sonnet 5.5 | Opus 5.5 | AP-301, AP-104 | S |
| [AP-705](arbeidspakker/AP-705.md) | Årsavslutning og årsskifte | K2 | Sonnet 5.5 | Opus 5.5 | AP-003, AP-402, AP-206 | M |
| [AP-706](arbeidspakker/AP-706.md) | Systembeskrivelse, lukkefunksjon og kontrollspor | K1 | Haiku 5.5 | Sonnet 5.5 | AP-304 | S |

## Fase 8: Brukerflate

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-801](arbeidspakker/AP-801.md) | UI: arbeidsgiver, ansatte, arbeidsforhold og avtaler | K2 | Sonnet 5.5 | Opus 5.5 | AP-008, AP-101, AP-103, AP-104, AP-107 | L |
| [AP-802](arbeidspakker/AP-802.md) | UI: lønnsarter, satser, lønnskjøring og lønnsslipp | K2 | Sonnet 5.5 | Opus 5.5 | AP-008, AP-301, AP-302 | L |
| [AP-803](arbeidspakker/AP-803.md) | UI: a-melding, betalinger, frister og avstemming | K2 | Sonnet 5.5 | Opus 5.5 | AP-008, AP-405, AP-406, AP-407 | M |
| [AP-804](arbeidspakker/AP-804.md) | UI: fravær, inntektsmelding og refusjon | K2 | Sonnet 5.5 | Opus 5.5 | AP-008, AP-502, AP-504, AP-505, AP-506 | M |
| [AP-805](arbeidspakker/AP-805.md) | UI: trekk, særgrupper og personvern | K2 | Sonnet 5.5 | Opus 5.5 | AP-008, AP-601, AP-602, AP-603, AP-701 | M |

## Fase 9: Kvalitet

| ID | Pakke | Kl | Implementeres av | Gjennomgås av | Avhenger av | Str |
| --- | --- | --- | --- | --- | --- | --- |
| [AP-901](arbeidspakker/AP-901.md) | Gullåret: ett helt lønnsår for en testbedrift | K3 | Opus 5.5 | Fable 5.1 | AP-304, AP-306, AP-403, AP-503, AP-601 | L |
| [AP-902](arbeidspakker/AP-902.md) | Sikkerhets- og personverngjennomgang | K4 | Fable 5.1 | menneske | AP-006, AP-401, AP-701, AP-901 | M |
| [AP-903](arbeidspakker/AP-903.md) | Ytelse og last | K2 | Sonnet 5.5 | Opus 5.5 | AP-301, AP-403 | S |
| [AP-904](arbeidspakker/AP-904.md) | Integrasjonstest i Skatteetatens og NAVs testmiljø med Tenor | K3 | Opus 5.5 | Fable 5.1 | AP-402, AP-405, AP-504 | M |

## Anbefalt rekkefølge

Bølgene er beregnet fra avhengighetene i tabellen: en pakke står i bølgen etter den seneste pakken den avhenger av. Alle pakker i samme bølge kan gå parallelt i egne økter. Beregnes på nytt når avhengigheter endres.

| Bølge | Pakker | Merknad |
| --- | --- | --- |
| 1 | AP-000, AP-009 | AP-000 er gjort. AP-009 går parallelt med alt og bør være ferdig før pakkene den blokkerer. |
| 2 | AP-001 | AP-001 er det alle andre bygger på. Ingen K2- eller K3-pakke starter før den er ferdig. |
| 3 | AP-002, AP-005 |  |
| 4 | AP-003, AP-006, AP-407 | AP-003 definerer parameterformatet som datapakkene i neste bølge fyller. |
| 5 | AP-004, AP-007, AP-102, AP-105, AP-203, AP-401, AP-701 | Datapakkene (K1) kan gå i egne, billige økter samtidig. |
| 6 | AP-008, AP-101, AP-103, AP-106 |  |
| 7 | AP-104, AP-201, AP-402 |  |
| 8 | AP-107, AP-108, AP-202, AP-205, AP-208, AP-209, AP-210, AP-211, AP-212, AP-501, AP-602 | Forskuddstrekk (AP-202) er den lengste pakken i fase 2 og bør starte først i bølgen. |
| 9 | AP-204, AP-206, AP-207, AP-502, AP-506, AP-507, AP-801 |  |
| 10 | AP-301, AP-603, AP-705 | Lønnskjøringen trenger trekk, AGA og feriepenger. |
| 11 | AP-302, AP-303, AP-305, AP-306, AP-403, AP-503, AP-704 |  |
| 12 | AP-304, AP-404, AP-504, AP-601, AP-702, AP-703, AP-802, AP-903 |  |
| 13 | AP-405, AP-505, AP-706, AP-805, AP-901 | Gullåret kan ikke bygges før hele kjeden fra lønnskjøring til a-melding finnes. |
| 14 | AP-406, AP-804, AP-902, AP-904 | Test i Skatteetatens og NAVs testmiljø til slutt, før første kunde. |
| 15 | AP-803 |  |
