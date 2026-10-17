# Plan for lønnssystemet

Denne mappen er planen for å bygge lønnssystemet som oppfyller lovkravene i `docs/`. Selve koden ligger i et eget repo: [hybriden/lonnssystem](https://github.com/hybriden/lonnssystem). Dette repoet holder bare kartleggingen, planen og historikken på planen.

Planen er laget av Claude Fable 5.1 den 17.10.2026 og vedlikeholdes her. Hver endring i planen logges i [LOGG.md](LOGG.md).

## Filene

| Fil | Innhold |
| --- | --- |
| [01-arkitektur.md](01-arkitektur.md) | Teknologivalg, pakkestruktur og de prinsippene som ikke skal brytes |
| [02-arbeidspakker.md](02-arbeidspakker.md) | Alle arbeidspakkene med fase, avhengigheter, kompleksitet og modell |
| [03-modelltildeling.md](03-modelltildeling.md) | Hvordan arbeid tildeles Haiku, Sonnet, Opus og Fable, og hvem som gjennomgår hva |
| [arbeidspakker/](arbeidspakker/) | Én fil per arbeidspakke, skrevet som et selvstendig oppdrag en modell kan få |
| [LOGG.md](LOGG.md) | Historikk på planen |

## Slik brukes planen

1. Finn neste arbeidspakke i [02-arbeidspakker.md](02-arbeidspakker.md). En pakke kan startes når alle pakkene den avhenger av har status «ferdig».
2. Start en Claude Code-økt i `lonnssystem`-repoet med modellen pakken er tildelt, og gi den pakkefilen som oppdrag. Pakkefilen peker på kildene i `docs/` og `research/` som skal leses først.
3. Når pakken er ferdig, gjennomgås den av modellen i kolonnen «Gjennomgås av». Gjennomgangen bruker `/code-review` eller en egen økt med pakkefilens akseptansekriterier som sjekkliste.
4. Oppdater status i pakkefilen og i tabellen, og skriv en linje i [LOGG.md](LOGG.md).

Pakkefilene er oppdrag, ikke fasit. Finner implementasjonen en feil i kartleggingen, rettes kartleggingen i `docs/` i samme omgang, og det noteres i pakkefilens «Åpne spørsmål».

## Status

| Status | Betydning |
| --- | --- |
| planlagt | Pakkefilen finnes, arbeidet er ikke startet |
| pågår | En økt arbeider med pakken |
| til gjennomgang | Implementasjonen er ferdig, gjennomgangen gjenstår |
| ferdig | Gjennomgått og slått sammen i `main` |

AP-000 til AP-008, AP-101 til AP-108, AP-201 til AP-203, AP-205, AP-208, AP-209, AP-211, AP-212, AP-401, AP-402, AP-407, AP-501, AP-602 og AP-701 er ferdige per 17.10.2026. AP-210 er til gjennomgang. Bølge 9 (AP-204, AP-206, AP-207, AP-502, AP-506, AP-507, AP-801) pågår. Resten har status «planlagt».
