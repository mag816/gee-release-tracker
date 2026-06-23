# PROJECT_STATE — Gee Release Tracker

**Last updated:** 2026-06-19  
**Status:** Active release-learning log  
**Owner:** Mariciel Georg / MG  
**Primary file:** `README.md`

---

## TL;DR

The release tracker is current through Mariciel’s `/version` check on **2026-06-19**, which still reports **gee-code v0.70.5** + “You're up to date,” and Neil’s Jun 18/19 Gee Test/Core “Huge New Release” note.

The new release wave is a major Beta-channel substrate/productization update: outcome loops, org/containerized task execution, scalable ticket-backed task queues, MS365 connector, Windows support, Operations panel, realtime voice/context upgrades, Telegram/group routing, live TaskGraph progress, and single DMG/EXE install packaging. The current action is not a blind upgrade; it is a supervised test queue focused on what matters for Mariciel’s NLYM, Edenic, GTEK, and Gee-learning workflows.

---

## Activity This Week

Recent commits:

- `0793db7` — auto: v0.70.0 detected 2026-06-09
- `897eed2` — auto: catch-up v0.70.3 2026-06-09
- `c3781da` — docs: refresh tracker to v0.70.5, update test queue
- `f55397e` — auto: catch-up GeeT 1.42.5 2026-06-12

---

## Current Test Queue

1. **Updater / installer boundary** — watch for the Beta build Neil referenced; test the single DMG/EXE path only in a low-risk window.
2. **Outcome Loops** — sandbox a harmless outcome and verify evidence, stop condition, escalation, and closure behavior.
3. **TaskGraph / DynamicHarness live progress** — run one visible graph in Pretext and verify progress/failure/final synthesis are easy to understand.
4. **Org/Container task isolation** — inspect task-session/delegation worktrees before trusting parallel work on real repos.
5. **Operations panel** — check whether event-driver health cards are clear enough for MG heartbeat/scheduled work monitoring.
6. **MS365 connector** — note for future Outlook/Microsoft clients; lower priority for NLYM while its operating system is Google Workspace.
7. **Realtime voice/context upgrades** — test later with a low-risk visible-surface question; privacy-aware because screenshots/DOM context may be included.
8. **Exa + Fable** — keep prior test items active: Exa for source-heavy research; Fable only in sandbox due premium cost sensitivity.

---

## Watch Items

- Confirm whether Neil’s “Huge New Release” appears as an updater-visible Beta version after local `/version` still showed `0.70.5` on Jun 19.
- Continue using the pinned Gee Test/Core iMessage chat for release intake.
- Avoid using Outcome Loops or containerized tasks on real NLYM/Edenic/GTEK deliverables until sandbox evidence/closure behavior is predictable.
- Keep installer/package testing away from critical work blocks because Neil explicitly flagged possible boundary bumps.

---

## Key References

| Resource | Path |
|---|---|
| Release log | `README.md` |
| Tracker repo | `gee-release-tracker/` |
| Source thread | Gee Test/Core iMessage chat |
