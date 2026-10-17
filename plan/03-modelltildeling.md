# Modelltildeling

Arbeidet tildeles den billigste modellen som løser pakken riktig på første forsøk. Kompleksitetsklassen bestemmer både hvem som implementerer og hvem som gjennomgår. Gjennomgangen gjøres alltid av en modell minst én klasse over implementeringsmodellen, i en egen økt uten implementeringens kontekst.

## Klassene

| Klasse | Kjennetegn | Implementeres av | Gjennomgås av |
| --- | --- | --- | --- |
| K1 Rutine | Spesifikasjonen er fullstendig i kildene. Data, tabeller, kodelister, parsere for kjente formater, dokumentasjon fra eksisterende kode. Lite rom for tolkning. | Haiku 5.5 | Sonnet 5.5 |
| K2 Standard | Avgrenset funksjon med gitte regler og formler. CRUD med validering, klienter mot dokumenterte API-er, brukerflate, beregninger der formelen står i kartleggingen. | Sonnet 5.5 | Opus 5.5 |
| K3 Kompleks | Mange regler som virker sammen, tilstandsmaskiner, korrigeringslogikk, protokoller med autentisering, eller feil som gir sanksjoner eller feil utbetaling. | Opus 5.5 | Fable 5.1 |
| K4 Kritisk | Domenemodell, invarianter, sikkerhet, personvern, avgjørelser som alle senere pakker bygger på. | Fable 5.1 | Fable 5.1 i ny økt, og et menneske |

## Hvorfor denne fordelingen

- Feil i K3 og K4 oppdages sent og koster mest: tvangsmulkt på 1/10 rettsgebyr per dag per inntektsmottaker, feil trekk som arbeidsgiver hefter for, eller en datamodell som må skrives om. Der er det billigere å bruke den sterkeste modellen med én gang.
- K1-pakkene er store i volum men små i tolkning. Haiku holder kostnaden nede, og Sonnet-gjennomgangen fanger slurv.
- Gjennomgang en klasse over gir et par øyne som ikke har gjort de samme antakelsene som implementeringen.

## Tildelingen i tall

| Klasse | Antall pakker | Implementeres av |
| --- | --- | --- |
| K1 | 6 | Haiku 5.5 |
| K2 | 36 | Sonnet 5.5 |
| K3 | 22 | Opus 5.5 |
| K4 | 4 | Fable 5.1 |

Hele listen står i [02-arbeidspakker.md](02-arbeidspakker.md).

## Regler for øktene

1. Økten får pakkefilen, `CLAUDE.md` i koderepoet og kildene pakkefilen peker på. Ikke mer.
2. Implementeringen starter med testene for akseptansekriteriene, og de skal feile før koden skrives.
3. Økten endrer bare filer innenfor pakkens omfang. Trengs en endring utenfor, stopper den og noterer det i pakkefilen under «Åpne spørsmål».
4. En K1- eller K2-økt som møter en regel som ikke står i kildene, stopper og eskalerer til neste klasse i stedet for å gjette.
5. Gjennomgangen bruker akseptansekriteriene som sjekkliste og leser den tilkoblede koden, ikke bare diffen.
6. Ingen pakke er ferdig før lint, build og alle tester er grønne, og gullåret (AP-901) fortsatt er grønt når det finnes.

## Modell-ID-er

| Navn | Modell-ID |
| --- | --- |
| Haiku 5.5 | `claude-haiku-5-5` |
| Sonnet 5.5 | `claude-sonnet-5-5` |
| Opus 5.5 | `claude-opus-5-5` |
| Fable 5.1 | `claude-fable-5-1` |
