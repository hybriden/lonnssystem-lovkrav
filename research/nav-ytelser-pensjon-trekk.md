# Norske lovkrav for et lønnssystem: sykepenger, familieytelser, permittering, pensjon, yrkesskade og trekk (2026)

Merking: **[V]** = sjekket på kildesiden i denne økten. **[U]** = usikkert eller ikke sjekket, må kontrolleres før implementering.

## 0. Grunnbeløp (G) 2026
Kilde: `mcp__brreg__grunnbelop`, som henter fra NAV (g.nav.no). [V]

| | Beløp |
|---|---|
| G fra 1.5.2026 | **136 549** |
| G før 1.5.2026 (2025-G) | 130 160 [U, fra minnet] |
| Gjennomsnittlig G 2026 | **134 419** |
| 0,5 G (minsteinntekt for sykepenger, svangerskapspenger og foreldrepenger) | 68 275 |
| 2 G (sykepenger for 67–70 år) | 273 098 |
| 6 G (tak for sykepenger, foreldrepenger, pleiepenger og omsorgspenger, og for feriepengegrunnlaget i ferieloven) | 819 294 |
| 7,1 G | 969 498 |
| 7,1 G med gjennomsnittlig G (AFP-premiegrunnlag) | ca. 954 375 (utregnet) |
| 12 G (OTP-tak) | 1 638 588 |

**Krav til lønnssystemet:** G må lagres som en datert tabell med verdi per 1. mai og gjennomsnittlig G per år. Ulike regler bruker ulik G:
- dagens G ved refusjon,
- G per 31.12 for feriepengetaket ved 60 år og over,
- gjennomsnittlig G for AFP.

---

## 1. Sykepenger (folketrygdloven kap. 8)

### Regler
- **Opptjening, § 8-2 og § 8-18 [V].**
  - Den ansatte må ha vært i arbeid minst 4 uker rett før arbeidsuførheten.
  - Arbeidsgiverplikten (§ 8-18) gjelder først etter minst 4 ukers ansettelse, og bare for dager det skulle vært utbetalt lønn.
  - Ifølge NAV teller lovlig fravær med hvis den ansatte har arbeidet minst 1 dag.
  - 100 % permisjon eller permittering i mer enn 14 dager starter opptjeningen på nytt.
  - Tilkallingsvikarer har egne regler (28 dager).
- **Minsteinntekt, § 8-3 [V].** Kravet er 0,5 G, men det gjelder ikke i arbeidsgiverperioden. Det gis ikke sykepenger fra fylte 70 år. For 67–70 år kreves inntekt over 2 G, og retten er 60 dager (§ 8-12).
- **Arbeidsgiverperioden, § 8-19 [V].**
  - Inntil 16 kalenderdager, regnet fra første hele fraværsdag. En dag med delvis fravær teller ikke som første dag (NAV).
  - Fraværsdager på fridager teller med i de 16 dagene, men det betales bare for planlagte arbeidsdager.
  - Nytt fravær innen 16 dager etter at den ansatte er tilbake, regnes inn i samme arbeidsgiverperiode.
  - Etter en fullført arbeidsgiverperiode starter en ny periode først når den ansatte har vært i arbeid igjen og det har gått minst 16 dager.
  - Det er ikke noe tak på antall arbeidsgiverperioder per år.
- **Grunnlag i arbeidsgiverperioden, § 8-28 [V].** Gjennomsnittet av inntekt rapportert til a-ordningen de 3 siste kalendermånedene før arbeidsuførheten, omregnet til månedsinntekt. Kortere ansettelse bruker perioden som finnes. Timelønnede og skiftarbeidere får dagsats ut fra faktiske arbeidsdager.
- **Skjønn, § 8-30 [V].** Avviker omregnet årsinntekt mer enn 25 % fra rapportert inntekt siste 12 måneder, fastsettes grunnlaget ved skjønn.
- **6G-tak, § 8-10 [V].** Gjelder sykepengegrunnlaget når trygden betaler. Dagsats er 1/260 av årlig grunnlag. At taket ikke gjelder i arbeidsgiverperioden (arbeidsgiver betaler 100 % av grunnlaget), er etablert praksis, men ikke sjekket ordrett i denne økten. [U]
- **Varighet, § 8-12 [V].** 248 dager (52 uker) innen 3 år. Ny rett etter 26 uker som helt arbeidsfør.
- **Gradering, § 8-13 [V].** Minst 20 % nedsatt arbeidsevne.
- **Ferie, § 8-17 [V].** Trygden betaler ikke sykepenger under lovbestemt ferie eller permisjon. Refusjonen stopper da i ferien.
- **Trygdens ansvar, § 8-22 [V].** Betaler ikke arbeidsgiver i arbeidsgiverperioden, utbetaler NAV og krever beløpet tilbake fra arbeidsgiver, med renter.
- **Forsikring, § 8-21 [V].** Arbeidsgivere med samlet lønn siste år på inntil 40 G kan forsikre seg mot arbeidsgiverperioden. Forsikringen må omfatte alle ansatte.

### Egenmelding, §§ 8-23 til 8-27 [V]
- Krever minst 2 måneders ansettelse.
  - Ved avbrudd over 2 uker starter de 2 månedene på nytt.
  - Etter permittering, lovbestemt permisjon eller militærtjeneste er kravet bare 4 uker.
- Inntil 3 kalenderdager hver gang.
  - Arbeidsgiver kan utvide utover 3 dager innenfor arbeidsgiverperioden, etter drøfting med tillitsvalgte.
  - Fravær fra en arbeidsøkt som går over midnatt er én egenmeldingsdag.
  - Varer fraværet lenger, kan arbeidsgiver kreve legeerklæring. Uten den faller retten bort for egenmeldingsperioden.
