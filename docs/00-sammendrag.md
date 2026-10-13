# Sammendrag

Et norsk lønnssystem må beregne lønn, trekk, feriepenger, arbeidsgiveravgift og pensjon riktig, rapportere alt månedlig i a-meldingen, betale trekk innen første virkedag etter utbetaling, og dokumentere og oppbevare grunnlaget i 5 år. Reglene er spredt på minst 15 lover og endres hvert år. Dokumentet gjelder inntektsåret 2026, med vedtatte og foreslåtte endringer for 2027.

**Endringer i 2026 som eldre systemer ofte mangler**

- Skattetrekkskonto og bankgaranti er avviklet. Forskuddstrekk og utleggstrekk forfaller første virkedag etter hver utbetaling.
- A-meldingen krever «sum forskuddstrekk per lønnsutbetalingsdato», og regel F527 avviser utbetalingsdatoer utenfor perioden.
- Samordnet utleggstrekk etter innkrevingsloven, med eget trekkpålegg, egen KID per ansatt og API.
- Altinn II er stengt. Alt går via API med Maskinporten og systembruker; fra januar 2027 kreves tilgangspakker.
- Inntektsmelding for sykepenger kan bare sendes fra lønnssystem via NAVs nye API.
- Lønnsdokumentasjonen i bokføringsforskriften § 5-6 er endret fra 1.1.2026.

**Største fallgruver**

- Feil klassifisering av lønnsarter (trekkpliktig, AGA-pliktig, feriepengegrunnlag) gir feil i alt som følger.
- AGA-sone per underenhet, fribeløp i sone Ia og regler for ambulerende arbeid og hjemmekontor.
- Trekk i lønn uten hjemmel i arbeidsmiljøloven § 14-15.
- Korrigeringer: erstatningsmelding mot tilleggsmelding, feil mot etterbetaling, netto mot brutto tilbakebetaling.
- Oppbevaring og sletting som må balansere bokføringsloven mot GDPR.

Punkter merket «Åpent spørsmål» er ikke bekreftet i primærkilde og må kontrolleres før implementering.
