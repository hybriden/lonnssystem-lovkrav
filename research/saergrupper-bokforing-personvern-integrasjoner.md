# Norske lovkrav til et lønnssystem (regler per 13.10.2026)

**Kildegrunnlag:** Jeg har åpnet sider på skatteetaten.no, lovdata.no, datatilsynet.no, nav.no, sdir.no, regjeringen.no og samarbeid.digdir.no, og lest Skatteetatens API-dokumentasjon på GitHub. I tillegg har jeg brukt kunnskapsbasen (bokføringsloven og -forskriften, a-opplysningsloven, skattebetalingsloven, NS 4102 og interne praksisdokumenter for 2026).
**Merking:** «⚠ Usikker» betyr at punktet ikke er fullt verifisert, eller at kildene spriker.

## Viktige korreksjoner til antakelsene i oppdraget
1. **Skattetrekkskontoen er avviklet fra 1.1.2026.**
   - Skattebetalingsloven (sktbl.) § 5-12 er opphevet ved LOV-2025-06-20-63.
   - Forskuddstrekk og utleggstrekk forfaller nå **senest første virkedag etter hver lønnsutbetaling** (sktbl. § 10-10 første ledd).
   - A-meldingen skal fra periode 2026-01 vise **«sum forskuddstrekk per lønnsutbetalingsdato»**.
   - Konto 1950 (skattetrekkskonto) brukes derfor ikke lenger for 2026. Gamle saldoer under 12 000 kr ble frigitt automatisk etter 10.4.2026. Større saldoer må arbeidsgiver søke frigitt med RF-1529.
2. **Sammenstillingsoppgaven har frist 1. februar, ikke 31. januar.**
   - Hjemmel: skatteforvaltningsforskriften (sff.) § 7-13-2. Den het § 7-12-2 før 2026. Fristen for lott eller part er 20. februar.
   - Oppgaven skal blant annet inneholde summerte ytelser, feriepengegrunnlaget, summert forskuddstrekk og ansattnummer. Trekkpliktig og trekkfri del av en ytelse skal vises hver for seg.
3. **RF-1199 lever videre som Oppdrags- og arbeidstakerregisteret.**
   - Det er en nettportal hos Skatteetaten (skatt.skatteetaten.no/web/oppdragsregister/). Papirskjemaene RF-1199E og RF-1198E finnes fortsatt.
   - Fra **17.11.2026** kan det ikke lenger rapporteres med gamle Altinn-roller. Tilgangspakker kreves.
4. **Altinn 2 er faset ut for lønn.**
   - A-melding sendt fra system (A02), tilbakemelding (A03) og avstemming (A06/A07) virket i Altinn II til **15.6.2026 kl. 12.00**.
   - Gamle skattekortforespørsler via RF-1211 er erstattet av nytt API fra 15.6.2026.
   - Skatteetaten la ikke tvangsmulkt for a-meldinger i mai, juni og juli 2026 på grunn av overgangen.
   - Altinn-roller kunne ikke delegeres etter 19.6.2026. Roller som allerede er delegert, gjelder ut 2026. Fra januar 2027 kreves tilgangspakker.

---

## 1. Særlige arbeidstakere og situasjoner

### Utenlandske arbeidstakere
**Skattekort og identifikasjon**
- Alle som arbeider i Norge, må ha skattekort, også når de ikke er skattepliktige til Norge.
- De må ha fødselsnummer eller D-nummer. D-nummer krever ID-kontroll hos skattekontoret, med noen unntak, blant annet for sokkel og sjøfolk på norske skip.
- Uten skattekort skal arbeidsgiver trekke **50 %** (sktbl. § 5-5 første ledd).
- Arbeidsgiver kan søke skattekort for arbeidstakeren med RF-1355.
- Arbeidsforholdet må være registrert før skattekortet kan hentes.
- Utenlandsk ID-nummer kan brukes midlertidig i a-meldingen, men må senere byttes til norsk ID.

**Kildeskatt på lønn (PAYE, skatteloven kap. 20)**
- Ordningen er frivillig. Satsene for 2026 er:
  - **25 %** for medlemmer av folketrygden.
  - **17,4 %** for ikke-medlemmer.
  - Inntektstaket er **725 050 kr**.
- Trekket er endelig skatt. Det gis ingen fradrag, ingen trekkfrie måneder og ingen halv skatt i desember.
- Feriepenger er trekkpliktige, og alle pendlerutgifter arbeidsgiver dekker, er trekkpliktige.
- Trekkgrunnlaget skal ikke reduseres for pensjonsinnskudd eller fagforeningskontingent.
- Skattekortet er merket «Kildeskatt på lønn». Lønnssystemet må lese og bruke denne merknaden.
- Ved nettolønnsavtale skal lønnen oppgrosses med satsen, og tabellnummer 0000 brukes.
- Arbeidsgiver er ansvarlig for riktig trekk (sktbl. § 16-20).
- ⚠ Usikker: Satsen for dem som bare betaler helsedelen av trygdeavgiften, er ikke funnet for 2026 (22,4 % gjaldt i 2025).

**Når personen blir skattemessig bosatt:** Ved opphold over 183 dager i en tolvmånedersperiode eller over 270 dager i en trettiseksmånedersperiode (skatteloven § 2-1 annet ledd).

**Oppholdstillatelse:** ⚠ Usikker. Utlendingsloven § 55 krever at tredjelandsborgere har oppholdstillatelse som gir rett til arbeid. Den konkrete plikten for arbeidsgiver til å kontrollere og ta kopi er ikke verifisert i paragrafteksten jeg åpnet.

### Utsending til og fra Norge, A1 og trygdeavtaler
**Arbeidstakere som kommer til Norge**
- Hovedregelen er at de er pliktige medlemmer av folketrygden, og arbeidsgiveravgift (AGA) skal betales (folketrygdloven § 23-2).
- Det gis bare fritak for AGA når Nav har registrert unntaket elektronisk hos Skatteetaten, og bare for perioden unntaket gjelder. A1 alene er ikke nok.
- Arbeidstakere utsendt fra USA eller Canada har en egen AGA-sats på **7 %**.
- Er personen medlem i et annet lands trygd i en periode som allerede er rapportert, korrigeres det med negativt avgiftsgrunnlag i måneden arbeidsgiver får vite det.

**Arbeidstakere som sendes ut fra Norge**
- Arbeidsgiver og arbeidstaker søker hver sin del hos Nav. Arbeidstakeren kan gi arbeidsgiver digital fullmakt.
- Nytt digitalt skjema kom 1.6.2026. Det krever enkelttjenesten «søknad om medlemskap i folketrygden eller lovvalgsavklaring», som ligger i tilgangspakken «ansettelsesforhold».
- A1 viser hvilket lands trygd som gjelder.
- ⚠ Usikker: Reglene for utsending utenfor EØS (blant annet frivillig medlemskap) er ikke detaljert her.