- § 8-25: Arbeidsgiver kan nekte egenmelding etter skriftlig melding, når turnus eller reiserute gjør det umulig å møte rett etter fraværet.
- § 8-26: Arbeidsgiver kan kreve skriftlig bekreftelse av muntlig egenmelding.
- § 8-27: Arbeidsgiver kan frata retten etter minst 4 fravær uten legeerklæring på 12 måneder, eller ved rimelig mistanke. Den ansatte skal få uttale seg, og vedtaket vurderes på nytt etter 6 måneder.
- Jeg fant ikke noe generelt lovfestet tak på 4 ganger per år i § 8-24. Tallet 4 står bare i § 8-27. IA-utvidelser (24/8 dager) er avtalebaserte. [U]

### Refusjon når arbeidsgiver forskutterer lønn etter dag 16 [V]
- NAV dekker opptil 6 G (819 294). Ved flere arbeidsforhold fordeles refusjonen forholdsmessig.
- Refusjonen kan gå inntil 3 måneder før kalendermåneden kravet sendes. Den ansatte har også 3 måneders søknadsfrist.
- Saksbehandlingstid for refusjon er ca. 15 uker. Ca. 70 % behandles automatisk når inntektsmeldingen er mottatt.
- Statsbudsjettet 2027 har mål om ned til 11 uker (regjeringen.no, 7.10.2026).
- Arbeidsgiver registrerer kontonummer for refusjon selv hos NAV.
- **Oppgjørsrapporten** (tidligere K27) viser refusjoner for alle ytelser.
  - Altinn 2 ble avviklet 15.6.2026, og rapporten sendes nå bare i Altinn 3.
  - Leverandører av lønns- og personalsystem måtte ta i bruk nytt API før 15.6.2026 (GitHub: navikt/sokos-oppgjorsrapporter).
- **Feriepenger av refusjon, § 8-33 [V].** NAV betaler feriepenger av sykepenger for de første 48 sykepengedagene i opptjeningsåret. Satsen er 10,2 %, eller 12,5 % for dem som fyller 59 år i opptjeningsåret. Det samme gjelder refusjon etter § 8-20.

### Kronisk syk eller gravid, § 8-20 [V]
- Arbeidstaker eller arbeidsgiver kan søke om at NAV dekker arbeidsgiverperioden.
  - Kronisk eller langvarig sykdom med risiko for særlig stort fravær. NAV bruker som veiledende grense ca. 35 fraværsdager per år.
  - Svangerskapsrelatert sykdom der tilrettelegging eller omplassering ikke er mulig.
- Vedtaket virker fra den dagen NAV mottok søknaden, og følger den ansatte, ikke arbeidsforholdet.
- Arbeidsgiver betaler lønn i arbeidsgiverperioden som vanlig og krever refusjon per fraværsperiode innen 3 måneder.

### Inntektsmelding i 2026 [V]
- **Når:** Etter at arbeidsgiverperioden er over og den ansatte har søkt. Ny melding kreves ved hvert nytt fravær med opphold på minst 1 kalenderdag.
- **Innhold:**
  - Inntektsmeldingen er samtidig refusjonskravet.
  - Begrunnelse må oppgis hvis arbeidsgiver ikke betaler full lønn i arbeidsgiverperioden. Kodelisten er ikke sjekket. [U]
  - Ferie skal ikke oppgis.
- **Kanaler:**
  1. NAVs skjema på Min side – arbeidsgiver, ut fra en forespørsel eller som manuell melding.
  2. **Lønns- og personalsystem via API, bare for sykepenger.**
     - API: «Sykepenger IM LPS API» (github.com/navikt/sykepenger-im-lps-api).
     - REST/JSON, Maskinporten med scope `nav:helseytelser/sykepenger`, og systembruker/Altinn 3.
     - `GET /v1/forespoersler` henter NAVs forespørsler.
     - NAV sender også varsel om behov for inntektsmelding via Dialogporten/Altinn-innboks (fra 16.6.2026).
     - Swagger i dev: sykepenger-api.ekstern.dev.nav.no/swagger.
     - Produksjons-URL og full liste over endepunkter er ikke sjekket. [U]
  3. **Altinn 2 kan ikke lenger brukes.** Fra 21.5.2026 kan inntektsmeldinger ikke sendes via Altinn.
- **Andre ytelser:** Foreldrepenger, svangerskapspenger, pleiepenger, opplæringspenger og omsorgspenger kan per kildene bare sendes manuelt på Min side – arbeidsgiver. NAV arbeider med API for disse, men jeg fant ingen bekreftelse på at det er lansert per oktober 2026. [U]
- **Flere arbeidsforhold:** Via eget system kunne man sende én melding per arbeidsforhold (med arbeidsforholdsID) til og med 15.6.2026.
- **Tilgang:** Altinn-tilgangspakken «Lønn med personopplysninger av særlig kategori».

### A-meldingen [V]
- Forskuttert lønn under sykdom rapporteres som vanlig lønn.
- Fritak for arbeidsgiveravgift ved refusjon (ftrl § 23-2 femte ledd):
  - Rapporter refusjonsbeløpet negativt under «Grunnlag refusjon fra NAV», med samme beregningskode, sone og sats.
  - Det kan gjøres i forskutteringsmåneden (krever dokumentert estimat) eller i måneden refusjonen mottas.
  - Grunnlaget kan bare reduseres med beløp som faktisk refunderes. Ble reduksjonen for høy, rettes forskutteringsmåneden.
  - Ordningen med ekstra arbeidsgiveravgift er avviklet fra 2025.
- Sykefravær under 12 måneder rapporteres ikke som permisjon. Sammenhengende sykefravær over 12 måneder med arbeidsforholdet i behold rapporteres som permisjon. Dager med syke barn er ikke permisjon.
- Feriepenger av sykepenger fra trygden rapporteres bare av NAV.

