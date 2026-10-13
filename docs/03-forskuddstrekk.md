# Forskuddstrekk

Arbeidsgiver skal hente skattekort før inntektsåret, holde det oppdatert før hver lønnskjøring og trekke etter det gjeldende kortet ([skattebetalingsloven §§ 5-1, 5-4](https://lovdata.no/lov/2005-06-17-67)). Uten skattekort trekkes 50 % av lønn (§ 5-5); pensjon uten kort trekkes 30 %.

**Skattekort**

- Hentes via Skatteetatens API (`bestillSkattekort` og `hentSkattekortbestillingSvar`). Fra 15.12.2026 virker bare polling ([Skatteetaten](https://www.skatteetaten.no/samarbeidspartnere/sluttbrukersystemer/sbs-nyheter/endret-bruksmonster-for-henting-av-skattekort/)).
- Opplysningene fra skattekortet kan ikke brukes til andre formål (§ 5-1 annet ledd).
- I januar uten nytt kort trekkes etter fjorårets kort; januartrekket korrigeres når nytt kort foreligger.
- Hovedarbeidsgiver bruker tabelltrekk. Biarbeidsgiver, eller ved tvil, bruker prosenttrekk ([skattebetalingsforskriften § 5-1-4](https://lovdata.no/dokument/SF/forskrift/2007-12-21-1766/KAPITTEL_5)). Tabelltrekk kan bare brukes hos én arbeidsgiver.
- Den ansatte kan be om høyere trekk (frivillig ekstra trekk).

**Tabell- eller prosenttrekk**

- Tabellene (fradragstabeller 8000–8400, tilleggstabeller 9010–9400) trekker over 10,5 måneder. Tabelltype velges etter lønnsperioden (sbf. § 5-10-2).
- Overtid og tillegg som betales sammen med vanlig lønn tabelltrekkes med lønnen. Bonus og ytelser for en annen periode prosenttrekkes.
- Grunnlaget rundes ned til hel krone (sbf. § 5-10-4).
- Arbeidsgiver kan la være å trekke når trekket ikke ventes å overstige 100 kr i måneden, eller ytelsene 500 kr i måneden (sbf. § 5-4-3).
- Pensjonsinnskudd og fagforeningskontingent som trekkes i lønn, trekkes fra i trekkgrunnlaget (§ 5-9).

| Periode | Tabell |
| --- | --- |
| Inntil 4 dager | Dagtabell |
| 5–10 dager | Uketabell |
| 11–17 dager | 14-dagerstabell |
| 18–24 dager | Uketabell på en tredjedel av lønnen, trekket × 3 |
| 25 dager til 1 måned og 3 dager | Månedstabell |

**Trekkfrie perioder** (§ 5-7, sbf. §§ 5-6-1, 5-7-1)

- Juni: feriepenger trekkfrie, eller én trekkfri månedslønn for den som har hatt lønn hele opptjeningsåret.
- «Halv skatt»: andre halvdel av november eller første halvdel av desember, valgt av arbeidsgiver. Timelønnede får to uker.
- Tillegg i fritaksperioden er bare trekkfrie opp til gjennomsnittsfortjenesten.
- Fritakene gjelder ikke kildeskatt på lønn, 50 %-trekk uten skattekort eller utleggstrekk.

**Naturalytelser** tas med i trekkgrunnlaget etter forskriftssatsene. Trekket tas bare så langt kontantlønnen rekker; mangler dekning, skal arbeidsgiver straks melde fra til skattekontoret (§ 5-10 tredje ledd).

**Frikort.** Beløpsgrensen er 100 000 kr i 2026, feriepenger medregnet. Når grensen er nådd og nytt kort ikke er hentet, trekkes 50 %.

**Kildeskatt på lønn (PAYE).** Utenlandske arbeidstakere på kortere opphold kan skattlegges med fast sats uten fradrag ([skatteloven kap. 20](https://lovdata.no/lov/1999-03-26-14/kap20)). Satsen gjelder i 12 måneder, også av feriepenger, uten trekkfrie perioder.

| PAYE 2026 | Sats |
| --- | --- |
| 17–69 år | 25 % |
| Under 17 eller over 69 år | 22,5 % |
| Ikke medlem av folketrygden | 17,4 % |
| Inntektstak | 725 050 kr; over taket skattlegges hele inntekten ordinært |

**Faste trekksatser 2026:** etterbetalt pensjon 32 %, etterbetalte folketrygdytelser som skattlegges som lønn 44 %, barnepensjon 17 % ([Skatteetaten, forskuddsutskrivingen 2026](https://www.skatteetaten.no/en/rettskilder/type/uttalelser/uttalelser/forskuddsutskrivingen-2026/)).

**Ansvar og straff.** Arbeidsgiver hæfter for trekk som ikke er foretatt eller betalt, med mindre det ikke skyldes forsømmelse (§ 16-20). Unnlatt trekk eller betaling kan straffes med inntil 2 års fengsel (§ 18-1). Skatteetaten kan kontrollere også lønnssystemet ved bokettersyn (§ 5-13).