**Oppdrag til utenlandske oppdragstakere (skatteforvaltningsloven § 7-6, sff. §§ 7-6-1 til 7-6-7)**
- Oppdragsgiver melder oppdraget. Oppdragstakeren melder sine arbeidstakere. Plikten gjelder to ledd nedover i kontraktskjeden.
- Unntak: avtalt vederlag under 20 000 kr, kabotasje, Svalbard og oppdrag fra privatpersoner.
- Frist: den 5. i måneden etter oppstart, eller den 15. hvis arbeidet startet etter den 20. i måneden.
- Personer uten norsk ID skal dokumenteres med kopi av legitimasjon med bilde (sff. § 7-6-2).

**Utenlandske arbeidsgivere**
- De skal levere a-melding uansett skatteavtale.
- Uten norsk adresse brukes sone 1.
- Skattekontoret kan etter søknad gi utsatt forfall for trekket til den 5. i måneden etter, når det er uklart hvor mye som er trekkpliktig til Norge (skattebetalingsforskriften § 10-10-8).

### Arbeid i utlandet (ettårsregelen)
- Hjemmel: skatteloven § 2-1 tiende ledd. Den som er bosatt i Norge, kan kreve skatten satt ned for lønn for arbeid i utlandet under et opphold på minst 12 måneder sammenhengende.
- Opphold i Norge kan i snitt være høyst 6 dager per hele måned, eller 9 dager hvis grunnen var uforutsett.
- Regelen gjelder ikke når skatteavtalen gir bare Norge rett til å skattlegge inntekten.
- Fritaket gjennomføres med endret skattekort på forskuddsstadiet. Lønnssystemet trekker etter skattekortet og må kunne oppgi **opptjeningsland** i a-meldingen.

### Sjøfolk
- Sjømannsfradrag 2026: **30 %, høyst 86 300 kr**. Fradraget gis i skatteoppgjøret, ikke i lønnssystemet.
- Tilskuddsordningen for sjøfolk («nettolønnsordningen») heter i dag «tilskudd til sysselsetting av arbeidstakere til sjøs» (forskrift FOR-2016-02-26-204, Sjøfartsdirektoratet).
  - Tilskuddet beregnes av innbetalt forskuddstrekk, trygdeavgift og AGA per kvalifisert sjømann. For NIS er det 26 %. I flere modeller er det 37 584 kr per termin per arbeidstaker.
  - Det søkes per termin med frist den 25. i måneden etter terminen. Søknaden krever revisorbekreftelse.
- ⚠ Usikker: Satsene for 2026 er ikke bekreftet (37 584 kr per termin er siste tall jeg fant). Søknadsfristene er hentet fra et søkeresultat; siden ble ikke åpnet.

### Svalbard og Jan Mayen
**Svalbard**
- Egen svalbardskattelov. Lønnstrekket er en bruttoskatt.
- Satser 2026:
  - **8 %** av lønn opp til 12 G (1 638 588 kr fra 1.5.2026).
  - **22 %** av det som overstiger.
  - Trygdeavgift **7,6 %** av lønn og **5,1 %** av pensjon.
  - AGA er **0 %**.
- Det finnes ikke skattekort, frikort eller trekkfrie måneder på Svalbard.
- Nytt fra 2026 er et **ungdomsfribeløp på 100 000 kr** for personer som er 13–19 år ved utgangen av året. Arbeidsgiver trekker likevel fra første krone, og Skatteetaten refunderer løpende.
- Det sendes **ikke egen a-melding**. Svalbard håndteres i vanlig a-melding:
  - Ytelser, forskuddstrekk og fradrag merkes med skatte- og avgiftsregel «Svalbard».
  - AGA rapporteres med beregningskode «Lønnstrekk Svalbard» og sone 5.
  - Oppholdet rapporteres med opphold-ID, start- og sluttdato.
- Omfattet er personer som er bosatt på Svalbard, og andre med sammenhengende opphold over 30 dager. Reisedager telles ikke, og et avbrudd starter tellingen på nytt.
- Naturalytelser verdsettes etter egen forskrift for Svalbard.

**Jan Mayen**
- Egen lov gjelder.
- ⚠ Usikker: Jeg fikk ikke lest reglene om satser og AGA for Jan Mayen. Systemet må likevel støtte skatteregel «Jan Mayen» i a-meldingen.

### Styrehonorar
- Styrehonorar er alltid trekkpliktig, men det trekkes ikke når beløpet er under minstegrensene.
- Det er AGA-pliktig, med unntak ved registrert A1 eller trygdeavtale.
- Det rapporteres som kontantytelse «Styrehonorar og godtgjørelse i forbindelse med verv».
- Styremedlemmet rapporteres med arbeidsforholdstype «frilansere, oppdragstakere og honorarmottakere», og bare i måneder det utbetales noe.
- Mottakere bosatt i utlandet er trekkpliktige (fra 2019), og skattemessig bostedsland skal oppgis.
- Styremedlemmer er ikke arbeidstakere etter ferieloven, så det beregnes ikke feriepenger. ⚠ Usikker: dette er min konklusjon, ikke uttrykkelig sagt på Skatteetatens side.

### Honorar til frilansere og ikke-ansatte
- Rapporteres i a-melding med samme arbeidsforholdstype som over, i utbetalingsmånedene. De registreres i Aa-registeret (siden 2021).
- **Selvstendig næringsdrivende** med reell virksomhet for egen regning og risiko er unntatt AGA og a-melding.
- Beløpsgrenser for opplysningsplikt:
  - Lønn: plikt når samlet utbetaling til en person overstiger **2 000 kr** i året.
  - Skattefrie organisasjoner: plikt når samlet utbetaling overstiger **10 000 kr** (sff. § 7-2-1). Da rapporteres hele beløpet.
  - Arbeid i privat hjem: forenklet a-melding når lønnen til én person overstiger 6 000 kr i året. Husholdningen er ordinær arbeidsgiver over 60 000 kr.

### Barn under 13 år
- Arbeidsinntekt opp til **10 000 kr** per år er skattefri. Grensen gjelder samlet for barnet, ikke per arbeidsgiver.
- Det trekkes ikke skatt og beregnes ikke AGA.
- Utbetalingen skal likevel rapporteres, med beskrivelse «skattefri arbeidsinntekt barn under 13 år». For timelønn skal antall timer oppgis.
- Passive honorarer, for eksempel for fotografering av babyer til reklame, er ikke omfattet.
- Beløpet over grensen skattlegges sammen med foreldrene.
- Arbeidsmiljøloven § 11-1 forbyr i utgangspunktet barnearbeid. Kultur-, idretts- eller reklamearbeid krever forhåndstillatelse fra Arbeidstilsynet.
- ⚠ Usikker: Skatteetatens side er sist oppdatert i 2019, så kontroller at grensen fortsatt er 10 000 kr.