### Sykefraværsstatistikk [V]
- Arbeidsgiver skal føre statistikk over sykefravær og barns sykdom. Den sendes ikke til NAV, men kan kreves fremlagt for Arbeidstilsynet.
- Krav:
  - kvartalsvis,
  - avtalte dagsverk = ansatte × driftsdager × stillingsandel,
  - skille mellom egenmeldt og legemeldt,
  - inndeling 1–3 dager, 4–16 dager, over 16 dager og over 8 uker,
  - gradert sykmelding telles med graderingen.
- Virksomheter under 20 ansatte velger detaljnivå selv, men må minst telle avtalte dagsverk og sykefravær.
- NAV oppgir ftrl. kap. 25 som hjemmel. Eksakt forskriftshjemmel er ikke sjekket. [U]
- Den nasjonale statistikken bruker a-ordningen (avtalte dagsverk) og sykmeldingsregisteret.

### Endringer 2026/2027
- **Utvalgsforslag (områdegjennomgang av helserelaterte ytelser, Oslo Economics m.fl., oktober 2025):**
  - arbeidsgiverperioden kortes fra 16 til 12 dager,
  - arbeidsgiver finansierer 10 % etter arbeidsgiverperioden,
  - sykelønnen settes ned til 95 % etter 12 dager og 90 % etter 6 måneder.
- **Ikke vedtatt.** Regjeringens pressemeldinger om statsbudsjett 2027 (7.10.2026) nevner ingen regelendring i sykelønnen, bare penger til kortere saksbehandlingstid. Prop. 1 S (2026–2027) er ikke gjennomgått i detalj. [U]

### Krav til lønnssystemet: sykepenger
- Fraværsregister per dag (egenmelding, sykmelding, grad, delvis dag) med automatisk beregning av arbeidsgiverperioden:
  - 16 kalenderdager fra første hele dag,
  - sammenslåing av fravær med under 16 dagers mellomrom,
  - ny periode etter 16 dager i arbeid,
  - kontroll av opptjening på 4 uker og egenmeldingsrett etter 2 måneder.
- Egenmeldingsregler: 3 dager, eventuell utvidelse fra arbeidsgiver, og sperre etter § 8-27.
- Beregning av lønn i arbeidsgiverperioden etter § 8-28: snitt av 3 måneder fra egne a-meldingsdata, og dagsats for timelønnede.
- Refusjonsberegning: årlig grunnlag begrenset til 6 G, dagsats = /260, gradering, stopp i ferie, maksdato/248 dager og regler for 67–70 år.
- Inntektsmelding via NAVs API for sykepenger:
  - Maskinporten og systembruker,
  - henting av forespørsler,
  - innsending,
  - endring som ny komplett melding.
  - For andre ytelser må brukeren henvises til Min side – arbeidsgiver.
- Avstemming mot oppgjørsrapporten fra NAV-API (Altinn 3): forventet mot mottatt refusjon.
- A-meldingen: grunnlag for refusjon fra NAV (negativt) i riktig måned, og retting ved avvik.
- Støtte for vedtak etter § 8-20 per ansatt: refusjon også for arbeidsgiverperioden.
- Feriepengeopptjening: feriepenger av lønn i arbeidsgiverperioden og forskuttert lønn, og feriepenger fra NAV på refundert beløp for de første 48 dagene.
- Rapport over sykefraværsstatistikk per kvartal.

---

## 2. Foreldrepenger, svangerskapspenger, pleiepenger, omsorgspenger og opplæringspenger

### Regler [V]
- **Foreldrepenger (ftrl. kap. 14):**
  - Opptjening: inntekt 6 av de siste 10 månedene og minst 0,5 G.
  - Tak 6 G. 49 uker med 100 % eller 61 uker og 1 dag med 80 %.
  - Arbeidsgiver som betaler lønn får refusjon opptil 6 G, eller 80 % av 6 G ved 80 % dekning.
  - Inntektsmelding sendes tidligst 4 uker før fraværet og er samtidig refusjonskravet. Den foreslåtte månedslønnen må kontrolleres.
- **Svangerskapspenger:**
  - Krav: risiko for fosteret, 0,5 G og 4 ukers arbeid. Tilrettelegging må først vurderes (Arbeidstilsynets skjema).
  - Opptil 6 G, og fram til 3 uker før termin. Refusjon ved lønn.
- **Pleiepenger:**
  - 100 % av grunnlaget, tak 6 G, dagsats /260.
  - Ingen arbeidsgiverperiode og ingen lønnsplikt.
  - Inntektsmelding tidligst 4 uker før, og ved nytt opphold over 4 uker eller varig inntektsendring.
  - Refusjon inntil 3 måneder før innsendingsmåneden.
  - Over 14 dager rapporteres som lovfestet permisjon i a-meldingen.
- **Opplæringspenger:** Som pleiepenger. Manuell inntektsmelding.
- **Omsorgspenger (ftrl. kap. 9):**
  - 10 dager per kalenderår for 1–2 barn, 15 dager for 3 eller flere. Dobbelt ved alenesomsorg. +10 dager per kronisk sykt barn (+20 alene). Normalt til barnet fyller 12 år, eller til året det fyller 18 med ekstra dager.
  - Arbeidsgiver betaler de første 10 dagene, eller flere hvis den ansatte har rett til flere dager. NAV refunderer fra dag 11. Tak 6 G.
  - Krav: 4 ukers arbeid.
  - Egenmelding de første 3 dagene. Legeerklæring kan kreves fra dag 4.
  - Refusjonskravet sendes etterskuddsvis via Min side – arbeidsgiver, med frist 3 måneder. Ett krav per kalenderår.
  - Inntektsmelding sendes bare når den ansatte søker direkte og arbeidsgiver ikke har betalt lønn.
