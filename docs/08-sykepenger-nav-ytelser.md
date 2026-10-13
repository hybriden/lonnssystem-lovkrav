# Sykepenger og NAV-ytelser

Arbeidsgiver betaler sykepenger de første 16 kalenderdagene (arbeidsgiverperioden) og kan deretter forskuttere lønn mot refusjon fra NAV opp til 6G ([folketrygdloven kap. 8](https://lovdata.no/lov/1997-02-28-19)). Refusjon kreves gjennom inntektsmeldingen, som fra lønnssystem bare kan sendes via NAVs API for sykepenger.

**Arbeidsgiverperioden**

- Gjelder etter minst 4 ukers ansettelse (§ 8-18). Perioden regnes fra første hele fraværsdag, og fridager teller med i de 16 dagene (§ 8-19).
- Nytt fravær innen 16 dager etter at den ansatte er tilbake, regnes inn i samme periode. En ny periode starter først etter minst 16 dager i arbeid.
- Grunnlaget er gjennomsnittet av inntekt rapportert i a-meldingen de 3 siste kalendermånedene (§ 8-28). Avviker årsinntekten mer enn 25 %, fastsettes den ved skjønn (§ 8-30).
- Egenmelding: inntil 3 kalenderdager hver gang, etter minst 2 måneders ansettelse (§§ 8-23 til 8-27). Arbeidsgiver kan utvide dette og kan frata retten etter minst 4 fravær uten legeerklæring på 12 måneder.
- Ved kronisk sykdom eller svangerskapsrelatert sykdom kan NAV dekke arbeidsgiverperioden etter vedtak (§ 8-20). Vedtaket følger den ansatte.

**Etter arbeidsgiverperioden**

- Refusjonen er begrenset til 6G (819 294 kr), med dagsats 1/260 av årsgrunnlaget, og gis for inntil 248 dager (§§ 8-10, 8-12).
- Refusjon gis for inntil 3 måneder før måneden kravet settes fram (§ 22-13). NAV betaler ikke sykepenger i lovbestemt ferie (§ 8-17).
- NAV betaler feriepenger av sykepenger for de første 48 dagene i opptjeningsåret (§ 8-33).
- Refundert lønn gir ikke AGA og føres som negativt grunnlag «refusjon fra NAV» i a-meldingen.
- NAVs oppgjørsrapport (tidligere K27) viser utbetalte refusjoner og hentes nå via API i Altinn 3 ([NAV](https://www.nav.no/arbeidsgiver/oppgjorsrapport)).

**Inntektsmelding** ([NAV](https://www.nav.no/arbeidsgiver/sende-inntektsmelding))

- Sendes etter at arbeidsgiverperioden er over og den ansatte har søkt; ny melding ved hvert nytt fravær. Meldingen er samtidig refusjonskravet.
- Fra lønnssystem: bare for sykepenger, via «Sykepenger IM LPS API» med Maskinporten og systembruker. Systemet henter forspørsler fra NAV og svarer på dem ([navikt på GitHub](https://github.com/navikt/sykepenger-im-lps-api)).
- Altinn 2 kan ikke brukes fra 21.5.2026. Tilgang krever tilgangspakken «Lønn med personopplysninger av særlig kategori».
- Foreldrepenger, svangerskapspenger, pleie-, opplærings- og omsorgspenger sendes foreløpig manuelt på Min side – arbeidsgiver.

**Andre ytelser**

| Ytelse | Arbeidsgivers del | Refusjon og rapportering |
| --- | --- | --- |
| Foreldrepenger | Lønn er frivillig, ofte tariff | Refusjon opp til 6G (80 %-dekning: 80 % av 6G); permisjon over 14 dager i a-meldingen |
| Svangerskapspenger | Ingen arbeidsgiverperiode | Refusjon ved lønn; ikke permisjon i a-meldingen |
| Pleie- og opplæringspenger | Ingen arbeidsgiverperiode eller lønnsplikt | Refusjon inntil 3 måneder bakover; permisjon over 14 dager |
| Omsorgspenger (sykt barn) | Betaler de første 10 dagene; 10 dager per år for 1–2 barn, 15 for 3 eller flere, doblet ved aleneomsorg | Refusjon fra dag 11, krav innen 3 måneder |
| Permittering | 15 dagers lønnsplikt | Permittering med egen ID og prosent i a-meldingen, uansett lengde |

**Sykefraværsstatistikk.** Arbeidsgiver skal føre kvartalsvis statistikk over sykefravær og barns sykdom, fordelt på egenmeldt og legemeldt fravær ([NAV](https://www.nav.no/arbeidsgiver/fore-sykefravar)). Den sendes ikke inn, men kan kreves fremlagt for Arbeidstilsynet.

Forslag om å korte arbeidsgiverperioden til 12 dager (utredning fra oktober 2025) er ikke fulgt opp i statsbudsjettet for 2027.