### Ungdom under 18 år (arbeidsmiljøloven kap. 11)
- Under 15 år eller i skolepliktig alder:
  - Høyst **2 timer per dag og 12 timer per uke** i skoleuker.
  - Høyst **7 timer per dag og 35 timer per uke** i skolefrie uker.
- 15–18 år og ikke skolepliktig: høyst **8 timer per dag og 40 timer per uke**.
- Timer hos flere arbeidsgivere legges sammen (§ 11-2).
- Nattarbeid er forbudt (§ 11-3), og det gjelder egne krav til pauser og fritid (§ 11-5).
- Frikort gis fra året personen fyller 13. OTP-medlemskap gjelder fra 13 år.

### Studenter og pensjonister
- Det finnes ingen særskilte unntak fra trekk eller AGA. Trekk skjer etter skattekortet.
- Frikortgrensen 2026 er **100 000 kr**. Når frikortet er brukt opp og nytt skattekort ikke er hentet, trekkes 50 %.
- Den ansatte fordeler selv frikortbeløpet mellom flere arbeidsgivere.
- Feriepengetillegget for ansatte over 60 år er 2,3 prosentpoeng. Taket på 6 G gjelder bare tillegget, med G per 31.12. i opptjeningsåret (819 294 kr for opptjeningsåret 2026). Tillegget er trekkpliktig.
- Andre pensjoner og lignende ytelser uten skattekort trekkes med 30 %.

### Lønn ved dødsfall
| Situasjon | Behandling |
|---|---|
| Lønn eller feriepenger opptjent før dødsfallet, men utbetalt etter («lønn etter dødsfall») | Ikke trekk, ikke AGA. Beskattes som kapitalinntekt hos boet eller arving. |
| Opptjent og utbetalt etter dødsfallet (etterlønn) | Skattefritt opp til 1,5 G (204 824 kr fra 1.5.2026), rapporteres som «etterbetalt lønn – skattefri». Det overskytende er trekkpliktig, men ikke AGA-pliktig. |
- Opptjente feriepenger utbetales til boet sammen med sluttoppgjøret (ferieloven § 11 nr. 5).
- ⚠ Usikker: Det er uavklart om inntektsmottaker i a-meldingen skal være avdødes fødselsnummer eller boets identifikator. Siden jeg leste, sier det ikke.

### Lønn ved konkurs
- Lønnsgarantien dekker inntil **2 G på fristdagen** (273 098 kr med G fra 1.5.2026), for høyst 6 måneder med lønnsperioder.
- Krav som forfalt mer enn 12 måneder før fristdagen, dekkes ikke. Feriepenger opptjent i fristdagens år og året før dekkes.
- Søknaden går til bostyrer, som kontrollerer den og sender den til Nav. Bostyrer trekker skatt og betaler ut nettobeløpet.
- Det trekkes aldri forskuddstrekk i feriepenger fra lønnsgarantien.
- Det er et vilkår for dekning at arbeidsgiver har betalt AGA for arbeid i Norge.
- ⚠ Usikker: Hvem som rapporterer garantiutbetalingene i a-ordningen, er ikke bekreftet.

### Lønn i utenlandsk valuta
- A-meldingen rapporteres i norske kroner.
- Bokføringsforskriften § 4-2: lønn omregnes etter kursen på **utbetalingstidspunktet**. Det gjelder også når bokføringen skjer i funksjonell valuta.
- Systemet bør lagre valuta, kurs, kursdato og kilde (for eksempel Norges Bank).
- ⚠ Usikker: Jeg fant ingen side i a-meldingsveiledningen som eksplisitt sier hvilken kurs som skal brukes.

### Lønnsforskudd og lån til ansatte
**Skattemessig**
- Lån og forskudd fra arbeidsgiver, også lønnsforskudd, omfattes av reglene om rimelige lån (skatteloven § 5-12 fjerde ledd).
- Rentefordelen er forskjellen mot normrenten og rapporteres som «naturalytelse, rentefordel lån». Den er trekk- og AGA-pliktig.
- Normrenten 2026: 4,8 % i alle perioder unntatt september–oktober, som har 4,7 %. ⚠ Tallet for november–desember (4,8 %) er gjengitt slik siden viser det, men bør kontrolleres.
- Lån på høyst **3/5 G** (81 929 kr) som tilbakebetales innen ett år, er fritatt.

**Selskapsrettslig**
- Aksjeloven § 8-7: kreditt til aksjeeier eller nærstående kan bare gis innenfor utbytterammen og mot betryggende sikkerhet.
- § 8-9 gjelder det samme for **styremedlem, daglig leder og medlem av bedriftsforsamlingen** og deres nærstående.
- Unntak etter § 8-8: ansatt aksjonær i hovedstilling som eier høyst 5 %, når lånet er på vanlige vilkår for ansatte. Unntaket gjelder ikke for daglig leder etter § 8-9.
- Lån i strid med reglene er ugyldige (§ 8-11).
- Skatteloven § 10-11 fjerde ledd: lån til personlig aksjonær skattlegges som utbytte.

**Nedbetaling ved trekk i lønn**
- Krever skriftlig forhåndsavtale (arbeidsmiljøloven § 14-15 annet ledd bokstav c).
- Trekket kan bare gjelde det som overstiger det arbeidstakeren rimelig trenger til livsopphold for seg og husstanden.

### Etterbetaling, tilbakebetaling og reverserte utbetalinger
- **Etterbetaling** rapporteres i utbetalingsmåneden. Tidligere a-meldinger endres ikke. Er timer rapportert tidligere, settes antall timer til 0.
- **Feil** rettes i a-meldingen for måneden feilen gjelder. Det kan gjøres på to måter:
  - Erstatningsmelding, som må være fullstendig og vise til meldingsID-en den erstatter.
  - Ny melding med bare differansen.
- **For mye utbetalt lønn:** a-meldingen korrigeres når beløpet er tilbakebetalt eller det er inngått bindende avtale om tilbakebetaling, det som skjer først.
  - **Netto** tilbakebetaling, der også trekket korrigeres, gjelder når avtalen eller tilbakebetalingen skjer før 31. januar året etter, eller etter at skatteoppgjøret for feilåret er ferdig.
  - Ellers skjer tilbakebetalingen **brutto**. Trekket står da uendret og godskrives i skatteoppgjøret.
  - ⚠ Den engelske siden ser ut til å ha en skrivefeil i vilkåret for brutto. Min lesning er «etter 31. januar og før skatteoppgjøret er ferdig». Bør kontrolleres mot den norske siden.