- **Ingen inntektsmelding fra 21.5.2026** ved lønnet arbeid i egen bolig eller fritidsbolig, for foreldrepenger, pleiepenger, opplæringspenger og omsorgspenger.

### Feriepenger, ferieloven § 10 nr. 4 [V]
- Arbeidsgiver betaler feriepenger av sykepenger i arbeidsgiverperioden og av inntil 10 omsorgspengedager.
- Trygden betaler feriepenger av:
  - sykepenger i 48 dager,
  - pleiepenger og opplæringspenger i inntil 12 uker (NAV: per barn per kalenderår),
  - svangerskapspenger i 64 dager,
  - foreldrepenger i 12 uker med 100 % eller 15 uker med 80 % (samlet for begge foreldre).
- Betaler arbeidsgiver lønn under foreldrepermisjon, utbetaler NAV feriepengene til arbeidsgiveren, og arbeidsgiveren betaler den ansatte feriepenger som normalt.
- Sats 10,2 %, +2,3 prosentpoeng for ansatte over 60 år. Ingen feriepenger av grunnlag over 6 G (G per 31.12).
- Hvem som betaler feriepenger av omsorgspenger etter dag 10 er ikke avklart. [U]

### A-meldingen [V]
- Permisjon over 14 dager rapporteres med permisjonId, start, slutt og prosent av avtalt stilling.
- Kategorier: foreldrepermisjon, militærtjeneste, utdanning (lovfestet/ikke lovfestet), annen lovfestet (f.eks. pleiepenger), annen ikke lovfestet.
- Kortere permisjoner som til sammen blir over 14 dager på 12 måneder, skal også rapporteres.
- Svangerskapspenger rapporteres ikke som permisjon.
- Det kreves en ny ID per nytt tilfelle, og åpen permisjon må gjentas hver måned (ellers feil 231).
- Fritak for arbeidsgiveravgift ved refusjon gjelder også for foreldrepenger og «andre trygdeytelser» (ftrl § 22-3). Pleiepenger og omsorgspenger er ikke nevnt eksplisitt. [U]

### Krav til lønnssystemet: familieytelser
- Fraværs- og permisjonstyper med grad og ID per tilfelle, og automatisk generering av permisjon i a-meldingen (over 14 dager eller summert på 12 måneder).
- Valg per tilfelle: arbeidsgiver betaler lønn med refusjon, eller NAV betaler direkte. Refusjon beregnes med 6 G-tak og 80 %-dekning.
- Teller for omsorgsdager per ansatt per kalenderår (10/15/20/30), med varsel ved dag 10 og grunnlag for refusjonskrav etter dag 10.
- Feriepengelogikk per ytelse: hvem betaler, uketaket på 12/15/48 dager/64 dager, og avregning mot NAV-utbetalte feriepenger i mai.
- Rapport eller eksport for manuell inntektsmelding (månedslønn, refusjon, naturalytelser) til Min side inntil NAV har API for disse ytelsene.

---

## 3. Permittering (permitteringslønnsloven, LOV-1988-05-06-22)

### Regler [V]
- **Lønnsplikt, § 3:** Arbeidsgiverperiode I er **15 dager**, i kraft fra 1.3.2022 (LOV-2021-12-17-147). NAV formulerer det som 15 arbeidsdager.
  - Perioden regnes fra første arbeidsdag permitteringen omfatter, og pauser på dager den ansatte uansett ville vært fri eller borte.
  - Unntak: ingen lønnsplikt ved brann, ulykker eller naturhendelser, og ingen ved arbeidskamp.
- **Fritaksperiode:** 26 uker innenfor 18 måneder. Arbeid inntil 6 uker avbryter ikke permitteringen.
- **Arbeidsgiverperiode II (5 dager)** finnes bare som forskriftshjemmel ved forlenget fritaksperiode. Jeg fant ingen 2026-forskrift som bruker den. [U]
- **Varsel:** 14 dager, eller 2 dager ved uforutsette hendelser. Lønnsplikt gjelder i varselperioden. Meldeplikt til NAV (§ 3a / arbeidsmarkedsloven § 8).
- **Arbeidsgiverperioden ved opptjening av sykepenger:** 100 % permittering over 14 dager starter opptjeningen på nytt. Egenmeldingsrett gjeninntrer etter 4 uker.

### A-meldingen [V]
- Rapporteres uansett lengde, også innenfor arbeidsgiverperioden.
- Felter: beskrivelse «permittering», unik permitterings-ID, startdato (første lønnspliktdag), sluttdato og prosent (over 0, maks 100).
- Startdatoen gjentas hver måned. Arbeidsforholdet skal ikke ha sluttdato.
- **Endring av prosent:** avslutt gammel ID dagen før endringen og opprett ny ID fra endringsdatoen.
- Arbeid over 6 uker avslutter permitteringen, og en senere permittering får ny ID. I fiskeindustrien er grensen 26 uker.
- Permitteringslønn rapporteres som vanlig lønn.
- Retting: send samme ID med samme start- og sluttdato og 0 %.

### Krav til lønnssystemet: permittering
- Permitteringsregister med ID, grad, start og slutt, og historikk per ID.
- Automatisk beregning av lønnsplikt for arbeidsgiverperiode I (15 arbeidsdager, pauser) og varsel ved 26 uker innen 18 måneder.
- Regler for samspill med ferie, sykdom og permisjon: permitteringen gjelder bare stillingsandelen den ansatte ellers ville arbeidet.
- Varselmal og dato for melding til NAV (dokumentasjon).

---

## 4. Pensjon

