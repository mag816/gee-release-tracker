# PROJECT_STATE — Gee Release Tracker

**Last updated:** 2026-07-01
**Status:** Active release-learning log
**Owner:** Mariciel Georg / MG
**Primary file:** `README.md`

---

## TL;DR

The release tracker is current through Neil’s Gee Test/Core iMessage release note sent **2026-06-30 20:46–20:48 PT** / **2026-07-01 UTC** for **Gee-Code `0.72.2` + Gee/T `1.43.5` headline build**, with Neil’s detailed list also noting a Gee/T version bump from `1.43.2` to `1.43.6`.

The current wave is about safer autonomous operation and recovery: least-privilege task workers, stronger parent/child approval handling, unified follow-up policy, faster OutcomeLoop wake behavior, OpenClaw sandboxing/error surfacing, Sonnet 5 and Gemma 4 model routing, typed capability packaging, stronger outbound/thread/attachment routing, shared Gee-HQ/Terminal surfaces, and Pretext panel/bridge hardening. The highest-value next move is a supervised testing pass using Mariciel’s real workflows as examples, while avoiding external sends, money movement, destructive edits, or client-visible changes.

The current action is not a blind upgrade. Use a supervised test queue focused on what matters for Mariciel’s NLYM, Edenic, GTEK, and Gee-learning workflows.

---

## Activity This Week

Recent tracker commits:

- `f5d5bde` — auto: v0.72.1 detected 2026-06-28
- `43d4773` — auto: catch-up v0.71.2 2026-06-25
- `d3c012c` — auto: catch-up v0.71.1 2026-06-24
- `56a17dc` — auto: catch-up v0.70.15 2026-06-23
- `f274027` — docs: update release tracker test queue

Recent release entries captured in `README.md`:

- 2026-06-30 — Gee-Code `0.72.2` + Gee/T `1.43.5` headline / `1.43.6` detailed version bump release
- 2026-06-27 — Gee-Code `0.72.1` follow-up build
- 2026-06-26 — Gee-Code `0.72.0` + Gee-Terminal `1.43.3` Mac / `1.43.4` Windows release
- 2026-06-25 — Gee-Code `0.71.2` + Gee-Terminal `1.43.1` Mac / `1.43.2` PC release
- 2026-06-24 — Gee-Code `0.71.1` + Gee/T `1.42.57` Beta release

---

## Current Test Queue