- **AGA for et tidligere år** kan endres i måneden ny informasjon blir kjent, i måneden eller månedene endringen gjelder, eller i desember.
- **Reverserte utbetalinger**, for eksempel lønn returnert fra banken: ⚠ Min vurdering. Kontantprinsippet tilsier at en utbetaling som aldri ble gjennomført, rettes som feil i den opprinnelige perioden. Ny utbetaling rapporteres på ny dato, med ny trekkfrist.

---

## 2. Bokføring og dokumentasjon

**Dokumentasjon av lønn (bokføringsforskriften § 5-6, endret fra 1.1.2026)**
- Dokumentasjonen skal vise ytelser, forskuddstrekk og utleggstrekk **per mottaker**, med fødselsnummer, navn, skattekommune og tabellnummer eller trekkprosent.
- Uten skattekort brukes bostedskommunen per 1.11. året før.
- Ved trekkpålegg (utleggstrekk) skal det fremgå når pålegget ble mottatt, og hvilken prosent eller hvilket beløp som skal trekkes per periode.
- Per rapporteringsperiode skal det fremgå:
  - utbetalingsdato og om mulig perioden ytelsen gjelder
  - brutto ytelse og godtgjorte timer
  - naturalytelser
  - fradrag etter sktbl. § 5-9
  - trekkgrunnlag
  - foretatt trekk
- For timelønte: dato for arbeidet, timer per dag og sum timer for perioden.
- Dokumentasjonen skal utstedes **senest når ytelsen kan utbetales**.
- Det skal finnes en **lettfattelig beskrivelse av lønnssystemets oppbygging og funksjoner**.

**Lønnsslipp:** Arbeidstakeren skal ved eller rett etter utbetalingen få en skriftlig oppgave over beregningen av lønn, grunnlaget for feriepenger og trekk (arbeidsmiljøloven § 14-15 femte ledd). Lønn skal utbetales minst to ganger i måneden, med mindre annet er avtalt.

**Spesifikasjon (bokføringsforskriften § 3-1 nr. 9):** Lønnsopplysningspliktige ytelser skal kunne spesifiseres per periode etter kontoene i regnskapssystemet. AGA-pliktige ytelser skal kunne vises samlet per sats og sone.

**Grunnprinsipper i bokføringsloven**
- § 4: fullstendighet, nøyaktighet, toveis sporbarhet og sikring.
- § 6: nummerering og dokumentert kontrollspor for systemgenererte poster.
- § 9: etter fristen rettes det med ny postering som reverserer den opprinnelige i sin helhet. Det er ikke nok å postere differansen, og sletting skal fremgå.
- Bokføringsforskriften § 5-12: korrigeringsbilag skal vise årsak og ha referanse til opprinnelig dokumentasjon.
- Bokføringsforskriften § 7-6: perioder skal lukkes med betryggende sikring mot endring, og det skal finnes en beskrivelse av lukkefunksjonen.
- Ajourhold: a-meldingen utløser ikke i seg selv plikt til ajourhold (bokføringsforskriften § 4-1).

**Oppbevaring**

| Hva | Hvor lenge | Hjemmel |
|---|---|---|
| Pliktig regnskapsrapportering, spesifikasjoner og bilag (nr. 1–4), også lønnsdokumentasjon | 5 år etter regnskapsårets slutt | bokføringsloven § 13 annet ledd. 5 år gjelder fra 1.2.2014, før var det 10 år. |
| Avtaler, korrespondanse mv. (nr. 5–8) | 3 år og 6 måneder | samme |
| Dokumentasjon av arbeidede timer (§ 5-6) | 3 år og 6 måneder | bokføringsforskriften § 7-3 |
| Elektronisk tilgjengelighet for bokførte opplysninger | 3 år og 6 måneder (unntak ved omsetning under 5 mill. kr) | bokføringsloven § 13 b, bokføringsforskriften § 7-7 |
| Fortegnelse over sikkerhetskopiering, og beskrivelse av lukkefunksjon | 5 år | bokføringsforskriften §§ 7-2 og 7-6 |

- **Sikkerhetskopi** skal oppbevares adskilt fra originalen og testes minst én gang i året (bokføringsforskriften § 7-2).
- **Fra 1.1.2027:** e-faktura skal oppbevares i opprinnelig format (LOV-2026-06-19-39). Tidene er ellers uendret.
- **Lagring i utlandet:** elektronisk materiale kan lagres i EØS, Storbritannia eller Sveits når det er lesbart og kan skrives ut fra Norge, og skattekontoret har fått **skriftlig melding** om hva, hvor og hvordan det er tilgjengelig (bokføringsforskriften § 7-5, ny ordlyd fra 27.1.2025). Lagring i andre land, for eksempel en amerikansk sky-region, er ikke dekket.

**Kontoplan (NS 4102 / SAF-T standardkonti)**
- NS 4102 er ikke pålagt. NS 4102:2023 har femsifrede konti som alle slutter på 0.
- Vanlige konti:
  - **Kostnader:** 5000 lønn, 5090 påløpt lønn, 5092 feriepenger, 52xx/5290 naturalytelser med motkonto, 5400 AGA, 5405 AGA av feriepenger, 5800 refusjon av sykepenger, 5950 OTP.
  - **Gjeld:** 2600 forskuddstrekk, 2610 utleggstrekk, 2650 fagforeningstrekk, 2770 skyldig AGA, 2780 og 2781 påløpt AGA, 2930 skyldig lønn, 2940 skyldige feriepenger.
  - **Fordring:** 1579 krav på refusjon fra Nav.
- 1950 skattetrekkskonto brukes ikke for 2026. Konto 2600 avstemmes mot trekk betalt første virkedag etter hver utbetaling.

**Avstemming**
- Avstemmingsrapporten for a-meldingen (tidligere A06/A07) hentes nå via API eller avstemmingsportalen.
- Lønn, AGA og trekk avstemmes mot regnskapet.
- Kontroller tilbakemeldingen (A03) etter hver innsending.
- A-meldingen er også arbeidsgivers skattemelding for AGA og finansskatt (skatteforvaltningsloven § 8-6).

**Revisjon og kontroll:** Bokføringsloven § 14 gir plikt til å bistå kontrollmyndighetene. SAF-T Regnskap kan kreves (bokføringsforskriften § 7-8). Lønnsdetaljer er ikke del av SAF-T Regnskap, så de må kunne leveres separat.