### OTP-loven (LOV-2005-12-21-124) [V]
- **§ 1 (hvem må ha ordning):** Foretak med minst ett av disse:
  - 2 personer i minst 75 % stilling,
  - 1 arbeidstaker uten eierinteresse i minst 75 %,
  - flere i minst 20 % som til sammen utgjør minst 2 årsverk.
  - Gjelder ikke foretak med offentlig ordning etter lov eller tariff.
- **§ 2:** Ordningen skal være etter foretakspensjonsloven, innskuddspensjonsloven eller tjenestepensjonsloven, og opprettet innen 6 måneder.
- **§ 4:** Minst **2 % av lønn opp til 12 G**, og fra første krone fra 1.1.2022 (frist for å tilpasse ordningen 30.6.2022).
  - Innskuddsfritak ved uføregrad på minst 20 %.
  - Foretaket dekker administrasjonskostnadene.
- **§ 5:** Minstekrav for ytelsesordninger.
- **§ 7:** Pensjonsinnretningen skal oppgis i a-meldingen.
- **§ 8 a:** Straff (fra 2022). Siste endring: LOV-2021-12-22-164.
- **Tilsyn:** Skatteetaten. Tvangsmulkt 250 kr per ansatt per dag. Bot eller fengsel inntil 2 år.

### Innskuddspensjonsloven (LOV-2000-11-24-81) [V]
- **§ 4-2 (medlemskap):**
  - Alle arbeidstakere fra fylte 13 år. Ordningen kan unnta ansatte over 75 år.
  - Opptak når samlet lønn har nådd rapporteringspliktig beløp i a-meldingen, eller fra første arbeidsdag hvis ordningen ikke har minstekrav.
  - Ingen grense for stillingsprosent. Unntaket for ansatte under 20 % falt bort i 2022.
- **Rapporteringsgrensen i a-meldingen** er 2 000 kr per år fra 2025, og 10 000 kr for skattefrie organisasjoner (Skatteetaten). [V]
- **§ 4-3:** Ansatte i permisjon er som hovedregel medlemmer. Permitterte kan omfattes etter regelverket.
- **§ 5-2:** Prosentsats av lønn opp til 12 G, og eventuelt tilleggsinnskudd for lønn mellom 7,1 og 12 G. § 5-5: lønn over 12 G tas ikke med.
- **§ 5-6:** Ansattes eget innskudd er maks 4 %.
- **Lønnsbegrepet, § 1-2 j:** Skattepliktig lønnsinntekt, med mer.
- **Maksimalt innskudd** (7 % opp til 12 G + 18,1 % mellom 7,1 og 12 G, skatteloven § 6-47 / forskrift) er ikke sjekket i denne økten. [U]
- **Egen pensjonskonto:** §§ 3-3, 3-6 og 3-7. Foretaket dekker kostnader for opptjening hos seg.

### A-meldingen [V]
- **Pensjonsinnretning:** Organisasjonsnummer oppgis (TIN for utenlandske innretninger), ikke polisenummer. Rapporteres på opplysningspliktig-nivå hver måned fra avtalen starter til den slutter. Ved bytte rapporteres begge innretningene i overgangsmåneden.
  - Feil F507 kommer hvis innretning mangler.
  - Offentlige ordninger etter lov eller tariff oppgir ikke innretning.
- **Arbeidsgivers tilskudd og premie** skal inngå i grunnlaget for arbeidsgiveravgift.
- **Ansattes eget innskudd** trukket i lønn (f.eks. SPK 2 %) rapporteres som fradrag «premie til pensjonsordning», med negativt bruttobeløp.
  - Trekket reduserer grunnlaget for skattetrekk, men ikke grunnlaget for arbeidsgiveravgift.
- Jeg fant ingen innrapportering av pensjonsgrunnlag per ansatt i a-meldingen. Pensjonsinnretningene henter lønnsdata fra a-ordningen. [U]

### AFP i privat sektor (Fellesordningen) [V]
- **Premie 2026: 2,7 %**, uendret fra 2025. **2027: 2,7 %** (publisert 27.8.2026).
- Grunnlaget er lønn per ansatt mellom 1 G og 7,1 G.
  - Azets oppgir at gjennomsnittlig G brukes, som ville gitt 134 419 og ca. 954 375 for 2026. Det er ikke bekreftet på afp.no. [U]
  - Lønnselementer som inngår står i vedlegg 7 til vedtektene.
- Premieplikt fra kalenderåret den ansatte fyller 13 år til og med året den ansatte fyller 61 år. Ingen premie hvis årslønnen er under 1 G.
- Fellesordningen beregner og fakturerer selv ut fra a-meldingen og Aa-registeret, etterskuddsvis per kvartal. Forfall er 31.5, 31.8, 30.11 og 28.2.
- OU-samordning: 46 kr per måned for fulltidsansatte.
- Sliterordningen: premieplikten opphørte 31.12.2023.

### Offentlig tjenestepensjon (kort) [V]
- SPK: medlemskap fra 13 år til 75 år, og ingen minstegrense for stilling fra 1.1.2025.
- Ansatte betaler 2 % medlemsinnskudd, trukket i lønn. Arbeidsgiver betaler resten, ca. 13–15 % totalt.
- Lønns- og stillingsdata rapporteres direkte til SPK/KLP, ikke via a-meldingen. Kanal og format er ikke sjekket. [U]
- Spørsmål om hvilke tillegg som er pensjonsgivende har gitt rettssaker (sak om Forsvaret-tillegg ble anket av staten i 2024).

