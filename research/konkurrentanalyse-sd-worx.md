# Konkurrentanalyse: SD Worx Lønn (Norge) mot lonnssystem

Skrevet 20.10.2026 for sak [hybriden/lonnssystem#2](https://github.com/hybriden/lonnssystem/issues/2). Kildene er merket **[M]** når de er SD Worx' egen markedsføring, **[U]** når de er uavhengige (Regnskap Norge, anmeldelsessider), og **[E]** når det er egen vurdering. Lest i denne økten; tallene gjelder høsten 2026.

## 1. Kort svar

SD Worx Lønn (tidligere Aditro Lønn) er den sterkeste lønnsmotoren i det norske markedet for virksomheter over 100 ansatte, regnskapsbyråer og offentlig sektor. Lønnsspesialistene gir den høyest totalscore i Regnskap Norges undersøkelse (5,4 av 6), men den samme undersøkelsen sier at systemet er ustabilt etter skyovergangen, tungt å implementere, lite intuitivt for folk uten lønnskompetanse, og har utilstrekkelig support, dokumentasjon, historikk og kontrollrapporter. SD Worx selger ikke til virksomheter under 100 ansatte selv, bare via partnere som outsourcing.

Vi dekker nesten hele den norske lovpliktige lønnskjeden i egen kode (a-melding, skattekort, NAV, bank, bokføring, personvern, særgrupper) og har tre ting SD Worx ikke har i Norge: en KI-assistent som kan jobbe i systemet (MCP med OAuth 2.1), innebygd avvikskontroll mot tidligere kjøringer, og et moderne, enkelt grensesnitt uten Citrix. Vi mangler det som gjør SD Worx til en plattform: HR-system, tid og skiftplan, byråportaler med kundegodkjenning, rapportgenerator, tariff- og regulativstyring, mobilapp, og sertifiseringene (ISO 27001, ISAE 3402) et byrå spør etter.

## 2. Hva SD Worx er

| | |
| --- | --- |
| Eier | SD Worx (Belgia). Kjøpte Aditro i 2021; Aditro Lønn og Aditro HR ble SD Worx Lønn og SD Worx HR, bare navnet ble endret [M]. |
| Volum i Norge | Ca. 450 000 til 480 000 lønnsslipper per måned [M]. Aditro hadde 34 % markedsandel i Norge i 2020 [U, Enterprise Times]. |
| Posisjon | Nest mest brukte system blant lønnsspesialister (103 av 298 respondenter), etter Visma.net Payroll (106) [U, Regnskap Norge]. |
| Målgrupper | «Mellomstore og store selskaper», regnskapsbyråer, offentlig sektor, internasjonale virksomheter. Egne løsninger «passer best for selskaper med over 100 ansatte»; under 100 henvises til sertifiserte partnere [M]. |
| Produkter | Lønn: Lønnssystem, Outsourcing lønn, Lønnssystem for Regnskapsbyrå (SD Worx Byrå), Lønnssystem for Offentlig sektor, Internasjonal lønn, Lønnsintegrasjoner. HR: SD Worx HR (masterdata og operativ HR, talent management og rekruttering), HRM for offentlig sektor, internasjonalt HR-system. Tid: Timeregistrering basic og advanced, Adgangskontroll, Oppgavestyring, Personalplanlegging. SAP: SuccessFactors HRM, SAP Lønn, Workforce Management. Tjenester: Outsourcing, konsulenter, revisjonsrapport, Service Desk. SD Worx Spend (reise og utlegg) [M]. |
| Pris | Ingen priser publisert; bare «Book demo». I Regnskap Norges prisrangering ligger SD Worx blant de dyreste og utenfor Pareto-fronten [U]. |
| Sertifiseringer | ISO 27001, ISO 27701, ISO 14001, ISAE 3402 type II (outsourcing), ISAE 3000. Servere i Europa/Norden [M]. |
| Support | Kundeportal for autoriserte lønnsbrukere (saker, artikler, bestilling av konsulent). Ansatte henvises til egen arbeidsgiver. Ingen åpningstider eller SLA publisert [M]. |
| KI | Konsernet lanserte «Legal Watch» (regelverksovervåking) i Tyskland, Sverige, Nederland og Spania i juni 2026, og «agentic AI» for egne lønnskonsulenter i Belgia med utvidelse til Nederland og Finland. Ingenting for Norge, og ingenting kunden selv kan bruke [M, pressemeldinger]. |

## 3. Hva de dekker som vi ikke dekker

Vurdert mot planen (AP-000 til AP-907 og AP-1001 til AP-1003 er ferdige) [E].

| Område | SD Worx | Oss | Verdt å tette? |
| --- | --- | --- | --- |
| HR-system (masterdata, onboarding, talent, rekruttering, medarbeidersamtaler) | Eget produkt, integrert med lønn | Ansattregister, arbeidsforhold, arbeidsavtale. Ikke HR-prosesser | Nei. HR er et eget marked (Simployer, Personio). Integrasjon er riktig svar. |
| Tid: skiftplanlegging, personalplanlegging, adgangskontroll, oppgavestyring | Egne produkter (WFM) | Timeregister med overtid og arbeidstidskontroll (AP-211) | Nei for skift og adgang. Import fra tidssystemer finnes alt (MCP `importer_timer`). |
| Byråplattform: fire portaler (ansatt, kunde, leder, byrå), kunden leverer og godkjenner lønnsgrunnlag selv, sikker meldingsutveksling, kjøre- og periodeplaner på tvers av kunder | Ja, «Administrer lønn for flere firmaer» | Flerkunde (én bruker, flere arbeidsgivere), ansattportal. Ingen kundeportal med godkjenning, ingen tverrkunde-plan | **Ja.** Byråene er den kanalen SD Worx vokser i (Azets, Aider, Amesto, View, XACCT, BDO/Enora). Minste versjon: kunden godkjenner lønnsgrunnlaget før kjøring, og en liste over alle kunders kjøringer med status og frist. |
| Rapportgenerator og importmaler laget av brukeren | «rikt rapporteringsunivers hvor det er enkelt å lage egne rapporter og definere importmaler» [U] | Faste rapporter, dimensjonsrapport med filter på lønnsart og dimensjoner, CSV | **Delvis.** Lagrede rapportoppsett og Excel-eksport er billig å bygge på det vi har. Fri rapportgenerator er dyrt og kan erstattes av MCP (assistenten lager rapporten). |
| Tariffavtaler og regulativer: lønnstabeller, lønnstrinn, automatisk regulering, «kontraktskonstanter, matriser, formler» | Sterk, og det er derfor store virksomheter velger dem | Allmenngjorte minstesatser og kontroll (AP-108), statens lønnstrinn finnes ikke | **Ja, på sikt.** Lønnstrinntabeller per avtale med virkningsdato og massregulering er en M-pakke og åpner offentlig sektor og tariffbundne private. |
| Fraværsmodul med selvbetjening i app | Får «spesielt gode skussmål» [U] | Fraværsregister, arbeidsgiverperiode, sykepengegrunnlag, inntektsmelding, omsorg, foreldrepenger, permittering, kvartalsstatistikk | Nei på regler. **Ja** på selvbetjening: ansatt melder fravær selv, leder godkjenner. |
| Mobilapp for ansatte (lønnsslipp, fravær, reise) | Ja | Ansattportal i nettleser, responsiv | Delvis. PWA med installasjon er nok; ingen app-butikk. |
| Reise og utlegg som egen app (SD Worx Spend) | Ja | Reiseregning i domenet (AP-209), registrering i portalen | Nei nå. |
| Internasjonal lønn, SAP-integrasjon | Ja | Nei | Nei. |
| Outsourcing, konsulenter, service desk | Ja, med ISAE 3402 | Nei, vi er programvare | Nei. Partnere kan tilby det på vår plattform. |
| Sertifiseringer (ISO 27001, ISO 27701, ISAE 3402) | Ja | Trusselmodell og sikkerhetsgjennomgang (AP-902), ingen sertifisering | **Ja før byråsalg**, men det er organisasjon og revisjon, ikke kode. |
| Standardintegrasjoner mot «de største ERP-systemene», Workday, SuccessFactors, Oracle | Ja | Kontering og regnskapseksport (NS 4102, SAF-T), import av ansatte, timer og lønnsgrunnlag via fil og MCP | Delvis. Direkte bilagsoverføring til PowerOffice, Tripletex og Xledger er det byråene spør om. |
| Dokumentasjon av oppsett og brukerhjelp | Finnes, men brukerne kaller den «klart utilstrekkelig» [U] | Invariantdokumenter og forklaring i beregningsresultatet, ingen brukerhjelp i grensesnittet | Ja, billig: hjelpetekst per side, og assistenten via MCP som svarer på «hvorfor ble trekket slik». |

## 4. Hva vi gjør som de ikke gjør

| Vi | SD Worx |
| --- | --- |
| **KI-assistent som arbeider i systemet.** MCP-server med OAuth 2.1 (registrering, samtykke, PKCE), 19 verktøy: import av ansatte, timer og lønnsgrunnlag, opprette og beregne kjøring, avvik, dimensjoner, rapporter. Assistenten jobber med brukerens rettigheter og tofaktor. | KI brukes av SD Worx' egne konsulenter i Belgia. Ingen kundevendt assistent i Norge. Regnskap Norges respondenter ønsker nettopp «AI som kontrollfunksjon, særlig innen lønn og reiseregninger» [U]. |
| **Avvikskontroll innebygd.** Hver ordinær beregning sammenlignes med de tre siste godkjente kjøringene (ny og manglende ansatt, brutto, netto, trekk, lønnsart som forsvinner eller dukker opp) med varsler som må kvitteres før godkjenning. | Brukerne sier «kontrollrapporter» og «oppretting av historikk» er mangelfulle, og at systemet er «for åpent og sårbart for brukerfeil» [U]. |
| **Enkelt og stabilt.** Ett moderne nettgrensesnitt, ingen Citrix, dark mode, tilgjengelighetstestet (axe), arbeidsflyt gruppert etter måneden (Grunnlag, Måneden, Oppfølging). | «Komplekst, tungt å implementere og lite intuitivt for sluttbrukere uten lønnskompetanse», «Citrix-løsningen skaper fortsatt frustrasjon», «ustabilitet etter overgangen til skybaserte løsninger» [U]. |
| **Sporbar beregning.** Forklaring per linje i resultatet, invarianter som dokumenterte regler, Gullår-fasit over et helt år, periodelås, reversering med kontrollspor. | Lukket motor. Brukere beskriver at «sammenhengene mellom styringselementene» er vanskelige å forstå [U, businesswith]. |
| **Lønnskartlegging etter kjønn (likestillingsloven § 26) innebygd.** | SD Worx' «Pay Equity»-modul finnes bare i Belgia (Spania og Romania under utvikling) [M]. |
| **Små og mellomstore virksomheter.** Ingen nedre grense, selvbetjent oppstart med orgnr fra Enhetsregisteret. | Under 100 ansatte henvises til partner for outsourcing. |
| **Personvern som funksjon.** Sletteløp med regler per tabell, innsyn, tilgangslogg, begrunnelse ved avmaskering, data i Norway East. | Sertifisert, men ingenting tilsvarende synlig for kunden. Globalt klages det på innlogging og passord i portalen (Trustpilot 2,0 av 5, 174 anmeldelser, mest britiske) [U]. |
| **Dynamiske dimensjoner** på ansatt, i kjøring og rapport, med flerutvalg som i Excel. | Kostnadssteder finnes, men ikke beskrevet som fritt definerbare. |
| **Hele den norske kjeden i én kode:** Maskinporten, skattekort via API, a-melding v2.3 med erstatning og tilbakemelding, inntektsmelding til NAV, samordnet utleggstrekk, betalingsoppdrag med KID, ISO 20022 bankfil, SAF-T, sammenstillingsoppgave, årsskifte. | Tilsvarende dekning, men over flere produkter og delvis via tjenester. |
| **Åpen pris mulig.** | Pris bare på forespørsel, oppfattet som dyr [U]. |

## 5. Styrker

1. **Lønnsmotoren.** «Sterk og avansert lønnsmotor», «konfigurering uten behov for spesialtilpasninger», «mange tariffavtaler og avanserte regulativer» [U]. Det er dette som holder store kunder.
2. **Byråkanalen.** Azets, Aider, Amesto AccountHouse, VIEW, XACCT, Enora (tidligere BDO) har standardisert på SD Worx for store kunder. Lønnsvolumet på byråplattformen er «mer enn tidoblet» [M].
3. **Brukertilfredshet hos spesialister.** 5,4 av 6 totalt, 5,1 på sluttbrukerfunksjoner, to år på rad øverst [U]. Konfidensintervallet overlapper trolig PowerOffice GO (5,1).
4. **Fullt økosystem.** Lønn, HR, tid, reise, outsourcing og SAP fra én leverandør, med ISO/ISAE-sertifiseringer som et innkjøp i offentlig sektor krever.
5. **Lokal kompetanse og skala.** Norsk support, lønnsspesialister, 450 000 lønnsslipper i måneden.

## 6. Hva kundene liker

Fra Regnskap Norge og Lønnslaget, «Lønnssystemer 2025» (298 respondenter, lansert 4.12.2025, publisert 17.3.2026) [U]:

- Fleksibelt og fremtidsrettet, høy grad av automatisering og effektiv prosesstøtte.
- Sterk og avansert lønnsmotor; konfigurering uten spesialtilpasninger.
- Rikt rapporteringsunivers; enkelt å lage egne rapporter og importmaler.
- Brukervennlig, intuitivt og kraftig for større virksomheter med komplekse behov.
- Fraværsmodulen får spesielt gode skussmål.
- «Det beste eller mest komplette lønnssystemet i markedet når det fungerer slik det skal.»

Fra businesswith.no (11 anmeldelser, 4,48 av 5, mest svenske storkunder) [U]: mye kan konfigureres selv, gode hjelpetekster og support, fleksibilitet; én kunde gikk fra to til én lønnsmedarbeider for 800 ansatte.

Fra byråene (SD Worx' egne kundehistorier) [M]: sparer tid, system laget for lønn, automatisering med høy datakvalitet, gjør byrået attraktivt som arbeidsgiver.

## 7. Hva kundene ikke liker

Regnskap Norge [U]:

- **Stabilitet**: «betydelige utfordringer knyttet til stabilitet, spesielt etter overgangen til skybaserte løsninger, der hyppige endringer og ustabilitet skaper usikkerhet».
- **Kompleksitet**: «komplekst, tungt å implementere og lite intuitivt for sluttbrukere uten lønnskompetanse».
- **Support og dokumentasjon**: «feilretting, support og brukerdokumentasjon beskrives som klart utilstrekkelig».
- **Citrix**: «skaper fortsatt frustrasjon, særlig ved import og oppdateringer for flere selskaper».
- **For åpent**: fleksibiliteten gjør systemet «sårbart for brukerfeil».
- **Mangler**: «oppretting av historikk og kontrollrapporter» er mangelfulle.

businesswith.no [U]: sammenhengen mellom kontraktskonstanter, matriser, formler og behandlingsregler er vanskelig å forstå; systemet tar tid å lære.

Capterra og Software Advice (2 til 4 anmeldelser, internasjonalt) [U]: hyppige innloggingssteg, avhengig av SD Worx' folk for tilpasninger, manglende varsel ved skattekortendring, enkelte feilberegninger.

Trustpilot (sdworx.com, 2,0 av 5, 174 anmeldelser, 79 % énstjerne, mest Storbritannia) [U]: innlogging og passordnullstilling i ansattportalen, økter som løper ut, treg support, betaling for supportsaker. Gjelder det globale selskapet, ikke dokumentert for norske kunder.

## 8. Finnes det andre produkter som er like gode?

Regnskap Norges totalscore (1 til 6) og antall brukere blant respondentene [U]:

| System | Score | Sluttbruker | Brukere | Segment og dom fra spesialistene |
| --- | --- | --- | --- | --- |
| SD Worx | 5,4 | 5,1 | 103 | Store og byrå. Best motor, dårligst stabilitet og læringskurve. |
| PowerOffice GO | 5,1 | 5,2 | 72 | Små og enkle. «Best som regnskapssystem med en enkel lønnsmodul»; feil i feriepenger og manglende forskuddstrekk i kombinerte kjøringer nevnes. 195 kr/mnd + 35 kr per lønnsmottaker. På Pareto-fronten. |
| Tripletex | 4,9 | 4,6 | 76 | Små. «Lettvekter» med manuell registrering, ingen fullverdig fraværsmodul, bare én import per kjøring, dyr for funksjonaliteten. |
| Duett | 4,8 | 4,7 | 20 | Byrå. På Pareto-fronten. |
| Visma.net Payroll | 4,6 | 4,5 | 106 | Mest brukt. Ren lønnsmotor, god support, men «rigid», datostyrte regler gjør korrigering og retro «komplisert og feilsensitiv», svak regnskapsintegrasjon, svak HRM. |
| Finago (24SevenOffice) | 4,6 | 4,6 | 31 | Byrå. Nytt i 2025 med «grunnleggende feil» i skattetrekk og feriepenger 60+. På Pareto-fronten. |
| Xledger | 4,5 | 4,4 | 46 | Konsern/ERP. Lønnsmodulen «tungvint, svært manuell», mangler automasjon mot Altinn. |
| Unimicro | 4,4 | | 14 | Pareto-fronten. |
| Unit4 / Agresso | 4,2 | 3,9 | 18 | Offentlig. |
| SAP | 3,9 | 3,6 | 13 | Store konsern, via Zalaris m.fl. |
| Visma Enterprise HRM | 3,4 | 3,3 | 14 | Offentlig. |
| Nettlønn | 2,9 | 2,8 | 20 | Små. |

Ingen leverandør kombinerer SD Worx' motor med PowerOffices enkelhet; det er hullet. Huldt & Lillevik er under avvikling hos Visma og kundene migreres til Visma.net Payroll. Internasjonale plattformer (Deel, Remote, Rippling, Personio) tilbyr Norge som EOR eller via partnere, ikke som eget norsk lønnssystem; Personio har ingen norsk a-melding.

Pris til sammenligning [U]: PowerOffice 195 kr + 35 kr per lønnsmottaker per måned; Tripletex lønn ca. 65 kr per ansatt per måned på toppen av pakke; Visma Payroll Start/Pluss/Smart 63/74/110 per ansatt per måned pluss implementering hos partner; 24SevenOffice ca. 30 kr per lønnsslipp. SD Worx: ikke publisert.

## 9. Hva det betyr for oss

**Posisjon** [E]: «Lønnsmotoren byråene stoler på, med enkelheten små kunder trenger, og den eneste med en KI-assistent som faktisk jobber i systemet.» Primærsegment: regnskapsbyråer og virksomheter med 10 til 250 ansatte, der SD Worx ikke selger selv og PowerOffice/Tripletex blir for enkle. Sekundært: tariffbundne mellomstore virksomheter når lønnstrinn er på plass.

**Hva vi bør gjøre (prioritert, minste versjon først)** [E]:

| Nr. | Forslag | Hvorfor | Størrelse |
| --- | --- | --- | --- |
| 1 | **Byråoversikt og kundegodkjenning**: liste over alle arbeidsgivere med kjøringens status, frist og avvik; kunden godkjenner lønnsgrunnlaget (fra MCP-import eller fil) før byrået kjører. | Byrå er SD Worx' vekstkanal, og «tverrkunde-plan» er det de selger. Bygger på flerkunde og avvikskontroll. | M |
| 2 | **Lagrede rapportoppsett og Excel-eksport** på dimensjonsrapporten og kjøringsrapportene. | Dekker «egne rapporter» for de fleste uten rapportgenerator. CSV finnes; xlsx er en liten pakke. | S |
| 3 | **Selvbetjent fravær og reise i ansattportalen** med godkjenning av leder. | SD Worx' fraværsmodul er det kundene roser mest; vi har reglene men ikke flyten. | M |
| 4 | **Lønnstrinn og regulativ**: tabeller per avtale med virkningsdato, massregulering med etterbetaling. | Åpner tariffbundne og offentlige kunder, SD Worx' kjernestyrke. Reversering og periodelås finnes alt. | M |
| 5 | **Hjelp i grensesnittet**: kort hjelpetekst per side, lenke til forklaringen i beregningen, og assistenten som svarer «hvorfor». | SD Worx' svakeste punkt; nesten gratis for oss. | S |
| 6 | **Regnskapsintegrasjon direkte** mot PowerOffice GO, Tripletex og Xledger (bilag og betaling), ikke bare fil. | «To av tre bruker samme leverandør for lønn og regnskap» [U]; vi må inn i deres regnskap. | M per system |
| 7 | **PWA for ansattportalen** (installerbar, push ved ny lønnsslipp via varsling fra AP-907). | «Mobilapp» på sjekklisten uten app-butikk. | S |
| 8 | **ISO 27001 / ISAE 3402** (organisasjon, ikke kode). | Byråer og offentlige innkjøp krever det. | Utenfor kode |

**Hva vi ikke bør jage** [E]: HR-system, skiftplan, adgangskontroll, internasjonal lønn, SAP, outsourcing. Integrer heller: ansatte og timer inn (finnes), bilag ut (nr. 6).

**Hva vi bør si høyt** [E]: avvikskontroll og KI-assistent svarer direkte på det lønnsspesialistene ba om i undersøkelsen («AI som kontrollfunksjon»); stabilitet, enkelhet og dokumentasjon svarer på det SD Worx-kundene klager på.

## 10. Forbehold

- SD Worx publiserer ingen funksjonsliste for Norge; produktsidene er overskrifter. Funksjonsdetaljene er fra businesswith.no, Regnskap Norge og byråenes kundehistorier.
- Regnskap Norge oppgir ikke antall svar bak hver score, bare antall brukere per system (en person kan bruke flere). Konfidensintervallene står i figuren, ikke i tekst; avstanden fra 5,4 til 5,1 er trolig ikke signifikant.
- Trustpilot-klagene gjelder konsernets ansattportal i Storbritannia og Belgia, ikke dokumentert for Norge.
- Priser for konkurrentene er fra leverandørsider og tredjepartsblogger og spriker; sjekk før de brukes i salg.
- Ingen kunder er intervjuet. Neste steg hvis dette skal brukes i salg: tre samtaler med byråer som bruker SD Worx for store kunder og noe annet for små.

## Kilder

- SD Worx Norge: forside, [Lønn](https://www.sdworx.no/nb-no/vare-losninger/lonn), [Lønnssystem for regnskapsbyrå](https://www.sdworx.no/nb-no/vare-losninger/lonn/lonnssystem-regnskapsbyra), [HR-system](https://www.sdworx.no/nb-no/vare-losninger/hr-system), [Workforce management](https://www.sdworx.no/nb-no/vare-losninger/workforce-management), [Trygg lønn for mindre virksomheter](https://www.sdworx.no/nb-no/trygg-lonn-mindre-virksomheter), [Lønnsintegrasjoner](https://www.sdworx.no/nb-no/vare-losninger/lonn/lonnsintegrasjoner), [Support](https://www.sdworx.no/nb-no/support), [Best i test](https://www.sdworx.no/nb-no/lonnssystem-best-i-test-pa-brukertilfredshet), [Byråenes erfaringer](https://read.sdworx.com/nb-no/byraguidedigitalendring/byrenes-erfaringer), [Aditro blir SD Worx](https://www.sdworx.no/nb-no/inspirasjon/hr-teknologi-ai/aditro-blir-sd-worx).
- SD Worx konsern: [Agentic AI i lønn, 24.6.2026](https://www.sdworx.com/en-en/about-sd-worx/press/2026-06-24-sd-worx-introduces-agentic-ai-payroll-enhance-customer-engagement), [Q2 2026 Innovation & Tech](https://www.sdworx.com/en-en/sd-worx-quarterly-updates-q2-2026/innovation-and-tech).
- Regnskap Norge og Lønnslaget: [Slik vurderer lønnsspesialister de mest brukte systemene](https://www.regnskapnorge.no/faget/artikler/teknologi2/slik-vurderer-lonnsspesialister-de-mest-brukte-systemene/) med rapporten [Lønnssystemer 2025 (PDF)](https://www.regnskapnorge.no/contentassets/b173a1e31cd741af9b610fc80db70ddf/lonnssystemer---resultater-til-publisering.pdf); [Teknologiundersøkelsen 2025](https://kommunikasjon.ntb.no/pressemelding/18777857/teknologiundersokelsen-2025-disse-systemene-er-best-pa-pris-og-fornoydhet?publisherId=89513&lang=no).
- Anmeldelser: [businesswith.no, SD Worx Lønn](https://businesswith.no/system/sd-worx-lon/), [Capterra](https://www.capterra.com/p/187453/SD-Worx-Payroll/), [Software Advice](https://www.softwareadvice.com/psa/sd-worx-payroll-profile/), [Trustpilot](https://www.trustpilot.com/review/sdworx.com).
- Marked: [Enterprise Times om Aditro-oppkjøpet](https://www.enterprisetimes.co.uk/2021/04/29/sd-worx-powers-into-nordics-with-aditro-acquisition/), [VIEW Group om Aditro lønn](https://viewgroup.no/lonnstjenester/aditro-lonn/).
- Konkurrenter: [PowerOffice lønnssystem](https://www.poweroffice.no/lonnssystem), [Visma Payroll pakker og priser](https://www.vismasoftware.no/lonn-hr/pakker-priser), [Tripletex priser](https://www.tripletex.no/priser/), [Xledger lønn](https://xledger.com/no/erp-system/lonn-reise/), [24SevenOffice 24Payroll](https://24sevenoffice.com/no/nyheter/vi-presenterer-24payroll), [Simployer og Visma.net Payroll](https://www.simployer.com/no/artikler/simployer-plus-vismanet-payroll-sant), [Conta om Huldt & Lillevik](https://conta.no/oppdateringer/huldt-og-lillevik-legges-ned/).