---

## 3. Personvern og sikkerhet

**Behandlingsgrunnlag**
- GDPR art. 6(1)(b): arbeidsavtalen.
- GDPR art. 6(1)(c): rettslige plikter, som a-meldingen, bokføring og forskuddstrekk.
- Samtykke er normalt ikke egnet i arbeidsforhold.

**Særlige kategorier (GDPR art. 9)**
- Fagforeningsmedlemskap, som følger av fagforeningstrekk, og helseopplysninger, som sykefravær og refusjon, er særlige kategorier.
- Grunnlaget er art. 9(2)(b) sammen med personopplysningsloven § 6 (særlige kategorier i arbeidsforhold, når det er nødvendig for arbeidsrettslige plikter eller rettigheter).
- Lønnssystemet skal ikke lagre diagnose. Sykefravær lagres bare som perioder og ytelser.
- Nav krever tilgangspakken «Lønn med personopplysninger av særlig kategori» for inntektsmelding.

**Fødselsnummer (personopplysningsloven § 12):** Kan bare brukes når det er saklig behov for sikker identifisering og metoden er nødvendig. Lønn oppfyller kravet, fordi fødselsnummer kreves av bokføringsforskriften § 5-6 og a-opplysningsloven § 3. Fødselsnummer bør likevel ikke brukes som synlig nøkkel, i URL-er eller i logger.

**Lagringstid og sletting**
- Lagringsbegrensning (art. 5(1)(e)) gir vei for lovpålagt oppbevaring etter art. 17(3)(b).
- Lønnsbilag og spesifikasjoner beholdes i 5 år etter regnskapsåret, timelister i 3 år og 6 måneder.
- Datatilsynet sier at slutt på arbeidsforholdet som regel er yttergrensen for opplysninger brukt til personaladministrasjon. Unntak er tvist og forsvar av rettskrav.
- Konsekvens: systemet må skille regnskapspliktige data fra HR-data og ha regelbasert sletting per datakategori.

**Innsyn:** Art. 15 gir den ansatte rett til innsyn i alt, også eventuelle skyggearkiv. Svar skal gis uten ugrunnet opphold, normalt innen én måned. A-opplysningsloven § 9 gir inntektsmottakeren innsyn i opplysninger om seg selv i a-ordningen. Personvernreglene gir ikke andre rett til innsyn i andres lønn.

**Tilgangsstyring og sikkerhet**
- Tilgang bare ved tjenstlig behov, med logging og internkontroll (art. 32 og Datatilsynets veileder om personalmappe).
- Dette faller sammen med bokføringslovens krav til sikring mot urettmessig endring.

**Databehandler og overføring**
- Databehandleravtale etter art. 28 med lønnsleverandør og driftsleverandør.
- Overføring utenfor EØS krever grunnlag etter kap. V: adekvansbeslutning, for eksempel EU–US Data Privacy Framework, eller standardavtaler (SCC) med vurdering av overføringen (TIA).
- Bokføringsforskriften § 7-5 begrenser uansett oppbevaring av regnskapsmateriale til EØS, Storbritannia og Sveits.

**DPIA:** Vanlig lønnsbehandling står ikke på Datatilsynets liste over behandlinger som alltid krever DPIA. Lista gjelder blant annet systematisk overvåking av ansatte og overvåking av effektivitet eller prestasjon. DPIA bør vurderes ved stor skala eller når lønn kobles med tidsregistrering og prestasjonsdata.

**Sending av lønnsslipp (Datatilsynet, 2018)**
- Ukryptert sending er bare greit til interne adresser når slippen aldri forlater virksomhetens eget system.
- Sendes den fra en ekstern part, som et lønnsbyrå, må enten kanalen eller filen være kryptert.
- Til **privat e-post må selve slippen være kryptert**. Kryptert kanal er ikke nok.
- Passordet skal ikke være fødselsdato.
- Anbefalt løsning er en portal med TLS og tofaktorautentisering, eller digital postkasse.

---

## 4. Integrasjoner

| Tjeneste | Maskinporten-scope | Systembruker / tilgangspakker | Merknad |
|---|---|---|---|
| A-melding: REST-API (under 10 MB), filopplastings-API (større filer) og tilbakemeldings-API | `skatteetaten:innrapporteringamelding` | Ressurs `ske-innrapportering-amelding`. Pakker: a-ordning, regnskapsforer-lonn, regnskapsforer-med- og -uten-signeringsrettighet, ansvarlig-revisor, revisormedarbeider | Tilbakemeldingen hentes ved å lytte på hendelser i **Dialogporten**. Gjeldende format er a-melding v2.3 (XSD 20240827), med kodelister R1 2026. Siste dato for innfasing av lønnssystemer var 31.5.2026, deretter forlenget til 15.6.2026. |
| Avstemmingsrapport (tidligere A06/A07) | samme | Ressurs `ske-avstemmingsinformasjon-amelding` | Bare JSON. I produksjon fra 3.6.2026, ny versjon 11.9.2026. |
| Skattekort til arbeidsgiver (erstatter RF-1211) | `skatteetaten:skattekorttilarbeidsgiver` | Ressurs `ske-skattekort-til-arbeidsgiver`. Pakker: lonn, regnskapsforer-lonn, skatt-naering, regnskapsfører- og revisorpakker | Bestilling med typene `HENT_ALLE_OPPGITTE` eller `HENT_KUN_ENDRING` og varsling. Høyst 1000 fødselsnumre per kall. Svaret har trekkode (hovedarbeidsgiver, biarbeidsgiver, Nav, pensjon), tabellnummer, prosentsats, antall måneder med trekk og frikortbeløp. Fra 15.12.2026 lager kall ikke lenger dialoger i Dialogporten. Midlertidig reserveløsning med opplasting av XML (høyst 1 MB). |
| Nav inntektsmelding (sykepenger) | `nav:helseytelser/sykepenger` (fra Navs kodelager) | Systembruker. Pakken «Lønn med personopplysninger av særlig kategori» | Sendes som svar på forespørsel fra Nav. Endret inntektsgrunnlag må begrunnes. Bare sykepenger kan sendes fra lønnssystem. Foreldrepenger, pleiepenger og omsorgspenger sendes manuelt eller via API som er under utvikling. |
| Enhetsregisteret | Åpent API (data.brreg.no) | – | Brukes til organisasjonsnummer, underenheter og sone. ⚠ Ikke åpnet i denne researchen. |

