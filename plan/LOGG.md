# Logg over planen

Nyeste øverst. Hver linje: dato, hva som ble endret, hvem.

| Dato | Endring | Av |
| --- | --- | --- |
| 17.10.2026 | AP-002 startet på Sonnet 5.5 (worktree lonnssystem-ap002, gren ap-002) og AP-005 på Opus 5.5 (worktree lonnssystem-ap005, gren ap-005). Docker installeres på utviklermaskinen; AP-005 sine databasetester kjører i CI uansett. | Fable 5.1 |
| 17.10.2026 | Eieren bekreftet ADR 0004 (kontantprinsippet), 0007 (periodelås og reversering) og 0008 (flerkunde). AP-001 ferdig. Bølge 3 (AP-002, AP-005) kan starte. | Hans Christian Thjømøe |
| 17.10.2026 | AP-001 implementert av Fable 5.1 i koderepoet (verdityper, domenetyper, 12 ADR-er, 10 invariant-filer, DI-registrering med validering, arkitekturtester). Status «til gjennomgang»: eieren må lese og bekrefte ADR 0004, 0007 og 0008 her i loggen. Nytt spørsmål 49 i AP-009 (ansettelsesform-koder). | Fable 5.1 |
| 17.10.2026 | Eieren valgte Azure som hosting. Ført inn i 01-arkitektur (Drift), AP-000 og AP-009 spm. 47. Region og tjenester avgjøres i AP-005. | Fable 5.1 |
| 17.10.2026 | Eieren presiserte: ett designsystem med felles komponenter og gjenbruk i `web/`, og i backend dependency injection, god arkitektur og riktig granularitet av tjenester. Lagt inn som to prinsipper i 01-arkitektur, ADR 0011 og 0012 i AP-001, og i `CLAUDE.md` i koderepoet. | Fable 5.1 |
| 17.10.2026 | Eieren pekte på designsystemet i hybriden/harmonix (Liquid Glass) som designet for brukerflaten. Dokumentert i `lonnssystem/docs/design.md`; AP-008 porterer det, UI-pakkene bygger på det. Nytt spørsmål 48 i AP-009 (merkefarge). | Fable 5.1 |
| 17.10.2026 | Eieren bekreftet: hosting i EØS, og systemet er flerkunde fra dag én. Ført inn i 01-arkitektur, AP-000 og AP-009 (spm. 46 og 47). | Fable 5.1 |
| 17.10.2026 | Planen opprettet: arkitektur, 68 arbeidspakker i 10 faser, modelltildeling. Stack valgt: .NET 10 backend med React/TS-frontend, PostgreSQL. Alternativet (TypeScript-monorepo) ble lagt fram og valgt bort av eieren. Koderepoet [hybriden/lonnssystem](https://github.com/hybriden/lonnssystem) opprettet med AP-000. | Fable 5.1 |
