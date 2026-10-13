# Kravspesifikasjon

Sjekklisten samler kravene fra seksjonene over, gruppert etter område. Hvert punkt kan krysses av når det er dekket i løsningen.

**Grunndata og parametre**

- [ ] Alle satser, grenser, tabeller og G-verdier versjonert per år og gyldighetsdato; G byttes 1. mai
- [ ] Ansatt- og arbeidsforholdsregister med alle a-meldingsfelter (type, ID, start/slutt, sluttårsak, stillingsprosent med endringsdato, timer for full stilling, arbeidstidsordning, ansettelsesform, 7-sifret yrkeskode)
- [ ] Permisjon og permittering med egen ID, prosent og historikk
- [ ] Virksomhet og underenheter fra Enhetsregisteret, med AGA-sone per kommune
- [ ] Lønnsarter mappet til a-meldingens kodeliste: fordel, beskrivelse, trekkpliktig, AGA-pliktig, feriepengegrunnlag, pensjonsgivende
- [ ] Arbeidsavtaledata etter aml. § 14-6 med endringslogg
- [ ] Kobling til allmenngjort tariff og validering mot minstesatser

**Beregning**

- [ ] Skattekort hentet via API før året og før hver lønnskjøring; 50 % uten kort, 30 % for pensjon
- [ ] Tabelltrekk (alle periodetabeller) og prosenttrekk etter regelmotor per lønnsart
- [ ] Trekkfri juni, halv skatt i november eller desember, tak på gjennomsnittsfortjeneste
- [ ] Frikort med akkumulator mot 100 000 kr og automatisk 50 % trekk
- [ ] Kildeskatt (PAYE) med fast sats, 12 måneder, tak 725 050 kr
- [ ] Svalbard-trekk (8/22 %) og Jan Mayen
- [ ] Naturalytelser: bil, elektronisk kommunikasjon, rentefordel, kost og losji, forsikring, aksjer og opsjoner
- [ ] Akkumulatorer for gaver, personalrabatt og sjablonger
- [ ] Reiseregning: deling i trekkfri og trekkpliktig del, måltidstrekk, dokumentasjonskontroll
- [ ] Feriepenger: opptjening per år, satser per avtale, 60+-tillegg med 6G-tak, utbetaling i juni og ved fratreden, avsetning månedlig
- [ ] Overtid med minst 40 % tillegg og kontroll av arbeidstidsgrenser
- [ ] Sykefravær: arbeidsgiverperiode, egenmelding, grunnlag etter § 8-28, refusjon med 6G-tak, § 8-20-vedtak
- [ ] Omsorgsdager med teller og refusjon fra dag 11; foreldrepenger med refusjon
- [ ] Permittering med 15 dagers lønnsplikt og 26-ukersgrense
- [ ] Pensjon: OTP fra første krone til 12G, eget innskudd, AFP-kontroll, SPK/KLP-trekk
- [ ] Trekk i lønn kun med hjemmel i aml. § 14-15, med lagret avtale og livsoppholdssperre
- [ ] Utleggstrekk: samordnet og gammelt regelverk side om side, import av trekkpålegg, prioritet etter dekningsloven § 2-8
- [ ] AGA per underenhet og sone, fribeløp i sone Ia, sektorunntak, A1-unntak, NAV-refusjon som negativt grunnlag
- [ ] Finansskatt for virksomheter i finansnæringen

**Rapportering og betaling**

- [ ] A-melding v2.3 via API, med erstatnings- og tilleggsmelding
- [ ] Validering før sending: F527 og sum trekk per utbetalingsdato som aldri er negativ
- [ ] Lese og vise tilbakemelding (A03); ikke sende ny melding før den er mottatt
- [ ] Fristkalender med varsling, flytting ved helg og helligdag
- [ ] Betalingsoppdrag med KID for trekk første virkedag etter utbetaling, og for AGA per termin
- [ ] Inntektsmelding for sykepenger via NAVs API; underlag for manuell inntektsmelding for andre ytelser
- [ ] Avstemming mot avstemmingsrapporten og NAVs oppgjørsrapport
- [ ] Sammenstillingsoppgave til alle mottakere innen 1. februar
- [ ] XML-eksport av a-melding som reserve

**Dokumentasjon og regnskap**

- [ ] Lønnsslipp ved hver utbetaling med beregning, feriepengegrunnlag og trekk
- [ ] Lønnsdokumentasjon med alle felter i bokføringsforskriften § 5-6, utstedt senest ved utbetaling
- [ ] Systembeskrivelse, beskrivelse av lukkefunksjon og kontrollspor
- [ ] Konterings- og eksportfunksjon mot regnskap (NS 4102/SAF-T), spesifikasjon per konto og per AGA-sone
- [ ] Full reversering ved retting etter frist, lukkede perioder og revisjonslogg
- [ ] Oppbevaring i 5 år (timelister 3,5 år) i Norge, EØS, Storbritannia eller Sveits; testet sikkerhetskopi
- [ ] Rapporter for lønnskartlegging etter kjønn og stillingsgruppe, og sykefraværsstatistikk per kvartal

**Personvern og sikkerhet**

- [ ] Rollebasert tilgang, tofaktor, tilgangslogg, kryptering ved lagring og overføring
- [ ] Strengere tilgang til fagforenings- og helseopplysninger; ingen diagnoser
- [ ] Maskert fødselsnummer, aldri i URL-er eller logger
- [ ] Sletteregler per datakategori, med bokføringsplikt foran slettekrav
- [ ] Innsyn og eksport for den ansatte
- [ ] Sikker lønnsslipp via portal eller digital postkasse
- [ ] Maskinporten-klient, systembruker og tilgangspakker; testoppsett i Tenor