**Oppkobling for leverandøren (Skatteetaten og Digdir)**
1. Opprett Maskinporten-klient med reelt organisasjonsnummer.
2. Signer Altinn-vilkår og be om scopes for systembruker (`altinn:authentication/systemuser.request.read` og `.write`, `altinn:authentication/systemregister.write`).
3. Registrer systemet i Altinns **systemregister**.
4. Søk tilgang til Skatteetatens tjenester via brukerstøtte (eksternjira.sits.no) og aksepter Skatteetatens bruksvilkår.
5. Bygg flyten der kunden godkjenner forespørselen om systembruker i Altinn. Kunden kan trekke godkjenningen.
6. Test i Skatteetatens og Digdirs testmiljø. Testpersoner finnes i Tenor, og manuell XML-opplasting i test er tilgjengelig på ameldingfilopplasting.skatteetaten-test.no.

Det finnes ingen formell sertifiseringsordning. Kravet er tilgang til scope og aksepterte bruksvilkår. Systembruker erstatter virksomhetssertifikatet.

**A-meldingsregler som systemet må håndheve**
- **F527:** lønnsutbetalingsdatoen må ligge innenfor rapporteringsperioden.
- **F277-2:** fanger bare opp negativ totalsum for trekk. Skatteetaten ber systemene i tillegg hindre negativ sum per utbetalingsdato.
- **Utleggstrekk:** ny kode «Utleggstrekk samordnet» krever dato. Den har eget kontonummer og egen KID per arbeidstaker.

**Avgrensning:** Inntektsmottakere-API-et er ikke relevant for lønnssystemer. Det krever særskilt lovhjemmel og er ikke tilrettelagt for systembruker.

---

## 5. Årshjul for lønn 2026/27

**Løpende**
- Forskuddstrekk og utleggstrekk betales **første virkedag etter hver utbetaling**. Fredagslønn gir frist mandag.
- A-melding senest den **5. i måneden etter**, flyttet til første virkedag ved helg eller helligdag. Utsatt frist gis ikke.
- Tvangsmulkt er 1/10 rettsgebyr per inntektsmottaker per dag (134 kr i 2026), høyst 1000 rettsgebyr. Overtredelsesgebyr er ¼ rettsgebyr per dag, høyst 15 rettsgebyr.
- Oppdrag og arbeidstakere etter sff. § 7-6 meldes den 5. eller 15. i måneden etter.
- Refusjonskrav til Nav dekkes bare inntil 3 måneder før måneden kravet settes fram (folketrygdloven § 22-13).
- Normrenten fastsettes for hver tomånedersperiode.
- Melding om oppstart og opphør av arbeidsforhold gis i den ordinære a-meldingen.

**Frister for a-melding 2026**
- 5.1, 5.2, 5.3, 7.4, 5.5, 5.6, 6.7, 5.8, 7.9, 5.10, 5.11, 7.12.
- For desember 2026: 5.1.2027.

**AGA og finansskatt (5 %) per termin, sktbl. § 10-10 annet ledd**
- 15.1, 16.3, 15.5, 15.7, 15.9 og 16.11.2026, og 15.1.2027.
- AGA-satser 2026:
  - Sone I: 14,1 %.
  - Sone Ia: 10,6 % inntil fribeløpet på 850 000 kr er brukt opp.
  - Sone II: 10,6 %.
  - Sone III: 6,4 %.
  - Sone IV: 5,1 %.
  - Sone IVa: 7,9 %.
  - Sone V: 0 %.
- Den ekstra AGA-en på 5 % er fjernet fra 2025.

| Når | Hendelse |
|---|---|
| Desember | Halv skatt: siste halvdel av november eller første halvdel av desember er trekkfri for månedslønte (skattebetalingsforskriften § 5-7-2). En stor bonus er ikke omfattet. Skattekort for neste år bestilles for det nye inntektsåret. ⚠ Usikker: publiseringsdato i desember er ikke bekreftet. Årsavslutning med avsetning av feriepenger (2940) og AGA av dem (2781). |
| Januar | Nye satser og tabeller. Mangler nytt skattekort, trekkes januar etter fjorårets kort, og trekket korrigeres innen utløpet av februar (skattebetalingsforskriften §§ 5-5-1 og 5-5-2). 5.1 frist for føderåd. 15.1 frist for årlig rapportering ved trekkfritak for § 7-6-pliktige. 31.1 er skillet for netto/brutto tilbakebetaling av lønn. Feriepengegrunnlaget for opptjeningsåret låses. |
| 1. februar | **Sammenstillingsoppgave** til alle inntektsmottakere (sff. § 7-13-2). Frist 20.2 for lott og part. |
| Mars–mai | Søknader om sjøfolkstilskudd per termin. 1.5 reguleres G (2026: 136 549 kr), som påvirker 1,5 G, 2 G, 3/5 G, 6 G og 12 G. Nav betaler feriepenger av sykepenger og foreldrepenger i annen halvdel av mai. 31.5 skattemelding for AS og næringsdrivende. |
| Juni | **Feriepenger** utbetales siste vanlige lønningsdag før ferien (ferieloven § 11). Satser: 10,2 %, 12 % ved avtalt femte ferieuke, tillegg på 2,3 prosentpoeng over 60 år. Feriepenger i ferieåret er trekkfrie. Avtalte feriepenger som overstiger lovens med mer enn 21 %, er trekkpliktige for det overskytende. Månedslønte kan i stedet få trekkfri juni. Ved fratreden er feriepenger trekkpliktige. |
| Hele året | OTP: minst 2 % av lønn fra første krone opp til 12 G (OTP-loven § 4). Pensjonsinnretningen identifiseres i a-meldingen (§ 7). Tilskuddet er AGA-pliktig. AFP: premien fastsettes av Fellesordningen. ⚠ Usikker: sats og forfall for 2026 er ikke bekreftet (2,7 % mellom 1 og 7,1 G er siste tall jeg fant). |
| Annethvert år | Lønnskartlegging etter kjønn og kartlegging av ufrivillig deltid (likestillings- og diskrimineringsloven § 26). Gjelder offentlige virksomheter, private med jevnlig mer enn 50 ansatte, og private med 20–50 ansatte når en av partene krever det. Redegjørelse i årsberetningen (§ 26 a). |
| Ferdig | Altinn 2-tilgang for lønn opphørte 15.6.2026. Roller gjelder ut 31.12.2026. Fra 17.11.2026 kreves tilgangspakker i oppdragsregisteret. Fra januar 2027 kreves tilgangspakker generelt. E-fakturakrav fra 1.1.2027. |

---

## Krav til lønnssystemet

**A. Særlige grupper og situasjoner**
1. **Skattekort**
   - Hente skattekort via API, både alle og bare endringer, og ta imot varsel.
   - Bruke trekkode for hovedarbeidsgiver og biarbeidsgiver.
   - Gi 50 % trekk når skattekort mangler.
   - Telle frikortbeløp og bytte til 50 % trekk når det er brukt opp.
   - Lese merknaden for kildeskatt (PAYE). Ved PAYE: ingen trekkfrie måneder og pendlerdekning i trekkgrunnlaget.