### Krav til lønnssystemet: pensjon
- Lønnsarter merket som pensjonsgivende eller ikke pensjonsgivende, per ordning: OTP (§ 1-2 j), AFP (vedlegg 7) og SPK/KLP.
- Beregning av innskudd: 2 % (eller avtalt sats) fra første krone til 12 G, eventuelt tillegg 7,1–12 G, og eget innskudd (maks 4 %).
- Kontroll av alder 13 år og eventuelt 75 år, og av rapporteringsgrensen på 2 000 kr for opptak.
- Organisasjonsnummer for pensjonsinnretning per opplysningspliktig og måned i a-meldingen. Arbeidsgivers tilskudd skal inngå i grunnlaget for arbeidsgiveravgift.
- Fradrag «premie til pensjonsordning» i a-meldingen, som reduserer grunnlaget for skattetrekk.
- AFP: avsetning eller kontroll av premie (2,7 % × lønn mellom 1 G og 7,1 G, alder 13–61) for regnskap og fakturakontroll.
- SPK/KLP: trekk på 2 % og eksport av pensjonsgrunnlag og stillingsprosent til pensjonskassen.

---

## 5. Yrkesskadeforsikring og gruppeliv

### Regler [V]
- Yrkesskadeforsikringsloven (LOV-1989-06-16-65):
  - § 3: alle arbeidsgivere må forsikre alle arbeidstakere (§ 2: alle «i arbeidsgivers tjeneste»). Staten er unntatt.
  - § 4: forsikringsgiveren må være godkjent og medlem av Yrkesskadeforsikringsforeningen.
  - § 6: dekningen løper inntil 4 måneder etter opphør av forsikringen.
  - § 7: solidaransvar mellom forsikringsgivere ved manglende forsikring.
  - § 8: regress mot arbeidsgiver som ikke har forsikring, uavhengig av skyld.
  - Siste endring: LOV-2022-12-20-115.
- Ingen beregning eller rapportering i a-meldingen.
- Arbeidsgivers plikt til å melde yrkesskade til NAV (ftrl § 13-14) er ikke sjekket i denne økten. [U]

### Gruppelivsforsikring [U, ikke sjekket i denne økten]
- Ikke lovpålagt i privat sektor. Den følger ofte av tariffavtale, f.eks. statens og kommunenes hovedtariffavtaler.
- Den skattemessige behandlingen av kollektiv livsforsikring for den ansatte må sjekkes.

### Krav til lønnssystemet: forsikring
- Registrere forsikringsavtaler (selskap, polise, periode).
- Grunnlag for premie: antall ansatte, årsverk eller lønnssum.
- Kostnadsføring og fordeling per avdeling eller prosjekt.
- Eventuell fordelsbeskatning av forsikringer som ikke er skattefrie. [U]

---

## 6. Trekk til tredjepart

### Stor endring fra 1.1.2026: innkrevingsloven og samordnet utleggstrekk [V]
- Innkrevingsloven (LOV-2025-04-25-12) trådte i kraft 1.1.2026, men utleggsreglene innføres gradvis. Motregning (§ 21) gjelder fra 2027.
- Én samlet innkrevingsmyndighet i Skatteetaten: SI, Innkrevingssentralen for bidrag (tidligere NAV Innkreving) og skatteinnkrevingen.
- Nye trekk samordnes til **ett utleggstrekk per ansatt**, som kan dekke krav fra flere kreditorer.
- Trekket har ikke lenger to års grense og løper til alle krav er dekket.
- **Overgangsperiode til ca. 2029.** Systemet må håndtere gamle trekk (som før) og samordnede trekk samtidig, og de skal ikke blandes.
- **Trekkpålegget** angir den ansatte, start, endring eller stopp, fast beløp eller prosent, konto og KID.
  - Pålegget har ingen sluttdato og ingen saldo. Arbeidsgiver trekker til det kommer endring eller stopp.
  - Pålegget kommer som brev i Altinn til hovedenheten, eller via **Skatteetatens Trekkpålegg-API**.
  - API-et er maskin-til-maskin og gir beløp eller prosent, gyldig fra, KID, konto, status og historikk.
  - Vilkår for API-tilgang: leverandøren har signert bruksvilkår, er integrert mot minst ett rapporterings-API (a-meldingen), og kunden har rapportert via systemet minst én gang.
  - Dokumentasjon: skatteetaten.github.io/api-dokumentasjon/api/trekkpaalegg. Detaljer om autentisering er ikke sjekket. [U]
- Arbeidsgiver gir ikke lenger den ansatte detaljer om kreditorene.

### Arbeidsgivers plikter, innkrevingsloven [V]
- § 30 første ledd: trekk etter beskjed fra innkrevingsmyndigheten.
- § 30 andre ledd: innbetaling **senest første virkedag etter utbetalingen**. Samordnet trekk går til én felles ny konto med unik KID per ansatt eller trekk.
- § 30 tredje ledd: månedlig rapportering i a-meldingen.
- § 30 fjerde ledd: melding når den ansatte ikke lenger har krav på lønn, med mindre det er rapportert i a-meldingen.
- § 31 (ansvar):
  - Arbeidsgiver er ansvarlig for beløpet hvis pålegget ikke følges eller trekket ikke betales.
  - Ved brudd på opplysningsplikten etter a-opplysningsloven kan ansvaret beregnes fra 14 dager etter ansettelsen med 20 % av trekkgrunnlaget.
  - Ansvaret faller bort hvis arbeidsgiver godtgjør at det ikke skyldes forsømmelse.
  - Ansvarskravet er tvangsgrunnlag for utlegg.
- § 34: gjennomført trekk virker frigjørende for skyldneren.
- § 39: straff.
- Tvangsfullbyrdelsesloven § 7-21 (endring av trekk) og § 7-22 (ny arbeidsgiver får trekkplikt).

### Grunnlag og prioritet [V]
- **Dekningsloven § 2-7:**
  - Trekk i lønn etter forskuddstrekk, utover det skyldneren og husstanden trenger til livsopphold.
  - Omfatter også feriepenger, pensjon fra arbeidsgiver og trygd.
  - For næringsdrivende inntil 20 % av brutto.
