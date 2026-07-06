# PROJECT_STATE — Gee Release Tracker

**Last updated:** 2026-07-05
**Status:** Active release-learning log; current through Gee-Code `0.72.3`, Gee/T `1.43.7` Mac / `1.43.8` Windows, GeeHQ `0.7.1`, and experimental GeeHQ `0.8.1` Mac build
**Owner:** Mariciel Georg / MG
**Primary file:** `README.md`

---

## TL;DR

The release tracker is current through Neil’s Gee Test/Core iMessage release note sent **2026-07-05 14:32–14:58 PT** for **Gee-Code `0.72.3` + Gee/T `1.43.7` Mac / `1.43.8` Windows + GeeHQ `0.7.1`**, plus Neil’s experimental **GeeHQ `0.8.1` Mac-only build link**.

Neil called this a “monster update.” The practical headline for MG is that Gee is moving from fixed-provider tool use toward a more adaptive operating layer: **Geenius** can route work to the cheapest capable model by intent, credentials, and feedback; Fable/Hermes are more first-class; token bloat should be lower; capability discovery is unified; repo indexing and symbol edits should reduce code-navigation friction; Bricks/Terminal/HQ are more stable; and Outcome Loops now have stronger leases, approvals, rerouting, and typed actions.

The current action is not broad adoption. Use a supervised test queue focused on Mariciel’s real workflows, while avoiding external sends, client-visible changes, QBO/book mutations, money movement, or destructive edits unless explicitly approved.

---

## Activity This Week

Recent release entries captured in `README.md`:

- 2026-07-05 — Gee-Code `0.72.3` + Gee/T `1.43.7` Mac / `1.43.8` Windows + GeeHQ `0.7.1`; experimental GeeHQ `0.8.1` Mac build link
- 2026-06-30 — Gee-Code `0.72.2` + Gee/T `1.43.5` headline / `1.43.6` detailed version bump release
- 2026-06-27 — Gee-Code `0.72.1` follow-up build
- 2026-06-26 — Gee-Code `0.72.0` + Gee-Terminal `1.43.3` Mac / `1.43.4` Windows release
- 2026-06-25 — Gee-Code `0.71.2` + Gee-Terminal `1.43.1` Mac / `1.43.2` PC release

Local working tree note as of 2026-07-05: `README.md` already contains the v0.72.3 release block from an earlier background/manual scan and remains locally modified/uncommitted.

---

## Current Test Queue