2. **Identifikasjon og arbeidsforhold**
   - Støtte D-nummer og midlertidig utenlandsk ID, med varsel om bytte til norsk ID.
   - Oppgi opptjeningsland og skattemessig bostedsland.
   - Støtte arbeidsforholdstype for frilansere, oppdragstakere og honorarmottakere, og rapportering bare i måneder med utbetaling.
3. **Trygd og AGA**
   - Registrere trygdeunntak per periode (A1).
   - Bruke beregningskodene, også egen sats for USA og Canada og «Lønnstrekk Svalbard» med sone 5.
   - Bruke sone per underenhet og fribeløp i sone Ia.
4. **Skatteregler i a-meldingen**
   - Støtte skatteregel «Svalbard» og «Jan Mayen».
   - For Svalbard: 8/22 % med 12 G-grense, trygdeavgift 7,6/5,1 %, oppholdsrapportering og ungdomsfribeløp.
5. **Spesielle ytelser**
   - Barn under 13: skattefri inntekt opp til 10 000 kr, med kontroll av akkumulert beløp.
   - Styrehonorar: trekkpliktig, ikke feriepengegrunnlag.
   - Lønn etter dødsfall og etterlønn: grense på 1,5 G, uten AGA.
   - Lønnsgaranti ved konkurs.
   - Rentefordel på lån etter normrente per periode, med fritak for lån inntil 3/5 G nedbetalt innen ett år.
   - Trekk i lønn bare med hjemmel etter arbeidsmiljøloven § 14-15 (skriftlig avtale), og ned til nivået for livsopphold.
   - Ved utenlandsk valuta: lagre kurs per utbetalingsdato.
6. **Korrigering**
   - Skille mellom etterbetaling, som rapporteres i utbetalingsmåneden, og feil, som rettes i opprinnelig måned.
   - Erstatningsmelding eller tilleggsmelding.
   - Netto eller brutto tilbakebetaling etter 31.1-regelen.
   - AGA-korrigering for tidligere år i valgfri måned.
7. **Ungdom:** advare mot arbeidstid over grensene i arbeidsmiljøloven § 11-2 og mot nattarbeid under 18 år.

**B. Bokføring og dokumentasjon**
1. Dokumentasjon per mottaker med alle feltene i bokføringsforskriften § 5-6, også skattekommune, trekkpålegg, trekkgrunnlag og timer per dato. Den skal være utstedt senest på utbetalingstidspunktet.
2. Lønnsslipp med beregning, feriepengegrunnlag og trekk.
3. **Systembeskrivelse** av lønnssystemet (§ 5-6 siste ledd), beskrivelse av lukkefunksjonen (§ 7-6) og dokumentert kontrollspor (bokføringsloven § 6).
4. Spesifikasjon av lønnsopplysningspliktige ytelser per periode og konto, og AGA per sats og sone (§ 3-1 nr. 9).
5. Konfigurerbar kontoplan med NS 4102/SAF-T-mapping. Ingen bruk av 1950 for 2026.
6. Avstemmingsrapport: regnskap mot a-melding mot A03 mot avstemmingsrapport-API. Avstemme 2600 per betalingsdato.
7. Uforanderlige poster: retting etter fristen ved full reversering, lukking av perioder og revisjonslogg for endringer.
8. Oppbevaring: 5 år for lønnsdokumentasjon og 3 år og 6 måneder for timer og elektronisk tilgjengelighet. Data lagres bare i Norge, EØS, Storbritannia eller Sveits, med varsel til skattekontoret. Sikkerhetskopi adskilt fra original og testet hvert år.
9. Eksport til kontrollmyndighet og revisor, også SAF-T.

**C. Personvern og sikkerhet**
1. Dokumentert behandlingsgrunnlag per datakategori: art. 6(1)(b)/(c), art. 9(2)(b) og personopplysningsloven § 6.
2. Ingen diagnoser. Fagforeningstrekk og helsedata med strengere tilgang.
3. Rollebasert tilgang etter tjenstlig behov, tofaktorautentisering, tilgangslogg og kryptering ved lagring og overføring.
4. Fødselsnummer maskert i grensesnittet, aldri i URL-er eller logger.
5. Lønnsslipp via portal med tofaktorautentisering eller digital postkasse. Filkryptering ved sending til privat e-post, med passord som ikke er fødselsdato.
6. Sletteregler per kategori, der bokføringsplikten går foran slettekravet. Innsyn og eksport for den ansatte.
7. Databehandleravtale (art. 28), oversikt over underleverandører og grunnlag for eventuell overføring ut av EØS.
8. Grunnlag for DPIA og risikovurdering.

**D. Integrasjoner**
1. Maskinporten-klient og registrering i systemregisteret.
2. Flyt for forespørsel om systembruker og håndtering av tilgangspakker (a-ordning, lonn, regnskapsforer-lonn, «Lønn med personopplysninger av særlig kategori»).
3. A-melding v2.3 via REST, med filopplasting for store filer. Tilbakemelding via Dialogporten. Avstemming via API.
4. Validering før sending: F527, ingen negativ trekksum per dato, «Utleggstrekk samordnet» med dato, og generering av KID.
5. Skattekort-API med batcher på høyst 1000. Reserveløsning: eksport av XML.
6. Nav inntektsmelding for sykepenger: svar på forespørsel, med begrunnelse ved endret inntektsgrunnlag.
7. Oppslag i Enhetsregisteret for organisasjonsnummer, underenheter og sone.
8. Testoppsett med Tenor, Skatteetatens testmiljø og test.maskinporten.no. Overvåke status.skatteetaten.no og nyheter for sluttbrukersystemer.

**E. Årshjul og frister**
1. Fristkalender med flytting ved helg og helligdag: trekk første virkedag etter utbetaling, a-melding den 5., AGA-terminer, sammenstillingsoppgave 1.2, korrigering av januartrekk innen februar, refusjonskrav innen 3 måneder.
2. Automatikk for feriepenger: satser, tillegg over 60 år med 6 G-tak, trekkfritak og 21 %-regelen, utbetaling ved fratreden og dødsfall.
3. Halv skatt i november/desember for månedslønte.
4. Oppdatering av G-avhengige beløp hver 1. mai, og av normrente annenhver måned.
5. OTP-beregning fra første krone opp til 12 G.
6. Uttrekk til lønnskartlegging etter kjønn og stilling.

---

