# Logg over planen

Nyeste øverst. Hver linje: dato, hva som ble endret, hvem.

| Dato | Endring | Av |
| --- | --- | --- |
| 19.10.2026 | Eierens bestilling: dynamiske dimensjoner, avvikskontroll og MCP med OAuth2. Tre nye pakker i fase 11: AP-1001 Dimensjoner (nøkkel med verdier på arbeidsgiveren, én verdi per ansatt, øyeblikksbilde i kjøringen, rapporten «Lønn per dimensjon» med delsummer som JSON og CSV), AP-1002 Avvikskontroll (hver ordinær beregning sammenlignes med de siste tre godkjente ordinære kjøringene: ny og manglende ansatt, brutto, netto og trekk over grensene, lønnsart ny eller borte; alt må kvitteres før godkjenning, `GET /lonnskjoringer/{id}/avvik`), AP-1003 MCP-tjener på `/api/mcp` med OAuth 2.1 i API-et (RFC 8414, 7591, 7636, 9728, samtykkeside, tilkoblede apper) og 15 verktøy for lesing, import av ansatte, timer og lønnsgrunnlag, opprettelse og beregning av kjøringer; ingen verktøy godkjenner. Ny NuGet-pakke ModelContextProtocol.AspNetCore 2.2.0. Grensene i AP-1002 (10 %, 1 000 kr, 5 prosentpoeng) er valgt av økten og bør bekreftes. | Fable 5.1 |
| 19.10.2026 | Eierens ønske: testmaskinen eksponeres gjennom Cloudflare-tunnelen som de andre containerne, som lonn.neoteric.no, og flyttes vekk fra 80/443. Caddy lytter nå på 8443 (LAN: https://192.168.71.230:8443), web-containeren er tunnelens origin på 8082, tunnelen «nas» har fått ingress-regel for lonn.neoteric.no (konfig versjon 20), API-et har KjenteProxynett for Docker-nettet så ratebegrensningen ser riktig klient-IP. Gjenstår for eieren: CNAME lonn → tunnelen i Cloudflare DNS, og anbefalt Access-policy på eierens e-post. Kode-commit fe7bfc6 (merget 76e3a23), rullet ut. Se docs/drift/utrulling.md. | Fable 5.1 |
| 19.10.2026 | Eierens ønske: UX etter lønnsarbeidet fra A til Å. Sidemenyen er gruppert i Grunnlag, Måneden, Oppfølging og Administrasjon i arbeidsrekkefølge og viser bare sider brukeren har rett til (systemadministrator ser Brukere og Ny arbeidsgiver, ikke lønnssidene). Startsiden for arbeidsgiveren viser månedens fire steg med status (pålegg og inntektsmeldinger som venter, kjøringens status, forfall, a-meldingens frist) og de neste fristene. «Rapportering» er blitt «Rapporter» med forklaring per rapport; plassholderen fra AP-802 er borte. Innstillinger bare i brukermenyen. Beskrevet i docs/design.md. | Fable 5.1 |
| 19.10.2026 | Eierens ønsker på testmaskinen: data og riktige arbeidsgivernavn. Databasen er nå Gullår-databasen (AP-901, Fjordvik Mekaniske AS, januar til september 2026, kjørt med LONN_TEST_POSTGRES og LONN_BEHOLD_TESTDATABASE mot maskinen, byttet inn som `lonn`; den tomme heter `lonn_tom`). API-et der bruker testnøklene. /api/auth/meg sender arbeidsgivernavn, så valgsiden viser navn for alle roller (commit 3c76740). | Fable 5.1 |
| 19.10.2026 | Eierens ønske: tofaktor settes opp med QR-kode. Oppsettsiden viser nå QR (otpauth-URI som SVG, pakken qrcode) med hemmeligheten som reserve. Kode-commit e33d43c, pushet og rullet ut til testmaskinen. | Fable 5.1 |
| 19.10.2026 | Eierens oppdrag: testmiljø som containere på hanschr@192.168.71.230 (Fedora Asahi, arm64). Satt opp med deploy/testmiljo (Compose-overlegg med Caddy for HTTPS, siden sesjonscookien er __Host- med Secure), Migrate.Dockerfile følger TARGETARCH. Kjører på https://192.168.71.230 med to arbeidsgivere og brukeren hanschr. Kode-commits 11db9da til 9db8b99 på main. | Fable 5.1 |
| 19.10.2026 | AP-907 ferdig, merget (c645af5). Alle arbeidspakker i planen (AP-000 til AP-907) er ferdige og merget til main. | Fable 5.1 |
| 19.10.2026 | Eierens beslutning: ingen fulle testsuiter i GitHub CI (koster for mye). ci.yml kjører nå bare format, bygg, migreringssjekk, Domain-, Parametre- og Integrasjoner-tester, Bicep-bygg og web-lint/bygg/enhetstester; PostgreSQL-suitene, Gullår, Ytelse, Playwright og containertesten ligger i full-gate.yml (manuell) og kjøres lokalt før merge; nattkjøringene i ytelse.yml og testmiljo.yml er tatt ut (bare «Run workflow»). CLAUDE.md og dokumentene oppdatert. | Fable 5.1 |
| 18.10.2026 | AP-906 ferdig, merget (b408aea). API-testenes flakehet rettet i testinfrastrukturen. AP-907 rebaser som siste pakke. | Fable 5.1 |
| 18.10.2026 | AP-907 levert, til gjennomgang hos Opus. AP-906 kjører stille API-runde. | Fable 5.1 |
| 18.10.2026 | AP-905 ferdig, merget (348c2fe). AP-907 startet; AP-906 hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-906 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-604 ferdig, merget (8b7289b). AP-905 rebaser som neste; AP-906 bygger. | Fable 5.1 |
| 18.10.2026 | AP-109 ferdig, merget (304605c). Bølge 15 fullført. AP-906 startet; AP-604 rebaser, så AP-905. | Fable 5.1 |
| 18.10.2026 | AP-109 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-109 og AP-604 levert første versjon, porten ufullstendig på grunn av minnemangel; sekvensert: AP-109 rebaser og kjører porten alene, AP-604 kjører lette prosjekter. Spørsmål 118. | Fable 5.1 |
| 18.10.2026 | AP-905 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-803 ferdig, merget (8ba55ca). Alle opprinnelige pakker (AP-000 til AP-904) er ferdige; oppfølgingspakkene AP-109, AP-604, AP-905 pågår, AP-906 og AP-907 venter. | Fable 5.1 |
| 18.10.2026 | AP-803 levert, til gjennomgang hos Opus. Nr. 106 utvidet; AP-109 fikk fristkalender-endepunktet. | Fable 5.1 |
| 18.10.2026 | AP-604 og AP-905 startet fra main da5e6b7 parallelt med bølge 15; AP-906 venter på AP-109 (begge rører sletting og auth), AP-907 venter på AP-905. | Fable 5.1 |
| 18.10.2026 | AP-406 ferdig, merget (da5e6b7). Bølge 14 fullført. AP-803 startet. | Fable 5.1 |
| 18.10.2026 | AP-902 ferdig, merget (2845733). AP-406 rebaser som neste; AP-803 starter etter den. | Fable 5.1 |
| 18.10.2026 | AP-904 ferdig, merget (ec2585b). AP-902 rebaser som neste. | Fable 5.1 |
| 18.10.2026 | Bølge 15 startet med AP-109; AP-803 venter på AP-406. | Fable 5.1 |
| 18.10.2026 | Oppfølgingspakker opprettet: AP-109 (API-mangler for brukerflaten), AP-604 (særgrupper del 2), AP-905 (drift og utrulling), AP-906 (sletteløp del 2 og rettelser), AP-907 (varsling). Bølge 15 er AP-803 og AP-109, bølge 16 er AP-604, AP-905, AP-906 og AP-907. Spørsmål 111 til 117. | Fable 5.1 |
| 18.10.2026 | AP-902 levert, til gjennomgang hos Fable. AP-406 gjennomgått av Opus, tre funn rettes. AP-904 rettet, Fable kjører porten. | Fable 5.1 |
| 18.10.2026 | AP-904 gjennomgått av Fable; to funn rettes. | Fable 5.1 |
| 18.10.2026 | AP-406 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-804 ferdig, merget (354073b). | Fable 5.1 |
| 18.10.2026 | AP-901 ferdig, merget (ee992cb). Bølge 13 fullført. | Fable 5.1 |
| 18.10.2026 | AP-804 levert, til gjennomgang hos Opus. Nr. 106 utvidet. | Fable 5.1 |
| 18.10.2026 | Bølge 14 startet: AP-406, AP-804, AP-902 (K4, Opus med gjennomgang av Fable) og AP-904 fra main ad9abd2, parallelt med at AP-901 avslutter bølge 13. Spørsmål 110 (testmiljø krever eierens handlinger). | Fable 5.1 |
| 18.10.2026 | AP-505 ferdig, merget (ad9abd2). AP-901 rebaser med oppfølgingene. | Fable 5.1 |
| 18.10.2026 | AP-405 ferdig, merget (28e5218). AP-505 rebaser som neste, så AP-901. | Fable 5.1 |
| 18.10.2026 | AP-706 ferdig, merget (6b799d4). AP-505 rebaser som neste, så AP-405 og AP-901. | Fable 5.1 |
| 18.10.2026 | Spørsmål 109 (halv skatt uavhengig av utbetalingsdag i desember) lagt inn med standard; rettes i AP-901. | Fable 5.1 |
| 18.10.2026 | AP-901 levert, til gjennomgang hos Fable. AP-706 verifiseres. | Fable 5.1 |
| 18.10.2026 | AP-805 ferdig, merget (9a2646b). AP-706 rebaser som neste. | Fable 5.1 |
| 18.10.2026 | AP-405 levert, til gjennomgang hos Fable. Spørsmål 108. | Fable 5.1 |
| 18.10.2026 | AP-903 ferdig, merget (876af7f). Bølge 12 fullført. | Fable 5.1 |
| 18.10.2026 | AP-505 gjennomgått av Opus; seks funn rettes. Nr. 107 avgjort. | Fable 5.1 |
| 18.10.2026 | AP-505 levert, til gjennomgang hos Opus. Spørsmål 107. | Fable 5.1 |
| 18.10.2026 | AP-805 gjennomgått av Opus; tre funn rettes. AP-008 kriterium 1 presisert (utsatte chunker). | Fable 5.1 |
| 18.10.2026 | AP-805 levert, til gjennomgang hos Opus. Spørsmål 106 (API-mangler til AP-109). | Fable 5.1 |
| 18.10.2026 | AP-702 ferdig, merget (d168e9c). AP-706 levert, til gjennomgang hos Sonnet. | Fable 5.1 |
| 18.10.2026 | Bølge 13 startet: AP-405, AP-505, AP-706, AP-805 og AP-901 fra main 5470449, parallelt med at AP-702 og AP-903 avslutter bølge 12. | Fable 5.1 |
| 18.10.2026 | AP-703 ferdig, merget (5470449). AP-702 rebaser som neste; AP-903 retter. | Fable 5.1 |
| 18.10.2026 | AP-903 gjennomgått av Opus; rebase og fire funn. Spørsmål 105. | Fable 5.1 |
| 18.10.2026 | AP-504 ferdig, merget (565cc29). AP-903 levert, til gjennomgang hos Opus. AP-703 rebaser som neste, så AP-702. | Fable 5.1 |
| 18.10.2026 | AP-404 ferdig, merget (be98158). AP-504 rebaser som neste, så AP-703, AP-702, AP-903. | Fable 5.1 |
| 18.10.2026 | AP-304 ferdig, merget (c71475f). AP-504 rebaser som neste. | Fable 5.1 |
| 18.10.2026 | AP-802 ferdig, merget (9dd5fae). Merge-kø: AP-304, AP-504, AP-404, AP-703, AP-702, AP-903. | Fable 5.1 |
| 18.10.2026 | AP-601 ferdig, merget (42251f0). AP-304 og AP-504 godkjent av Fable med små rettelser. AP-404, AP-702 og AP-703 rettet. Merge-kø: AP-802, AP-304, AP-504, AP-404, AP-703, AP-702, AP-903. | Fable 5.1 |
| 18.10.2026 | AP-304, AP-504 og AP-601 levert (Fable gjennomgår; AP-601 godkjent). AP-702 gjennomgått av Opus (to funn). AP-802 rettet. Spørsmål 103 og 104. | Fable 5.1 |
| 18.10.2026 | AP-404 gjennomgått av Opus mot Skatteetatens regelliste; nivåer rettes. Kriteriene 2–6 presisert. Spørsmål 102. | Fable 5.1 |
| 18.10.2026 | AP-703 gjennomgått av Opus; ett funn må rettes. Noter i AP-705 og AP-407. | Fable 5.1 |
| 18.10.2026 | AP-802 gjennomgått av Opus; fem funn rettes. Spørsmål 101. | Fable 5.1 |
| 18.10.2026 | AP-702 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-704 ferdig, merget (805b2bf). Bølge 11 komplett. AP-404, AP-703 og AP-802 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 18.10.2026 | AP-503 ferdig, merget (35a0008). AP-504 startet. AP-704 rebaser som siste i bølge 11. | Fable 5.1 |
| 18.10.2026 | Bølge 12 startet for AP-304, AP-404, AP-601, AP-702, AP-703, AP-802 og AP-903 fra main 7db0cce; AP-504 venter på AP-503. | Fable 5.1 |
| 18.10.2026 | AP-303 ferdig, merget (7db0cce). AP-503 rebaser som neste, så AP-704. | Fable 5.1 |
| 18.10.2026 | AP-403 ferdig, merget (61a5afb). AP-303 rebaser som neste. | Fable 5.1 |
| 17.10.2026 | AP-302 ferdig, merget (eaa2025). AP-403 rebaser som neste. | Fable 5.1 |
| 17.10.2026 | AP-306 ferdig, merget (4960592). AP-302, AP-303, AP-403, AP-503 og AP-704 er rettet og rebases i rekkefølge. | Fable 5.1 |
| 17.10.2026 | AP-403 og AP-503 gjennomgått av Fable (godkjent med rettelser; AP-503 må trekke fastlønn for sykedager). Spørsmål 100. AP-306 rebaser for merge. | Fable 5.1 |
| 17.10.2026 | AP-305 ferdig, merget (398f3aa). AP-303, AP-403 og AP-503 levert (Fable gjennomgår). AP-704 gjennomgått av Opus (tre funn). AP-302 og AP-306 retter. | Fable 5.1 |
| 17.10.2026 | AP-704 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-302 gjennomgått av Opus; fire funn rettes, kriterium 5 rettet (maskering). | Fable 5.1 |
| 17.10.2026 | AP-302 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-306 gjennomgått av Opus; KID-struktur fra Skatteetaten må implementeres. Kriterium 4 rettet. Spørsmål 99. | Fable 5.1 |
| 17.10.2026 | AP-305 gjennomgått av Opus; sju funn rettes. Spørsmål 98. | Fable 5.1 |
| 17.10.2026 | AP-306 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-305 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-301 ferdig, merget (c27b055). Bølge 10 komplett. Bølge 11 startet: AP-302, AP-303, AP-305, AP-306, AP-403, AP-503, AP-704 fra main c27b055. | Fable 5.1 |
| 17.10.2026 | AP-301 levert og gjennomgått av Fable; godkjent med tre rettelser. Spørsmål 97. Noter i AP-210, AP-302, AP-305, AP-403. | Fable 5.1 |
| 17.10.2026 | AP-603 ferdig, merget (e9a9bcc). Bølge 10 mangler bare AP-301 (lønnskjøringen). | Fable 5.1 |
| 17.10.2026 | AP-705 ferdig, merget (1708ab2). AP-603 rettet, tar siste rebase. AP-301 bygger. | Fable 5.1 |
| 17.10.2026 | AP-603 levert og gjennomgått av Fable; godkjent med små rettelser. Spørsmål 96 (utsatte deler, G-dato for etterlønn). | Fable 5.1 |
| 17.10.2026 | AP-705 gjennomgått av Opus; tre funn rettes. Noter i AP-301, AP-304 og AP-703. | Fable 5.1 |
| 17.10.2026 | AP-705 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-506 ferdig, merget (7a35593). Bølge 9 komplett. Bølge 10 (AP-301, AP-603, AP-705) pågår. | Fable 5.1 |
| 17.10.2026 | AP-207 ferdig, merget (2083b00). Bølge 9 mangler bare AP-506. | Fable 5.1 |
| 17.10.2026 | Bølge 10 startet: AP-301, AP-603 og AP-705 på egne grener fra main b5e4191, parallelt med rettingene i AP-207 og AP-506. | Fable 5.1 |
| 17.10.2026 | AP-507 ferdig, merget (b5e4191). Bølge 9 mangler AP-207 og AP-506 (retter). Bølge 10 (AP-301, AP-603, AP-705) forberedes. | Fable 5.1 |
| 17.10.2026 | AP-206 ferdig (5897634) og AP-801 ferdig (02b4a77). Gjenstår i bølge 9: AP-207, AP-506 (retter), AP-507 (rebaset, OpenAPI-kopi oppdateres). | Fable 5.1 |
| 17.10.2026 | AP-506 gjennomgått av Opus; sju funn rettes. Kriterier i AP-207 og AP-506 rettet. AP-206 og AP-801 rettet og rebases for merge. | Fable 5.1 |
| 17.10.2026 | AP-502 ferdig, merget (c968c58). AP-207 gjennomgått av Opus (fire funn, kriterier rettet). AP-507 rettet. | Fable 5.1 |
| 17.10.2026 | AP-204 ferdig, merget (655fb5f). AP-801 gjennomgått av Opus (fem funn, fødselsnummer i søke-URL viktigst). AP-506 levert, til gjennomgang hos Opus. AP-206 rettet etter Fables gjennomgang. Spørsmål 95 (API-mangler fra UI). | Fable 5.1 |
| 17.10.2026 | AP-502 gjennomgått av Fable, godkjent med små rettelser. Spørsmål 94. | Fable 5.1 |
| 17.10.2026 | AP-207 og AP-502 levert (til gjennomgang hos Opus og Fable). AP-507 gjennomgått av Sonnet; to funn rettes. Note i AP-805. | Fable 5.1 |
| 17.10.2026 | AP-206 levert og gjennomgått av Fable; én lovrettelse (trekk ved fratreden), kriterium 9 rettet. Spørsmål 93. | Fable 5.1 |
| 17.10.2026 | AP-210 ferdig, merget (3267487). Bølge 8 komplett. AP-204 gjennomgått av Opus (fire funn), AP-801 og AP-507 levert og til gjennomgang. Spørsmål 5 lukket, spørsmål 92. | Fable 5.1 |
| 17.10.2026 | AP-211 ferdig, merget (f01dcbf). AP-204 levert, til gjennomgang hos Opus. AP-210 tar siste rebase. | Fable 5.1 |
| 17.10.2026 | AP-107 ferdig, merget (128f0e8). AP-210 og AP-211 rebaser. | Fable 5.1 |
| 17.10.2026 | Bølge 9 startet: AP-204, AP-206, AP-207, AP-502, AP-506, AP-507 og AP-801 på egne grener fra main 43009ad. AP-107, AP-210 og AP-211 fra bølge 8 gjenstår å merge. | Fable 5.1 |
| 17.10.2026 | AP-501 ferdig, merget (43009ad). AP-211 rettet. AP-107, AP-210 og AP-211 rebaser i rekkefølge. | Fable 5.1 |
| 17.10.2026 | AP-108 ferdig, merget (7d3dda2). AP-501, AP-107 og AP-210 rebaser i rekkefølge. | Fable 5.1 |
| 17.10.2026 | AP-211 gjennomgått av Opus; seks funn rettes (timelønn ved deltid var feil). Spørsmål 52 utvidet, spørsmål 91. | Fable 5.1 |
| 17.10.2026 | AP-212 ferdig, merget (d8c5349). AP-107, AP-108 og AP-501 rettet etter gjennomgang og venter på rebase og merge. | Fable 5.1 |
| 17.10.2026 | AP-209 ferdig, merget (e4ae440). AP-211 levert, til gjennomgang hos Opus. AP-212 og AP-108 rebaser mot ny main. | Fable 5.1 |
| 17.10.2026 | AP-501 gjennomgått av Opus; overlapp per arbeidsforhold rettes. Spørsmål 90. | Fable 5.1 |
| 17.10.2026 | AP-602 ferdig, merget (a20627e). AP-107 gjennomgått av Opus; fem funn rettes, kriterium 4 rettet etter § 14-5 tredje ledd. AP-212 rettet, rebaser mot ny main. | Fable 5.1 |
| 17.10.2026 | AP-108 gjennomgått av Opus: satsene stemmer, dokumentasjon og tester rettes. Spørsmål 89 (nattarbeidsflagg). | Fable 5.1 |
| 17.10.2026 | AP-501 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-402 ferdig, merget (8c6a0dd). Bølge 7 (AP-104, AP-201, AP-402) komplett. Køen for rebase og merge: AP-602, AP-209, AP-210, AP-212. | Fable 5.1 |
| 17.10.2026 | AP-107 levert, til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-108 levert, til gjennomgang hos Opus. Spørsmål 33 besvart. | Fable 5.1 |
| 17.10.2026 | AP-205 ferdig, merget (24dfbe1). AP-402 rettet (XML-eksport krever LesFulltFodselsnummer) og rebaser; ADR-nummer kolliderte med AP-205 (0020) og blir 0021. | Fable 5.1 |
| 17.10.2026 | AP-212 gjennomgått av Opus; sju funn rettes. Spørsmål 88 i AP-009, note i AP-301. AP-205 rebaser for siste gang og merges straks. | Fable 5.1 |
| 17.10.2026 | AP-208 ferdig, merget (6594c06). AP-209 gjennomgått av Opus (fire funn rettes, blant annet 6-timersregelen skal være «6 timer eller mer» og 120 000-taket mangler hjemmel). AP-602 og AP-210 rettet, rebaser mot ny main. | Fable 5.1 |
| 17.10.2026 | AP-402 gjennomgått av Fable og godkjent med én rettelse (policy på XML-eksport). AP-205 rebaser en gang til etter AP-202. Noter i AP-904. | Fable 5.1 |
| 17.10.2026 | Bølge 8 fortsetter etter AP-104: AP-107, AP-108, AP-211 og AP-501 startet på Sonnet 5.5 (worktrees ap107, ap108, ap211, ap501). AP-107 modellerer ikke trekkavtaler (det er AP-212). | Fable 5.1 |
| 17.10.2026 | AP-104 ferdig (merget a41c432) og AP-202 ferdig (merget 149ce2d). To lastfølsomme tester fikk romsligere grenser på main (trekktabellinnlasting 10 s, innloggingstiming 50 ms) etter at de feilet under ni samtidige testverter. AP-209, AP-212 og AP-402 levert; AP-209 og AP-212 til gjennomgang hos Opus, AP-402 hos Fable. | Fable 5.1 |
| 17.10.2026 | AP-205 gjennomgått av Fable (godkjent, én serialiseringsrettelse). AP-210 til gjennomgang hos Opus. AP-602 til gjennomgang hos Opus; spesifikasjonen presisert (fradrag i trinn 2). Noter i AP-101 og AP-301. | Fable 5.1 |
| 17.10.2026 | AP-202 gjennomgått av Fable; ett funn rettes (fjorårets kort bare i januar). Spørsmål 83 til 86 i AP-009. AP-208 gjennomgått av Opus: tre funn må rettes (to kjøringer samme måned mistet data, tilbakerulling i låst periode, 8 000 kr gave uten kilde); Sonnet retter. | Fable 5.1 |
| 17.10.2026 | AP-104 gjennomgått av Fable og godkjent; rebaser. AP-208 til gjennomgang hos Opus. Spørsmål 82 i AP-009. | Fable 5.1 |
| 17.10.2026 | AP-201 ferdig, merget (bb08fb8). Bølge 8 startet med de sju pakkene som bare trengte AP-201: AP-202 og AP-205 på Opus, AP-208, AP-209, AP-210, AP-212 og AP-602 på Sonnet (worktrees ap202, ap205, ap208, ap209, ap210, ap212, ap602). AP-107, AP-108, AP-211 og AP-501 venter på AP-104. | Fable 5.1 |
| 17.10.2026 | AP-008 ferdig, merget (9ce8dfc). Bølge 6 komplett (AP-008, AP-101, AP-103, AP-106). | Fable 5.1 |
| 17.10.2026 | AP-201 gjennomgått av Fable og godkjent; rebaser. Spørsmål 79 til 81 i AP-009, note i AP-301. | Fable 5.1 |
| 17.10.2026 | AP-101 ferdig, merget (a02eac1). AP-201 levert av Opus, til gjennomgang hos Fable. | Fable 5.1 |
| 17.10.2026 | AP-103 ferdig, merget (1647c27). AP-104 og AP-402 startes på Opus (worktrees ap104, ap402). | Fable 5.1 |
| 17.10.2026 | AP-008, AP-101 og AP-103 rettet etter gjennomgang; merges i rekkefølgen AP-103, AP-101, AP-008 med rebase og regenererte migreringer etter AP-106. | Fable 5.1 |
| 17.10.2026 | Bølge 7 startet med AP-201 på Opus 5.5 (worktree lonnssystem-ap201, gren ap-201) siden AP-106 er merget. AP-104 og AP-402 venter på AP-103. | Fable 5.1 |
| 17.10.2026 | AP-106 ferdig, merget (b808e02). | Fable 5.1 |
| 17.10.2026 | AP-101 og AP-103 gjennomgått av Opus; rettelser pågår på Sonnet. Spørsmål 75 til 78 i AP-009, noter i AP-205 og AP-801. Spesifikasjonen i AP-101 rettet: 974760673 er Registerenheten i Brønnøysund. | Fable 5.1 |
| 17.10.2026 | AP-008 gjennomgått av Opus; rettelser og Radix-innføring pågår. AP-101 og AP-103 til gjennomgang hos Opus. Spørsmål 44 besvart (Enhetsregisteret), 73 og 74 lagt til. | Fable 5.1 |
| 17.10.2026 | AP-106 gjennomgått av Opus, seks funn rettes av Sonnet. Spørsmål 70 til 72 i AP-009, noter i AP-301 og AP-303. AP-008 til gjennomgang hos Opus. | Fable 5.1 |
| 17.10.2026 | AP-007 ferdig, merget (30f796d). Bølge 5 komplett. Bølge 6 fortsetter: AP-008, AP-101, AP-103 startes på Sonnet (worktrees ap008, ap101, ap103); AP-106 får beskjed om å legge på endepunktene. | Fable 5.1 |
| 17.10.2026 | Bølge 6 startet med AP-106 på Sonnet 5.5 (worktree lonnssystem-ap106, gren ap-106): domene, data, lagring og tjenester først; endepunktene legges på AP-007 sitt mønster når AP-007 er merget. AP-008, AP-101 og AP-103 venter på AP-007. | Fable 5.1 |
| 17.10.2026 | AP-105 ferdig, merget (6e830c1). Bare AP-007 gjenstår i bølge 5. | Fable 5.1 |
| 17.10.2026 | AP-401 ferdig, merget (e10efbb). | Fable 5.1 |
| 17.10.2026 | AP-105 gjennomgått (kodelistene bekreftet mot Skatteetatens xlsx), to funn rettes. Spørsmål 49 besvart: ansettelsesform har fem koder (fast, midlertidig, fastAnsattUtleid, midlertidigAnsattUtleid, midlertidigAnsattSomTilkallingsvikar). | Fable 5.1 |
| 17.10.2026 | AP-401 gjennomgått av Fable og godkjent; Opus rebaser og regenererer migreringen etter AP-701. AP-007 rettet etter Opus-gjennomgang, merges sist i bølgen. Spørsmål 69 i AP-009, noter i AP-902 og AP-904. | Fable 5.1 |
| 17.10.2026 | AP-701 ferdig (merget 4e1b833) og AP-203 ferdig (merget a5a615e). Worktree-mappene slettet. | Fable 5.1 |
| 17.10.2026 | AP-701 implementert av Opus og gjennomgått av Fable; ett funn rettes (slettefrist regnes fra sluttdato + 1 år til lønnstabellene finnes, fordi feriepenger utbetales året etter). Spørsmål 67 og 68 i AP-009. Noter i AP-301, AP-805 og AP-902. | Fable 5.1 |
| 17.10.2026 | AP-203 til gjennomgang, rettelser pågår. Akseptansekriterium 2 (tabell 8000 i stedet for 7100) og 7 (3 s i stedet for 500 ms) og importkommandoen justert i pakkefilen. Spørsmål 66 i AP-009. Eieren ba om at ferdige worktree-mapper slettes; ap004, ap006 og ap102 er slettet. | Fable 5.1 |
| 17.10.2026 | AP-102 ferdig: gjennomgått av Sonnet, rettelser verifisert, merget (5319ba9). Spørsmål 65 i AP-009 (Jan Mayen). | Fable 5.1 |
| 17.10.2026 | AP-004 ferdig: gjennomgått av Sonnet, rettelser av Haiku verifisert, merget (0e3d631). Spørsmål 64 i AP-009 (km-sats 5,30 eller 5,00; gave 20 år). | Fable 5.1 |
| 17.10.2026 | AP-102 fullført av Sonnet, til gjennomgang hos Sonnet (egen økt). Beregningskodestrengene bekreftes når AP-105 har a-meldingens kodeliste. Delte kommuner notert i AP-101. | Fable 5.1 |
| 17.10.2026 | AP-004 til gjennomgang hos Sonnet. AP-203 eskalert til Sonnet for fullføring (to røde tester, 21 MB innebygd tabell skal gzippes). | Fable 5.1 |
| 17.10.2026 | AP-105 eskalert fra Haiku til Sonnet for a-meldingens kodelister; AP-004 fikk avgjørelser fra Fable (G verifisert mot NAV: 130 160 fra 1.5.2025, 136 549 fra 1.5.2026, snitt 134 419; primærkilder i stedet for research; forslagsår unntas fra kravet om komplette nøkler). Erfaring: K1-datapakker som krever kildehenting fra nett bør gå på Sonnet, ikke Haiku. | Fable 5.1 |
| 17.10.2026 | Bølge 5 fortsetter etter AP-006: AP-007 på Sonnet (ap-007), AP-401 og AP-701 på Opus (ap-401, ap-701). AP-102 eskalert fra Haiku til Sonnet fordi kildedataene ikke ble hentet; rammeverket fra Haiku beholdes. | Fable 5.1 |
| 17.10.2026 | AP-006 ferdig: rettelser verifisert, merget til main (dc36b4e). Bølge 4 er dermed komplett. | Fable 5.1 |
| 17.10.2026 | AP-006 implementert av Opus og gjennomgått av Fable; to funn rettes (selvtildeling av roller, global deaktivering). Avgjort: en bruker kan ikke gi seg selv roller; deaktivering bare når brukeren ikke har roller hos andre arbeidsgivere. Bølge 5-datapakkene startet på Haiku 5.5: AP-004 (ap-004), AP-102 (ap-102), AP-105 (ap-105), AP-203 (ap-203). Eieren ga stående instruks: gjør alle oppgaver uten å spørre, stopp bare for spørsmål som trenger svar. | Fable 5.1 |
| 17.10.2026 | AP-407 ferdig: gjennomgått av Opus, rettelser av Sonnet verifisert av Fable, merget til main (f3d55c6). E-postport utsatt til AP-007. Spørsmål 57 til 60 i AP-009. | Fable 5.1 |
| 17.10.2026 | AP-003 ferdig: gjennomgått av Opus, rettelser av Sonnet verifisert av Fable, merget til main (60cf8b3). Spørsmål 55 og 56 i AP-009. | Fable 5.1 |
| 17.10.2026 | Bølge 4 startet av Fable: AP-003 på Sonnet 5.5 (worktree lonnssystem-ap003, gren ap-003), AP-006 på Opus 5.5 (lonnssystem-ap006, ap-006), AP-407 på Sonnet 5.5 (lonnssystem-ap407, ap-407). Status pågår. | Fable 5.1 |
| 17.10.2026 | AP-005 ferdig: gjennomgått av Fable med databasetester mot PostgreSQL i Docker, to funn rettet (HMAC per arbeidsgiver, INSERT-sperre i låst periode), merget til main (06f5c1c). Avgjort: nye rader kan ikke legges inn i en låst periode. AP-009 spm. 47 besvart, nytt spm. 54, dupliserte numre 47/48 rettet til 52/53. Neste bølge: AP-003, AP-006, AP-407. | Fable 5.1 |
| 17.10.2026 | AP-005 implementert av Opus 5.5 på lokal gren ap-005, status til gjennomgang. Databasetestene venter på Docker Desktop (eieren installerer og rebooter). | Fable 5.1 |
| 17.10.2026 | AP-002 ferdig: implementert av Sonnet, gjennomgått av Opus (8 funn rettet), merget til main av Fable. Nye spørsmål 50 og 51 i AP-009. | Fable 5.1 |
| 17.10.2026 | AP-002 startet på Sonnet 5.5 (worktree lonnssystem-ap002, gren ap-002) og AP-005 på Opus 5.5 (worktree lonnssystem-ap005, gren ap-005). Docker installeres på utviklermaskinen; AP-005 sine databasetester kjører i CI uansett. | Fable 5.1 |
| 17.10.2026 | Eieren bekreftet ADR 0004 (kontantprinsippet), 0007 (periodelås og reversering) og 0008 (flerkunde). AP-001 ferdig. Bølge 3 (AP-002, AP-005) kan starte. | Hans Christian Thjømøe |
| 17.10.2026 | AP-001 implementert av Fable 5.1 i koderepoet (verdityper, domenetyper, 12 ADR-er, 10 invariant-filer, DI-registrering med validering, arkitekturtester). Status «til gjennomgang»: eieren må lese og bekrefte ADR 0004, 0007 og 0008 her i loggen. Nytt spørsmål 49 i AP-009 (ansettelsesform-koder). | Fable 5.1 |
| 17.10.2026 | Eieren valgte Azure som hosting. Ført inn i 01-arkitektur (Drift), AP-000 og AP-009 spm. 47. Region og tjenester avgjøres i AP-005. | Fable 5.1 |
| 17.10.2026 | Eieren presiserte: ett designsystem med felles komponenter og gjenbruk i `web/`, og i backend dependency injection, god arkitektur og riktig granularitet av tjenester. Lagt inn som to prinsipper i 01-arkitektur, ADR 0011 og 0012 i AP-001, og i `CLAUDE.md` i koderepoet. | Fable 5.1 |
| 17.10.2026 | Eieren pekte på designsystemet i hybriden/harmonix (Liquid Glass) som designet for brukerflaten. Dokumentert i `lonnssystem/docs/design.md`; AP-008 porterer det, UI-pakkene bygger på det. Nytt spørsmål 48 i AP-009 (merkefarge). | Fable 5.1 |
| 17.10.2026 | Eieren bekreftet: hosting i EØS, og systemet er flerkunde fra dag én. Ført inn i 01-arkitektur, AP-000 og AP-009 (spm. 46 og 47). | Fable 5.1 |
| 17.10.2026 | Planen opprettet: arkitektur, 68 arbeidspakker i 10 faser, modelltildeling. Stack valgt: .NET 10 backend med React/TS-frontend, PostgreSQL. Alternativet (TypeScript-monorepo) ble lagt fram og valgt bort av eieren. Koderepoet [hybriden/lonnssystem](https://github.com/hybriden/lonnssystem) opprettet med AP-000. | Fable 5.1 |
