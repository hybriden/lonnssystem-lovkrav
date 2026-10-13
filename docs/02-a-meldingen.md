# A-meldingen

A-meldingen leveres minst én gang i måneden, senest den 5. i måneden etter utbetaling, for hver inntektsmottaker ([a-opplysningsloven §§ 3–4](https://lovdata.no/lov/2012-06-22-43), [a-opplysningsforskriften § 2-1](https://lovdata.no/dokument/SF/forskrift/2014-06-24-857)). Utbetalingsdatoen styrer rapporteringen, ikke opptjeningen (kontantprinsippet). Etterbetaling rapporteres i utbetalingsmåneden.

**Frister 2026.** Faller den 5. på helg eller helligdag, flyttes fristen til neste virkedag. Skatteetaten gir ikke utsatt frist.

| Periode | Frist |
| --- | --- |
| Januar | 5.2.2026 |
| Februar | 5.3.2026 |
| Mars | 7.4.2026 (påske) |
| April | 5.5.2026 |
| Mai | 5.6.2026 |
| Juni | 6.7.2026 |
| Juli | 5.8.2026 |
| August | 7.9.2026 |
| September | 5.10.2026 |
| Oktober | 5.11.2026 |
| November | 7.12.2026 |
| Desember | 5.1.2027 |

**Innhold** ([Skatteetatens veiledning](https://www.skatteetaten.no/bedrift-og-organisasjon/arbeidsgiver/a-meldingen/veiledning/), meldingsformat v2.3)

| Del | Felter systemet må ha |
| --- | --- |
| Melding | Opplysningspliktig (org.nr.), meldingsID, kalendermåned, eventuell meldingsID som erstattes |
| Inntektsmottaker | Fødselsnummer eller D-nummer; ellers navn, fødselsdato, utenlandsk ID og utstederland |
| Arbeidsforhold | Type (ordinært, maritimt, frilanser, pensjon), arbeidsforholdsID, start- og sluttdato, sluttårsak (6 verdier) |
| Stilling | Stillingsprosent med siste endringsdato, siste lønnsendringsdato, timer per uke for full stilling, arbeidstidsordning (må stemme med timetallet) |
| Klassifisering | Ansettelsesform (fast, midlertidig, utleid, tilkallingsvikar), 7-sifret yrkeskode fra SSB (0000 000 og 9999 999 avvises) |
| Permisjon og permittering | Egen ID, start, slutt, prosent og beskrivelse; permisjon over 14 dager rapporteres |
| Pensjon | Org.nr. til OTP-leverandøren for private arbeidsgivere |
| Inntekt | Fordel (kontant, natural, utgiftsgodtgjørelse), beskrivelse fra kodelisten, trekkpliktig ja/nei, AGA-pliktig ja/nei, antall timer, tilleggsinformasjon |
| Forskuddstrekk | Negativt beløp per mottaker; nytt fra 2026: sum forskuddstrekk per lønnsutbetalingsdato |
| Utleggstrekk | «utleggstrekkSamordnet» (med dato) eller «utleggstrekkSkatt», negativt beløp |
| AGA og finansskatt | Per underenhet: sone, beregningskode, grunnlag (lønn, pensjonstilskudd, NAV-refusjon som negativt grunnlag), beregnet avgift |

Sykefravær under 12 måneder rapporteres ikke i a-meldingen; det går til NAV via inntektsmeldingen.

**Kontroller som systemet må håndtere**

- Regel F527 (fra januar 2026): utbetalingsdatoen må ligge i perioden det rapporteres for. Summen av trekk per dato må være lik trekkene i meldingen og aldri negativ ([Skatteetaten](https://www.skatteetaten.no/en/our-partners/end-user-systems/sbs-nyheter/sum-forskuddstrekk-per-lonnsutbetalingsdato--presiseringer/)).
- Tilbakemeldingen (A03) har tre nivåer: avvisning (regnes som ikke levert), øyeblikkelig (rettes innen fristen) og retningslinje. Den gir også beløp, kontonummer og KID. Ny melding skal ikke sendes før tilbakemeldingen er mottatt.

**Korrigering**

- Erstatningsmelding: viser til meldingsID-en den erstatter og må inneholde alle opplysningene for måneden. En melding kan bare erstattes én gang.
- Tilleggsmelding: egen meldingsID med bare differansene.
- Feil rettes i måneden feilen gjaldt; feil beskrivelse rettes med negativt beløp og ny rapportering.
- Tilbakebetalt lønn: netto (brutto og trekk) før 31.1 året etter, bare brutto etter 31.1 ([Skatteetaten](https://www.skatteetaten.no/bedrift-og-organisasjon/arbeidsgiver/a-meldingen/veiledning/lonn-og-ytelser/rette-feil-i-lonn-og-andre-ytelser/)).
- Uten ansatte skal arbeidsforholdene få sluttdato. En tom melding skal ikke brukes som «ingen ansatte»; den erstatter forrige melding og kan gi feil hos NAV.

**Sanksjoner** (rettsgebyr R = 1 345 kr i 2026)

| Reaksjon | Sats | Maksimum |
| --- | --- | --- |
| Tvangsmulkt (§ 10) | 1/10 R per dag per inntektsmottaker med manglende eller feil opplysninger | 1 345 000 kr per periode |
| Overtredelsesgebyr (§ 11) | ¼ R per dag fra dagen etter fristen | 20 175 kr |

**Teknisk overgang.** Altinn II ble stengt i juni 2026. A-melding sendes nå via Skatteetatens API med Maskinporten og systembruker ([Skatteetaten](https://www.skatteetaten.no/samarbeidspartnere/reetablering-altinn/systemleverandor/)). Altinn-rollene opphører 31.12.2026; fra januar 2027 kreves tilgangspakker. Systemet bør også kunne eksportere a-meldingen som XML for manuell opplasting.

Åpent spørsmål: om a-melding kan leveres inntil to måneder fram i tid, er ikke bekreftet på skatteetaten.no.