1. **Version / updater check — CURRENT TARGET.** Confirm local Gee-Code `0.72.2` and Gee/T `1.43.5`/`1.43.6` after daemon or Gee/T restart. If the local version lags, record the blocker before deeper feature testing.
2. **Task-worker guardrails — sandbox test.** Delegate a harmless read-only task, then confirm the worker cannot send outbound, cannot turn progress chatter into a final answer, and cannot close with empty/placeholder work. Good MG example: ask a worker to inspect the Gee Release Tracker test queue and return a summary only.
3. **Follow-up policy — MG operating-system test.** Try closing a low-risk follow-up with a vague disposition such as “reviewed” or “still pending” and confirm the tool rejects it or requires a durable close reason. Good example: use a non-client/internal follow-up row only.
4. **OutcomeLoop approval reuse — low-risk sandbox.** Run one tiny loop with a parent approval and child task, then confirm the child reuses parent approval evidence and the runner wakes promptly after completion. Good example: draft-only “prepare a test checklist” loop, no sends or file mutations without approval.
5. **OpenClaw / Gee-Claw sandbox.** Run a read-only OpenClaw/Gee-Claw task and confirm errors surface clearly instead of vanishing. Good example: inspect a public/non-sensitive repo or release tracker docs, not NLYM finance or client files.
6. **Model/capability routing — safe compare.** Confirm Sonnet 5 tiers, Gemma 4 via Cerebras, and typed capability inventory show up where expected. Good example: ask for a short comparison of which model should handle code review vs finance review; do not run on confidential data.
7. **Knowledge skills — non-sensitive corpus.** Confirm `/skills deep-knowledge-compiler` and `/skills knowledge` are listed as package-level skills, then test on a small public/non-sensitive doc set before pointing it at NLYM, Edenic, or GTek material.
8. **Pretext paste/clipboard/status-bar hardening — visible UI test.** In a low-risk terminal or Pretext panel, test setup-code paste/Ctrl+V once and confirm no duplicate input; copy/cut should route cleanly; hidden/minimized panels should report sensible status.
9. **Gee-HQ / Terminal surface sharing — visual routing test.** If Gee-HQ is available, switch Gee targets or remotes and confirm actions route to the selected Gee, not a stale/default target. Keep test read-only.
10. **Outbound thread/attachment routing — draft-only test.** Create a draft or simulated message with an attachment and confirm route metadata/thread identity is correct. Do not send Slack, email, SMS, or Telegram without explicit approval.
11. **MS365 daily scan integration — real workflow test.** Confirm the 8am `morning-calendar-review` and `morning-inbox-summary` include Microsoft 365 account `mariciel@garaygames.com` alongside Google accounts. Good example: check whether Garay Games calendar/mail items appear in tomorrow’s morning scan.
12. **Edenic partner workflow test.** Use the next Edenic partner meeting or release-feedback note to test long-context continuity, task-worker summary discipline, and final-answer separation. Keep any Neil-facing Slack/email as draft-only until approved.
13. **GTek / Garay Games workflow test.** Use Garay Games MS365 mail/calendar as a connector test: summarize recent Garay Games action items from inbox/calendar, flag sensitive client data, and confirm MG recommends switching to `gee-gtek` before client drafting.
14. **NLYM Treasurer workflow test.** Use the Treasurer Manual or invoice-readiness files as a safe read/write test only after backup: confirm docs/handoff continuity, follow-up disposition rules, and no accidental outbound communications.
15. **Tax / finance workflow test.** Use a local non-filing tax or month-end planning artifact to test finance reasoning, file-backed continuity, and model selection. Do not make tax/legal claims without uncertainty and do not alter books/QBO.
16. **Raw-result retrieval / evidence retention.** Run one tool-heavy read/check flow and recover a compacted result to confirm evidence remains available after result-governor compaction.
17. **Gee/T Reports flow — regression check.** Confirm Help > Reports still works and note whether the prior Microsoft 365 duplicate report issue remains.
18. **Event Rules list/preview — PARKED resume trigger: “Let’s create an event rule.”** Create a safe Release Tracker intake rule first, not an autonomous updater. Recommended Version 1: use the installed `local_jsonl` watcher against a local release-intake JSONL file, draft a tracker update + test punch list, and require Mariciel approval before changing files, sending anything, or starting release testing.

---

## Watch Items

- Do not use OutcomeLoops, Event Rules, Bricks, Computer Use, OpenClaw-in-Gee, task-worker delegation, or outbound routing tests on real NLYM/Edenic/GTEK deliverables until sandbox behavior is predictable.
- Treat Base10/BaseTen, Gemma 4 via Cerebras, Sonnet 5 effort tiers, and OpenClaw/Gee-Claw paths as experimental until cost, privacy, and provider behavior are checked.
- Treat “MCPs upgraded,” `0.72.2`, and Gee/T `1.43.5`/`1.43.6` restart requirements as prompts to smoke-test the connectors Mariciel actually uses; do not assume Google Calendar, MS365, Slack, Granola, or Telegram are healthy after a daemon/Gee-T restart.
- Continue using the pinned Gee Test/Core iMessage chat for release intake.
- Keep installer/package testing away from critical work blocks because Neil has repeatedly flagged possible boundary bumps.

---

## Key References

| Resource | Path |
|---|---|
| Release log | `README.md` |
| Tracker repo | `gee-release-tracker/` |
| Source thread | Gee Test/Core iMessage chat |