## Gjenstående usikkerhet
- Jan Mayen: satser og AGA.
- PAYE-sats for dem som bare betaler helsedelen, for 2026.
- Sjøfolkstilskudd: satser og frister for 2026.
- AFP: premiesats og forfall for 2026.
- Om grensen på 10 000 kr for barn under 13 fortsatt gjelder (Skatteetatens side er fra 2019).
- Ordlyden i netto/brutto-regelen på den engelske siden.
- Inntektsmottaker ved dødsbo.
- Hvem som rapporterer lønnsgaranti ved konkurs.
- Valutakurs i a-meldingen.
- Arbeidsgivers kontrollplikt etter utlendingsloven.
- Publiseringsdato for skattekort for 2027.
- Utsending utenfor EØS (frivillig medlemskap).

## Kilder jeg åpnet
**Skatteetaten**
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/overview-of-salary-and-other-benefits/tax-free-employment-income-for-children-under-13/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/overview-of-salary-and-other-benefits/pay-after-death/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/overview-of-salary-and-other-benefits/back-payments-of-wages-and-pension-upon-death/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/overview-of-salary-and-other-benefits/directors-fees-and-remuneration-associated-with-holding-office/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/salary-and-benefits/correcting-errors-in-salary-and-other-benefits/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/the-a-melding-guide/employers-national-insurance-contributions-and-financial-activity-tax/employers-national-insurance-contributions/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/hjelp-til-a-gjore-riktig/who-is-obliged-to-submit-a-melding/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/siste-fra-a-ordningen/oppdatert-grunnbelop-i-folketrygden-fra-1.-mai-2026/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/siste-fra-a-ordningen/new-access-packages-for-the-a-melding-a-melding/
- https://www.skatteetaten.no/en/business-and-organisation/employer/the-a-melding/siste-fra-a-ordningen/nye-frister-for-betaling-av-forskuddstrekk-og-utleggstrekk/
- https://www.skatteetaten.no/nn/bedrift-og-organisasjon/arbeidsgiver/a-meldinga/rettleiinga-til-a-meldinga/sarskilde-grupper/svalbard
- https://www.skatteetaten.no/person/skatt/hjelp-til-riktig-skatt/svalbard/skatt-lonn/
- https://www.skatteetaten.no/en/rates/tax-rates-on-svalbard/
- https://www.skatteetaten.no/en/rates/normal-interest-rate-for-the-taxation-of-low-cost-loans-from-an-employer/
- https://www.skatteetaten.no/bedrift-og-organisasjon/arbeidsgiver/arbeidsgiveravgift/nar-skal-jeg-ikke-betale-arbeidsgiveravgift/
- https://www.skatteetaten.no/bedrift-og-organisasjon/arbeidsgiver/skattekort-og-skattetrekk/kildeskatt-pa-lonn/
- https://www.skatteetaten.no/en/forms/rf-1199-information-about-contracts-contractors-and-employees/
- https://www.skatteetaten.no/samarbeidspartnere/sluttbrukersystemer/sbs-nyheter/ingen-tvangsmulkt-for-a-meldingen-i-mai-juni-og-juli
- https://www.skatteetaten.no/samarbeidspartnere/sluttbrukersystemer/a-meldingen-sbs/
- https://www.skatteetaten.no/en/our-partners/end-user-systems/the-tax-deduction-card---for-end-user-systems/
- https://www.skatteetaten.no/en/our-partners/end-user-systems/sbs-nyheter/sum-forskuddstrekk-per-lonnsutbetalingsdato--presiseringer/
- https://www.skatteetaten.no/en/our-partners/reetablering-altinn/systemleverandor/oppkobling/

**Skatteetatens API-dokumentasjon**
- https://skatteetaten.github.io/api-dokumentasjon/anvendelsesomraader/skattekorttilarbeidsgiver, /api/skattekorttilarbeidsgiver og /api/innrapportering-amelding (lite innhold i nettleservisning)
- github.com/Skatteetaten/api-dokumentasjon: docs/api/skattekorttilarbeidsgiver.md, innrapportering-amelding.md, avstemmingsrapport-amelding.md, inntektsmottakere.md (lest via gh api)

**Nav, Digdir, Sjøfartsdirektoratet og regjeringen**
- github.com/navikt/sykepenger-im-lps-api (README)
- https://www.nav.no/arbeidsgiver/sende-inntektsmelding
- https://www.nav.no/lonnsgaranti
- https://samarbeid.digdir.no/altinn/systembruker/2542
- https://www.sdir.no/naringsfartoy/for-rederi/tilkudd-til-sysselsetting-av-sjofolk/om-tilskuddsordningen/
- https://www.regjeringen.no/no/tema/okonomi-og-budsjett/skatter-og-avgifter/skattesatser-2026/id3121978/

**Lovdata**
- https://lovdata.no/forskrift/2004-12-01-1558/§5-6
- https://lovdata.no/lov/2004-11-19-73/§13
- https://lovdata.no/forskrift/2016-11-23-1360/§7-13-2
- https://lovdata.no/dokument/NL/lov/2018-06-15-38 og https://lovdata.no/lov/2018-06-15-38/§12
- https://lovdata.no/lov/2005-06-17-62/§11-2 og §14-15 (kapitteloversikt for kap. 11)
- https://lovdata.no/lov/2017-06-16-51/§26a
- https://lovdata.no/lov/2008-05-15-35/§55
- https://lovdata.no/lov/1999-03-26-14/§2-1

**Datatilsynet**
- https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/kryptering-lonnsslipp/
- https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/personalmappe/
- https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/innsyn-i-lonnsopplysninger/
- https://www.datatilsynet.no/personvern-pa-ulike-omrader/personvern-pa-arbeidsplassen/sykdom-og-personvern-arbeidsplassen/
- https://www.datatilsynet.no/rettigheter-og-plikter/virksomhetenes-plikter/vurdere-personvernkonsekvenser/vurdering-av-personvernkonsekvenser/ og undersiden «nar-ma-man-gjennomfore-en-vurdering-av-personvernkonsekvenser/»

**Kunnskapsbasen**
- Bokføringsloven og -forskriften: lovtekst for kap. 3, 5 og 7, og oversiktsdokumenter.
- A-opplysningsloven 2026.
- «Lønn i praksis 2026».
- Feriepenger, OTP og sykepenger 2026.
- Utenlandske arbeidstakere og PAYE 2026.
- NS 4102.
- Aksjeloven §§ 8-7 til 8-11.
- Skatteforvaltningsforskriften kap. 7.

**Bare sett i søkeresultater, ikke åpnet:** nav.no/arbeidsgiver/medlemskap (A1), Sjøfartsdirektoratets FAQ om søknadsfrister og AFP-sats.