- **§ 2-8 (prioritet når trekket ikke dekker alt):**
  - a) forsørgelseskrav (bidrag),
  - b) erstatning eller oppreisning for straffbar handling,
  - c) bøter,
  - d) skatt, avgift og statens regresskrav,
  - e) andre krav.
  - Lik prioritet deles forholdsmessig. Forskuddstrekk går alltid først.
- **Skatteetatens retningslinje (2023, eldre regler):**
  - Trekkgrunnlaget er nettolønn etter forskuddstrekk, inkludert feriepenger, faste tillegg, provisjon, bonus og fast overtid. Skattefrie utgiftsgodtgjørelser holdes utenfor.
  - Samlet trekk sammen med forskuddstrekk bør ikke overstige 80 % av lønnen.
  - Gamle trekk har maks 2 år, men 5 år for skatt og bøter og ingen grense for bidrag.
- **Livsoppholdssatser fra 1.7.2026** (FOR-2014-06-13-724, KPI +3,1 %), per måned. Namsmyndigheten bruker dem ved fastsettelse av trekket. Arbeidsgiver trekker bare det pålagte beløpet eller den pålagte prosenten.

| Kategori | Sats |
|---|---|
| Enslig | 11 388 |
| Gift/samboende | 9 644 |
| Forsørger ektefelle/samboer | 19 288 |
| Barn 0–5 år | 3 645 |
| Barn 6–10 år | 4 835 |
| Barn 11–14 år | 6 102 |
| Barn 15 år og over | 7 020 |

  Samværstillegg i 4 klasser kommer i tillegg. Boutgifter vurderes særskilt. [U]

### Forskuddstrekk og skattetrekkskonto fra 2026 [V]
- **Skattetrekkskonto og bankgaranti er avviklet fra 1.1.2026.**
- Forskuddstrekk og utleggstrekk (både samordnet trekk og «utleggstrekk skatt») betales til Skatteetaten senest første virkedag etter lønnsutbetaling. Arbeidsgiveravgift følger fortsatt terminen.
- **A-meldingen fra periode 2026-01:**
  - «sum forskuddstrekk per lønnsutbetalingsdato» erstatter «sum forskuddstrekk å betale», med én linje per utbetalingsdato.
  - Nye koder `utleggstrekkSamordnet` (dato er påkrevd) og `utleggstrekkSkatt` (gammelt regelverk).
  - Begge rapporteres med lønnsutbetalingsdato.
- Trekk for NAV, Helfo og andre etter gammelt regelverk betales etter brevet, med full KID. Disse rapporteres ikke under skattekodene.

### Bidragstrekk [V/U]
- NAV fastsetter bidraget. Innkrevingen ligger nå i Skatteetaten (innkrevingsmyndigheten) og inngår i det samordnede trekket for nye saker.
- Gamle bidragstrekk etter bidragsinnkrevingsloven løper som før, med betaling etter påleggsbrevet.
- Konkrete overgangsrutiner er ikke funnet. [U]

### Fagforeningskontingent [V]
- Maks fradrag (skatteloven § 6-19) er **8 700 kr for 2026** (8 250 i 2025), uansett antall medlemskap. Forholdsmessig fradrag ved deler av året.
- Kontingent trukket i lønn rapporteres i a-meldingen som fradrag «fagforeningskontingent».
- Det brukes ved forskuddsutskrivingen og forhåndsutfylling av skattemeldingen. Uten rapportering videreføres fjorårets fradrag.
- Arbeidsgiver må kunne bekrefte trukket beløp.
- Trekket krever samtykke eller tariffhjemmel (arbeidsmiljøloven § 14-15). [U, ikke sjekket i denne økten]

### Krav til lønnssystemet: trekk
- Trekkregister per ansatt med type (samordnet, gammelt skattetrekk, gammelt namsmann/SI/bidrag/NAV), beløp eller prosent, startdato, KID, konto og status. Historikk og ingen sluttdato for samordnede trekk.
- Integrasjon mot Skatteetatens Trekkpålegg-API (Maskinporten/systembruker) og manuell registrering fra Altinn-brev.
- Beregningsrekkefølge: brutto → forskuddstrekk → trekkgrunnlag (netto, inkludert feriepenger, uten skattefrie godtgjørelser) → utleggstrekk etter prioritet (bidrag først) → fagforening og pensjonstrekk etter avtale.
  - Kontroll av taket på 80 % for eldre trekk. [U]
- Generering av betaling per lønnsutbetalingsdato: forskuddstrekk og trekk forfaller første virkedag etter. Separate konto/KID for samordnet trekk, skattetrekk og hver kreditor etter gammelt regelverk.
- A-meldingen:
  - `utleggstrekkSamordnet` og `utleggstrekkSkatt` med dato,
  - forskuddstrekk per utbetalingsdato,
  - fradrag for fagforeningskontingent og pensjonspremie.
- Varsel eller melding til innkrevingsmyndigheten når arbeidsforholdet opphører, hvis det ikke dekkes av a-meldingen.
- Revisjonsspor (logg) for trekk som ikke ble gjennomført, med begrunnelse. Arbeidsgiver har objektivt ansvar for gjennomførte trekk som ikke er betalt.

---

## Største usikkerheter
- Om NAVs API for inntektsmelding for familieytelser er lansert per oktober 2026. Fant ikke bekreftelse.
- Teknisk autentisering og endepunkter for Trekkpålegg-API og produksjonsmiljøet til NAVs API for sykepenger.
- Om 6G-taket ikke gjelder i arbeidsgiverperioden (praksis, ikke sjekket ordrett), og kodelisten for begrunnelse ved redusert utbetaling i inntektsmeldingen.
- Om AFP-grunnlaget bruker gjennomsnittlig G (bare oppgitt av Azets), og maksgrensene for innskudd i innskuddspensjon.
- Hvem som betaler feriepenger av omsorgspenger etter dag 10. Gruppeliv og meldeplikt for yrkesskade er ikke sjekket.
- Prop. 1 S (2026–2027) er ikke lest i detalj. Bare pressemeldinger, som ikke nevner endringer i sykelønnen.