1. **Version / restart check — CURRENT TARGET.** Confirm local Gee-Code `0.72.3`, Gee/T `1.43.7` on Mac, and GeeHQ `0.7.1` after restart/update. Record if any local surface still reports `0.72.2` or older before deeper testing.
2. **Geenius provider routing — safe compare.** Ask one low-risk question with `/model geenius` or semantic model targeting, then confirm the route is reasonable and does not pick a model outside available entitlements. Good MG example: compare which provider should handle code review vs finance review without using sensitive data.
3. **Per-node Dynamic Harness routing — read-only graph.** Run a tiny read-only harness where one node summarizes and one node critiques, then confirm node-level routing works and results remain coherent. Good example: summarize the release tracker README and ask a critic node to identify missing test risks.
4. **Fable aliases — non-sensitive writing test.** Confirm `cc-gee-fable`, `zero`, `high`, and `max` aliases resolve where expected. Good example: draft two versions of a non-client project note and compare quality/cost behavior.
5. **Hermes / Gee MCP wiring — sandbox only.** If Hermes is available, run a read-only tool-surface check and confirm it sees Gee tools with correct identity attribution, not `default`. Avoid NLYM finance/client data until identity and tool boundaries are clear.
6. **Token/result-governor behavior — evidence retention.** Run one tool-heavy read/check flow, let a large result compact, then recover it with `get_tool_result`. Confirm evidence remains retrievable and summaries do not lose important facts.
7. **Capability graph — real MG capability search.** Query whether Gee can do common MG tasks across tools/skills/connectors. Good examples: “read Gmail from both accounts,” “create a calendar event,” “generate a chapter onboarding checklist,” and “search project docs.” Confirm results point to the right primitive.
8. **Promoted workflow skills — repeated-workflow check.** Watch whether repeated MG workflows promote into first-order skills. Good examples: release tracker updates, NLYM punchlist review, and finance-project handoff checks. Do not allow a promoted skill to skip approval boundaries.
9. **Repo index / symbol edits — code navigation test.** Use the persistent index and symbol-level safe edits on a non-sensitive repo first. Good example: locate a function/class in the release tracker or a scratch repo, then make a reversible docs/code edit and run a lint/diff check.
10. **Bricks / Terminal stability — NLYM command center visual check.** Open the NLYM go-live command center and confirm helper processes do not accumulate, ticket panels remain fast, and settings/overview state is correct. Keep this read-only unless Mariciel approves edits.
11. **Outcome Loop approvals and leases — sandbox.** Run one tiny draft-only loop with a parent approval and child task. Confirm lease renewal, durable approval reuse, rerouting on failure, and no repeated approval prompts for the same run.
12. **Report-to-actions flow — gated artifact test.** Use `/loop report --act` on a read-only artifact and confirm proposed actions are typed and gated before mutation. Good example: turn release tracker findings into a draft checklist, not live edits.
13. **Pretext/HQ task-card flow — visible delegation test.** Start a background delegation with `wake_on_user_click` or a visible task-card PIP, then confirm the result returns when clicked and does not get buried in transcript history.
14. **Remote Spaces / redeem-code onboarding — observe only unless needed.** If a remote build target is needed, test the console and redeem-code flow on a non-client environment first. Do not move NLYM/Edenic/GTEK work to remote targets until credential and privacy boundaries are clear.
15. **Person-keyed comms — draft-only routing check.** Confirm cross-channel identity attribution follows the person and no unattributed send path appears. Good example: inspect metadata/draft behavior only; do not send Slack/email/SMS/Telegram without explicit approval.
16. **Google + MS365 connector smoke test.** Re-check the connectors Mariciel actually uses: Gmail/Drive/Calendar account routing, MS365 calendar/mail for Garay Games, and any known Calendar multi-account edge cases. Keep result reporting local unless Mariciel asks to message Neil.
17. **NLYM Treasurer workflow test.** Use file-backed NLYM docs only after backup. Test continuity, punchlist updates, budget-upload readiness notes, and no accidental outbound communications.
18. **Edenic / GTek project workflow test.** Use a non-sensitive partner note or Garay Games MS365 summary to test provider routing, tool discipline, and final-answer separation. Switch to the right Gee/mode before client-facing drafting.
19. **Finance/tax reasoning guardrail test.** Use a non-filing local planning artifact to test model selection and caveat discipline. Do not make tax/legal claims as certainty and do not alter QBO/books.
20. **GeeHQ `0.8.1` experimental Mac build — optional sandbox only.** Treat the link as experimental. Test only when there is time to recover, and keep it away from critical NLYM or client work blocks.

---

## Watch Items

- Treat Geenius/provider routing as powerful but new: confirm cost, entitlement, privacy, and quality before using it on sensitive NLYM, Edenic, GTek, tax, or client workflows.
- Do not use Outcome Loops, Event Rules, Bricks, Computer Use, OpenClaw/Gee-Claw, task-worker delegation, remote agents, or outbound routing tests on real deliverables until sandbox behavior is predictable.
- Keep all outbound tests draft-only unless Mariciel explicitly approves sending.
- Treat experimental GeeHQ `0.8.1` as optional and potentially unstable.
- Continue using the pinned Gee Test/Core iMessage chat for release intake.
- Keep installer/package testing away from critical work blocks because Neil has repeatedly flagged possible boundary bumps.

---

## Key References

| Resource | Path |
|---|---|
| Release log | `README.md` |
| Tracker repo | `gee-release-tracker/` |
| Source thread | Gee Test/Core iMessage chat |
| v0.72.3 source note | Neil Young, Gee Test/Core iMessage, 2026-07-05 14:32 PT |