## Kildesider åpnet i denne økten
- https://www.nav.no/arbeidsgiver/sykepenger
- https://www.nav.no/arbeidsgiver/sykepenger-i-arbeidsgiverperioden
- https://www.nav.no/arbeidsgiver/sykepenger-etter-arbeidsgiverperioden
- https://www.nav.no/arbeidsgiver/inntektsmelding
- https://www.nav.no/arbeidsgiver/sende-inntektsmelding
- https://www.nav.no/arbeidsgiver/nye-inntektsmeldinger
- https://www.nav.no/arbeidsgiver/oppgjorsrapport
- https://www.nav.no/arbeidsgiver/kroniker-gravid
- https://www.nav.no/arbeidsgiver/foreldrepenger-til-ansatt
- https://www.nav.no/arbeidsgiver/svangerskapspenger-til-ansatt
- https://www.nav.no/arbeidsgiver/omsorgspenger
- https://www.nav.no/arbeidsgiver/pleiepenger-barn
- https://www.nav.no/arbeidsgiver/permittere
- https://www.nav.no/arbeidsgiver/fore-sykefravar
- https://www.nav.no/foreldrepenger
- https://github.com/navikt/sykepenger-im-lps-api
- https://lovdata.no/lov/1997-02-28-19/§8-20, §8-23, §8-24, §8-10, §8-33 (ftrl. kap. 8)
- https://lovdata.no/lov/1988-04-29-21/§10 (ferieloven)
- https://lovdata.no/dokument/NL/lov/1988-05-06-22 (permitteringslønnsloven)
- https://lovdata.no/dokument/NL/lov/2005-12-21-124 (OTP-loven)
- https://lovdata.no/dokument/NL/lov/2000-11-24-81 og https://lovdata.no/lov/2000-11-24-81/§4-2 (innskuddspensjonsloven)
- https://lovdata.no/dokument/NL/lov/1989-06-16-65 (yrkesskadeforsikringsloven)
- https://lovdata.no/lov/1992-06-26-86/§7-22 og §7-17 (tvangsfullbyrdelsesloven)
- https://lovdata.no/lov/1984-06-08-59/§2-7 (dekningsloven)
- https://lovdata.no/dokument/NL/lov/2025-04-25-12 (innkrevingsloven)
- https://www.regjeringen.no/no/tema/forbruker/gjeldsordning/livsoppholdssatser/id691824/
- https://www.regjeringen.no/no/aktuelt/vil-ha-kortare-saksbehandlingstid-for-sjukepengar/id3175613/
- https://www.regjeringen.no/no/statsbudsjett/2027/statsbudsjettet-2027-statens-inntekter-og-utgifter/id3173250/
- https://www.altinget.no/arbeidsliv/artikkel/foreslaar-loesninger-paa-en-av-hans-stoerste-hodepiner-kan-skape-ny-og-noedvendig-debatt
- https://www.skatteetaten.no/om-skatteetaten/fremtidens-innkreving/systemleverandorer/lonns--og-personalsystem/
- https://www.skatteetaten.no/om-skatteetaten/fremtidens-innkreving/kommuner/arbeidsgiver/
- https://www.skatteetaten.no/samarbeidspartnere/sluttbrukersystemer/trekkpalegg-sbs/
- https://skatteetaten.github.io/api-dokumentasjon/api/trekkpaalegg (siden manglet tekniske detaljer)
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/siste-fra-a-ordningen/nye-frister-for-betaling-av-forskuddstrekk-og-utleggstrekk/
- https://www.skatteetaten.no/bedrift-og-organisasjon/betaling-og-innkreving/tema/trekk-i-lonn-hos-ansatte/betale/
- https://www.skatteetaten.no/en/rettskilder/type/retningslinjer/retningslinje-for-utleggstrekk/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/employment/information-on-employment/leave/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/employment/information-on-employment/layoffs/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/pension-scheme-arrangement-mandatory-occupational-pension-scheme/
- https://www.skatteetaten.no/en/business-and-organisation/employer/otp---mandatory-occupational-pension-scheme/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/deductions/premium-for-pension-schemes/
- https://www.skatteetaten.no/en/business-and-organisation/employer/employers-national-insurance-contributions/when-should-i-not-pay-employers-national-insurance-contributions/Exemption-from-employers-national-insurance/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/overview-of-salary-and-other-benefits/holiday-pay-from-sickness-benefit-from-the-national-insurance-scheme/
- https://www.skatteetaten.no/en/person/taxes/get-the-taxes-right/employment-benefits-and-pensions/deduction-for-trade-union-fees/
- https://www.afp.no/om-oss/aktueltsaker/premie-for-2026/
- https://www.afp.no/om-oss/aktueltsaker/premie-for-2027/
- https://www.afp.no/bedrift/premie-og-faktura/premie-og-premiemodell/
- https://www.afp.no/bedrift/premie-og-faktura/sliterordningen/
- https://www.revisorforeningen.no/andre-nyheter/pensjon0122/
- https://www.spk.no/virksomhet/slik-rapporterer-du/medlemsskap/

Følgende tall kom bare fra søkesammendrag, ikke fra åpnede sider: rapporteringsgrensen på 2 000 kr i a-meldingen og gamle tall for skattetrekkskonto (frigiving av saldo under 12 000 kr). Digdir-presentasjonen om NAVs API for sykepenger og navikt/sokos-oppgjorsrapporter ble heller ikke åpnet.
