# Gee Release Tracker — MG Learning Log

**Purpose:** Running summary of Gee-Code + The Terminal releases, with workflow-specific guidance on what matters most for Edenic, GTEK, and mg mode.
**Source:** Gee-Code Test iMessage chat (Neil)
**Updated:** 2026-06-27 (Captured Neil’s Gee-Code `0.72.1` follow-up build: restart required; fixes daemon autostart crash; adds system skills for deep knowledge compilation and knowledge recall.)

---

## 2026-06-27 — Gee-Code 0.72.1 follow-up build

**Source:** Neil Young, Gee Test/Core iMessage, 2026-06-27 00:01 PT.

**Plain-English summary:** This is a small follow-up build after `0.72.0`. It needs a daemon restart or Gee/T restart to pick up. The release fixes a daemon autostart crash and adds two system skills: `deep-knowledge-compiler` for turning a repo/site/corpus/subject into a knowledge pack, and `knowledge` for recalling that knowledge.

**What changed:**

- **Daemon autostart crash fix.** This should reduce startup/restart brittleness after updating.
- **New knowledge-pack skill.** `/skills deep-knowledge-compiler repo/site/corpus/subject` can create a knowledge pack from a repo, site, corpus, or subject.
- **New knowledge recall skill.** `/skills knowledge` is available as a system skill to recall compiled knowledge.

**Why it matters for MG:**

- Restart behavior matters for scheduled/background reliability, especially after Gee-Code updates.
- The knowledge-pack skills may be useful for larger source-of-truth projects like NLYM Treasurer docs, Edenic partner materials, and release-tracker learning packs, but should be tested on a small non-sensitive corpus first.

**Suggested test queue updates:**

- [ ] Restart daemon or Gee/T and confirm local Gee-Code `0.72.1` is active.
- [ ] Confirm `/skills deep-knowledge-compiler` and `/skills knowledge` are listed as system skills.
- [ ] Run a safe, small knowledge-pack test on a non-sensitive repo or docs folder before using it on NLYM/Edenic material.

---

## 2026-06-26 — Gee-Code 0.72.0 + Gee-Terminal 1.43.3 Mac / 1.43.4 Windows release

**Source:** Neil Young, Gee Test/Core iMessage, 2026-06-26 19:44 PT.

**Plain-English summary:** This release expands Gee from tool-running into more direct environment operation. The main changes are guarded browser/desktop computer use, durable OpenClaw integration inside Gees, better capability-gap handling during work, safer long-running task sessions, faster/cleaner continuity access, more accurate cost reporting, targeted daemon restarts, steadier Claude pipe cache behavior, smoother Terminal UI, better host-surface choices, WebApp reply cleanup, and quieter AgentsPanel logs.

**What changed:**

- **Computer Use Agent landed.** Gee can now operate browsers outside Pretext and desktop apps, with guardrails around risky actions and payments. Neil noted it requires extra packages via `gee-code setup-all`.
- **OpenClaw can live inside Gee.** Claws can now run durably within a Gee, combining Claw execution with Gee memory, policies, tools, and delivery loops.
- **Outcome loops and mode policy got more self-correcting.** Gee detects capability gaps while working and can remediate instead of pretending a tool exists or failing flatly.
- **Task-session reliability improved.** Long-running work should be less prone to breakage, duplicate sends, or premature success claims.
- **Continuity ledger and session history got faster.** Background continuity should stay available without crowding the active prompt.
- **Cost Analyzer is more accurate.** Reporting now handles live partial-day usage, pricing scenarios, and login redirects better.
- **CLI restart targets were added.** Developers can restart specific daemon pieces instead of bouncing the whole system.
- **Claude pipe cache stability improved.** Temporary environment changes should no longer invalidate cached runs unnecessarily.
- **Terminal UI got smoother.** Notepad shortcut, live rename, and nested-list rendering improved.
- **Host-surface preferences improved.** `gee-t open` now chooses the visible Terminal surface when that is the right place to show something.
- **WebApp ledger cleanup landed.** Replies should no longer include internal ledger text.
- **AgentsPanel log noise was reduced.** Streamed logs collapse into cleaner lines.

**Why it matters for MG:**

- Highest relevance: guarded Computer Use testing, OpenClaw-in-Gee architecture, safer OutcomeLoop remediation, and task-session reliability for NLYM/Pay Voucher polish work.
- The continuity-ledger speedups directly support MG’s cross-session operating-partner workflow, especially during heartbeat and project handoff cycles.
- Cost Analyzer accuracy matters for the Edenic pricing and cost-structure work.
- Host-surface preferences and Terminal notepad changes matter because Mariciel is actively using Terminal/Pretext as the working environment.

**Suggested test queue updates:**

- [ ] Run version check and confirm local Gee-Code `0.72.0` + Gee/T `1.43.3` or `1.43.4` availability.
- [ ] Check whether `gee-code setup-all` is needed before testing Computer Use Agent; do not install packages without approval.
- [ ] Run a safe, read-only Computer Use Agent smoke test once approved, avoiding payments, external sends, or account mutation.
- [ ] Inspect OpenClaw-in-Gee docs or registry surface and note a safe future test path.
- [ ] Run one small OutcomeLoop capability-gap test and confirm the remediation is visible and honest.
- [ ] Confirm task-session completion does not duplicate-send or claim success early on the next delegated worker flow.
- [ ] Check Cost Analyzer on a live partial-day usage view and compare against prior assumptions for pricing work.
- [ ] Test Terminal notepad shortcut/live rename/nested-list rendering during a normal work session.

---

## 2026-06-25 — Gee-Code 0.71.2 + Gee-Terminal 1.43.1 Mac / 1.43.2 PC release

**Source:** Neil Young, Gee Test/Core iMessage, 2026-06-25 19:58 PT and 20:01 PT.

**Plain-English summary:** This release is mostly about making Gee’s autonomous work easier to route, reconcile, and trust. The big user-facing themes are actionable Event Rules, safer task/session completion, capability remediation inside OutcomeLoops, richer Slack context, early Teams trigger infrastructure, better pricing/cost measurement through AI cache-hit tracking, cleaner scheduled deliveries, stronger credential scoping, Terminal UI fixes, and report cleanup.

**What changed:**

- **Event Rules now route action, not just record events.** Rules can preview and route “what should happen next,” which matters for the Release Tracker event-rule concept.
- **Task completion and provenance got safer.** Late and terminal graph completions now reconcile/adjudicate instead of silently sticking, and operator-relevant sessions surface first.
- **OutcomeLoops can remediate missing capabilities.** If a loop discovers a missing capability mid-execution, it can trigger remediation instead of failing silently.
- **Slack got a real context upgrade.** Thread sessions, rolling buffer, reactions, presence, and context injection landed across 20 commits.
- **Microsoft Teams trigger foundation landed.** TeamsTriggerListener can auto-spawn per Gee, route @mentions through a durable gateway, and relay replies without manual wiring.
- **Task-session execution context was hardened.** Execution context is isolated, meta-progress is filtered, surface state is suppressed, and concurrent autonomous tasks should bleed context less.
- **AI cache-hit measurement is now visible.** Shared parser across OpenAI-compatible providers surfaces cached-token savings, making model/provider pricing more data-driven.
- **Scheduled deliveries and plan delivery artifacts got safer.** The release dedupes double-sends, carries thread context across scheduled activations, and forces completed plans to produce delivery artifacts.
- **Credentials gained structured envelopes and all-Gees scope.** Credentials can be scoped across all Gees with structured raw-JSON envelopes.
- **Baseten provider behavior improved.** Content streams directly without the reasoning-split heuristic, cache hit rate is measured, and GLM models are priced.
- **Gee-Terminal UI/app updates landed.** Mermaid fallback rendering, slash-command history, inline git sync, browser/panel container refresh, and Apple Silicon installer build improvements were called out.
- **Cross-component fixes landed.** Worker failsafe + GDrive, WebApp nginx + Slack OAuth, BYOP pure-mode baseline tools, and coalescer stream preservation were included.
- **Docs/configuration refreshed.** Configuration reference, models/providers, and companion-gateway docs were refreshed via PRs #180/#181.
- **Reports cleanup improved.** Local report records can now be deleted from the product intake surface.

**Why it matters for MG:**

- Highest relevance: Gee Release Tracker Event Rule design, Slack #geetm context/testing, OutcomeLoop durability, scheduled delivery safety, and pricing/cost work using cache-hit measurement.
- The Teams foundation is worth tracking, but use only in explicit-consent contexts.
- The scheduled-delivery fixes directly touch MG’s heartbeat/scheduled notification rules, especially avoiding duplicate sends.
- The cache-hit measurement ties into the current Gee pricing model: actual cached-token savings can pressure-test the cost assumptions behind fixed fee + activation meter.

**Suggested test queue updates:**

- [ ] Run version check and confirm local Gee-Code `0.71.2` + Gee-Terminal `1.43.1`/`1.43.2` availability.
- [ ] Revisit the Release Tracker Event Rule design and test one safe list/preview route before enabling anything live.
- [ ] Run one tiny OutcomeLoop that intentionally lacks a capability and observe whether remediation is surfaced clearly.
- [ ] Test one Slack thread/context read in a consent-bound workspace/channel.
- [ ] Confirm scheduled delivery dedupe behavior with a harmless dry run or logs-only check.
- [ ] Inspect cache-hit measurement output on a small provider/model test and compare against the pricing model assumptions.
- [ ] Confirm local report deletion in the Gee/T Reports window if there are stale duplicate test reports.

---

## 2026-06-24 — Gee-Code 0.71.1 + Gee/T 1.42.57 Beta release

**Source:** Neil Young, Gee Test/Core iMessage, 2026-06-24 13:57 PT and 14:09 PT.

**Plain-English summary:** This release keeps pushing Gee from “assistant that can run tools” toward a durable operating system for real work. The biggest user-facing changes are safer long sessions, faster outcome loops, inspectable Event Rules, more durable Bricks, more reliable MCP/OAuth startup, a usable Reports window for bug/feature follow-up, Slack restored, upgraded MCPs, and Base10 as a lower-cost high-performance model provider.

**What changed:**

- **Context became a runtime contract.** Prompt sections are tagged, capsules are isolated, parent scopes have journals, Pretext snapshots are scoped, and stale-anchor behavior was hardened.
- **Long sessions are safer under context pressure.** The result governor is on by default, old tool exchanges compact into recoverable ledger pointers, and recovery hints were hardened.
- **Outcome Loops got faster.** Fast-follow child completion, cold-start wakeups, parent wakeups on non-terminal completion, and loop-create hang fixes should reduce “sleepy” autonomous work.
- **Event Rules moved closer to product.** Durable rule management now supports list/get/upsert/remove/preview backed by subscriptions and end-user docs.
- **Bricks share a stronger runtime foundation.** Central runtime handles port assignment, duplicate process cleanup, registry state, health checks, and logs.
- **MCP/OAuth/cold-start reliability improved.** Single-flighted OAuth refresh, surfaced reauth, original launch-env isolation, config repair, and keeping the AI stack off the cold-start path should make MCP clients faster and clearer when they fail.
- **Provider/model surface expanded.** Native Baseten support was added with 32k default context and hidden-reasoning stream support. Neil separately called out Base10/BaseTen GLM5.2 as Opus 4.7–4.8 class at roughly 1/4 the cost.
- **Bug reporting / GTX got more user-safe.** Provisioning self-heals outbound config, avoids leaking internal CLI advice, maps provision errors to useful reasons, clears awaiting-response on reply, and Gee/T now has Help-menu bug/feature reports plus a Reports window.
- **Gee identity and task routing got cleaner.** Active Gee identity is clearer, modes should bleed less, and assigned tickets route through task sessions with fewer stalls/duplicates.
- **Teams became a routed connector.** Microsoft Teams now has a delegated connector path for chats, channels, send, and meetings, flag-gated and consent-bound.
- **Gee/T stability improved.** Custom Gee-Code path handling, Pretext rendering/context, browser/Brick panel durability, report-message threads, installer-click lockout, and autonomy model status-bar sync were all called out.
- **Slack is back fully functional for Gees.** Neil explicitly listed Slack restoration in the follow-up.
- **MCPs have been upgraded.** Neil did not list specifics in the follow-up, so treat as a prompt to smoke-test active MCPs rather than assume all are healthy.

**Why it matters for MG:**

- Highest relevance: Calendar connector escalation via bug reporting/Reports, Granola MCP monitoring, Gee Release Tracker sandbox work, NLYM Pay Voucher support workflows, and any future loop/task demos for Kim Nations.
- The result-governor compaction behavior is already visible in this session, so release-tracker testing should include raw-result retrieval as a normal evidence step.
- Event Rules and Outcome Loops map directly to “Gee does follow-through” demos, especially for Kim’s Claude/vibe-coding ceiling.
- Base10/BaseTen is worth a controlled sandbox test only; do not move user/client work onto it without checking cost, privacy, and provider behavior.

**Suggested test queue updates:**

- [ ] Run version check and confirm local Gee-Code `0.71.1` + Gee/T `1.42.57` availability.
- [ ] Open Gee/T Help Menu > Documentation and confirm it lands on the latest Gee Documentation.
- [ ] File or open one safe test item from the Gee/T Help-menu Reports flow and confirm it appears in the Reports window.
- [ ] Smoke-test Granola MCP after the MCP upgrade note; record whether it still lists meetings.
- [ ] Try one Event Rules list/preview path and note whether it is understandable enough for scheduled-task monitoring.
- [ ] Run one tiny Outcome Loop and confirm fast child completion / parent wakeup behavior.
- [ ] Open a Brick after switching spaces and confirm the blank-webview fix holds.
- [ ] Test Slack read/send capability only in a safe consent-bound context.
- [ ] Compare Base10/BaseTen GLM5.2 in a sandbox against the usual model path for latency, quality, and cost before any real use.
- [ ] Use raw-result retrieval once after a compacted tool exchange to confirm evidence recovery remains usable.

---

## 2026-06-23 — Gee-Code 0.70.15 + Gee/T 1.42.49 Beta hardening release

**Source:** Neil Young, Gee Test/Core iMessage, 2026-06-23 06:43 PT.

**Plain-English summary:** This is a reliability release for the parts of Gee that matter most to Mariciel’s work: durable workflows, Outcome Loops, plan/task context, lane isolation, and tool-result management. The practical goal is less drift, lower token use, cleaner long-running work, and better recovery when something breaks.

**What changed:**

- **Activation-lane context got stronger.** `/org`, `/loop`, and plan execution can now carry parent context better, so a task inside a plan can understand the plan it belongs to.
- **Tool results are lighter.** The Results Envelope/Governor and Tool History Manager can cut model token consumption by up to ~75% by showing compact tool summaries while keeping durable access to raw results. Controls: `/governor on|off` and `/debug history-tool-window 0|1-N`.
- **GLM/ZAI support expanded.** New native/subscription ZAI support, `/model zai`, `/model ZAI-CODE`, plus zero/max reasoning support.
- **Gee File Panel behavior improved.** Gees shown in File Panel > Gee’s now honor activation settings across activation lanes.
- **Core reliability fixes landed.** Neil specifically called out Task System, Outcome Loops, workflows, bug reporting, GTX self-healing, quota exhaustion protection, Pretext pipe protections, native REPL revamp, prompt tagging, updater messaging, Brick stability, Brick server port assignment, Deepseek/ZAI reasoning threads, and MCP launch reliability for the single installer.

**Why it matters for MG:**

- Highest relevance: Outcome Loops, TaskGraph/plan execution, heartbeat/scheduled workflow reliability, Bricks, GTX bug-report submission, and tool-result compaction.
- This directly affects the current Gee learning/test queue and the Release Tracker sandbox loop idea.
- Also relevant to the recent GTX outbound-mailbox blocker and MS365 connector feedback because bug reporting and GTX self-healing were named in the fix list.

**Suggested test queue updates:**

- [ ] Run version check and confirm local Gee-Code `0.70.15` + Gee/T `1.42.49` availability.
- [ ] Test one tiny Outcome Loop using the Gee Release Tracker sandbox and confirm context parenting + clean stop behavior.
- [ ] Turn the governor on, run a tool-heavy read/check flow, then use raw-result retrieval to confirm compact summaries do not hide needed evidence.
- [ ] Re-test Bug Report / GTX submission flow after update; see whether self-healing or clearer mailbox guidance appears.
- [ ] Open NLYM Go-Live Command Center Brick and confirm Brick server/port stability.
- [ ] Try one small TaskGraph/plan execution and confirm child tasks inherit plan context clearly.

---

## Mariciel Test Queue — Current Release

**Current focus:** Neil’s Jun 18/19 “Huge New Release” note: outcome loops, org/container substrate, scalable task queues, MS365 connector, Windows support, Operations panel, realtime voice/context upgrades, and the single DMG/EXE installer path. Local Gee-Code was confirmed via `/version` on 2026-06-19 as `0.70.5` + “You're up to date,” so treat this as a Beta-channel readiness/test-planning item until an updater-visible version appears.
**Purpose:** Pull only the release actions that matter to Mariciel into one working checklist.

### Must test now
- [x] **Confirm current local Gee-Code version.** `/version` on 2026-06-19 shows Gee-Code `0.70.5` + “You're up to date.” Keep watching for the updater-visible Beta build Neil referenced.
- [ ] **Do not upgrade during a critical work block.** Neil explicitly asked for issue reports because the release moves from component installer to a single DMG/EXE bundle. Test the installer only in a low-risk window.
- [ ] **Sandbox-test Outcome Loops before real work.** Use a harmless goal with clear success criteria; confirm Gee records evidence, stops cleanly, and escalates instead of drifting.
- [ ] **Test visible TaskGraph/DynamicHarness progress.** Run one small graph you can watch in Pretext; verify progress, failure state, and final synthesis are understandable.
- [ ] **Inspect Org/Container task isolation.** Confirm delegated/task-session worktrees do not collide with the active repo before trusting parallel work.
- [ ] **Open Operations panel.** Confirm event-driver health cards are understandable enough for MG scheduled tasks and heartbeat monitoring.
- [ ] **Treat MS365 connector as future-client surface.** Useful for Outlook/Microsoft users, but not an immediate NLYM priority unless Workspace strategy changes.
- [x] **Confirm Gee-Code 0.70.0 baseline.** `/version` showed Gee-Code `0.70.0` and “You're up to date” earlier on 2026-06-09.
- [x] **Confirm current Gee-Code version.** `/version` on 2026-06-12 shows `0.70.5` + “You're up to date.” Past the `0.70.3` announcement. `0.70.4`–`0.70.5` are unannounced point releases (nothing posted in Gee Test (Core)), so no specific new features to test from them — likely minor fixes.
- [ ] **Test Exa agentic web-search.** Run one current-fact research query that should benefit from Exa, compare against the normal search path, and note source quality/latency.
- [ ] **Try Fable on a gee (sandbox only).** Fable support shipped in `0.70.2` and you're on `0.70.5`, so the aliases should resolve. To use: model picker → `custom` → `cc-gee-fable` (effort tiers: `cc-gee-fable-zero` / `-medium` / `-high` / `-xhigh` / `-max`). Old `fable-low` is now `fable-zero`. Direct-API equivalent: `claude-fable-5` (aliases `fable`, `claude-fable`, tiers `fable-zero`…`fable-max`).
- [ ] **Note Fable cost before use.** Treat Fable as a premium model path: Neil said it bills at 2x Opus 4.8, so use only for a small sandbox comparison unless there is a clear reason.
- [ ] **Check new documentation updates.** Use `/version browse` or the bundled docs path to confirm the new Exa/Fable docs material is discoverable and understandable.
- [ ] **Confirm Gee/T + iOS Beta versions.** Verify Gee/T shows `1.41.0` on Mac or `1.42.0` on Windows; iOS app is build/version `0.31`.
- [ ] **Test iOS 0.31 fixes.** On iOS, check iOS 27 compatibility, link rendering, web click-throughs, and keyboard behavior.
- [ ] **Try one Loop in a sandbox.** Use a low-stakes “watch/research until done or blocked” goal to see whether Loops hold success criteria and stop cleanly.
- [x] **Run one TaskGraph/Dynamic Harness visibly in Pretext.** Completed a live Dynamic Harness demo on the NLYM KB review flow; second pass completed cleanly and showed the DAG/orchestration mechanics.
- [ ] **Inspect Tasks substrate behavior.** Check that queued/delegated work has clear tickets, evidence, leases, and closure state before relying on it for client work.
- [ ] **Spot-check install/productization paths.** Note the single DMG/EXE and Windows beta progress as beta-program readiness signals, not production rollout proof yet.

### Keep in mind
- Plain-English takeaway: Gee is moving from “answer this request” toward “own this outcome until done, blocked, or escalated.” That is powerful, but it raises the bar for evidence, stop conditions, and approval gates.
- `0.70.1`–`0.70.3` are same-day follow-ups on top of the large `0.70.0` autonomy/substrate release: keep the Loops/Tasks caution, but add Exa search, Fable alias, Fable cost, and docs checks now.
- iOS `0.31` is specifically about mobile polish: iOS 27 fixes, link rendering, web click-throughs, and keyboard behavior.
- Best first test is still a sandbox workflow. Do not use a real client/NLYM/Edenic/GTEK deliverable until task closure, approval gates, and visible state feel predictable.

---

## Release Index

| Version | Date | Impact | Theme |
|---|---|---|---|
| [Gee-Code 0.71.1 + Gee/T 1.42.57 Beta](#2026-06-24--gee-code-0711--geet-14257-beta-release) | Jun 24, 2026 (~1:57 PM PT + follow-up 2:09 PM PT) | 🔴 High | Context runtime contract, safer long sessions/result-governor defaults, faster Outcome Loops, Event Rules productization, Brick runtime hardening, MCP/OAuth reliability, Teams routed connector, Reports UI, Slack restored, upgraded MCPs, and Base10/BaseTen provider coverage. |
| [Gee Beta — Outcome Loops, Org/Containers, Scalable Tasks, MS365, Windows, Single Installer](#v070x-big-beta) | Jun 18, 2026 (~10:14 PM PT) | 🔴 High | Major substrate/productization release: **outcome loops**, **org/container systems**, **scalable ticket-backed task queue**, **MS365 connector**, **Windows support**, **single DMG/EXE install path**, live TaskGraph progress, Operations panel, Telegram/group routing, realtime voice upgrades, and release-pipeline hardening. |
| [Gee/T 1.42.5 Beta](#gt1425) | Jun 12, 2026 (~5:48 PM PT) | 🟡 Medium | Beta bug-fix build from Neil: crash + attachment fixes, including side-tab addition crash and iOS photo-send repair. |
| [Gee-Code 0.70.1–0.70.3 + iOS App 0.31](#v0701) | Jun 9, 2026 (~10:35 AM PT–3:27 PM PT) | 🟡 Medium | Same-day follow-ups: **Exa agentic web-search**, Fable model aliases + rename to `fable-zero`, documentation updates, and iOS 0.31 polish. |
| [Gee-Code 0.70.0 + Gee/T 1.41.0 Mac / 1.42.0 Windows + iOS App (30)](#v0700) | Jun 8, 2026 (~11:42 PM PT) | 🔴 High | **Loops Alpha**, **Task Substrate**, TaskGraph + DynamicHarness orchestration, visible Pretext/Mermaid DAGs, single DMG/EXE packaging path, Windows beta end-to-end, iOS App 30, and broad task/delegation/ticket hardening. |
| [Gee-Code 0.69.0 + Gee/T 1.40.0](#v0690) | Jun 3, 2026 (~10:33 PM PT) | 🔴 High | **Prompt/capability doctrine**, **Organization substrate promotion**, multiplex **Task sessions**, TaskGraph + DynamicHarness orchestration, Commitments → tickets, Pretext canvas polish, sandbox/credential hardening, access-policy guardrails, Windows hardening, daemon/delivery proof, per-user prime routing, and in-window Cost Analyzer. |
| [Gee-Code 0.68.x + Gee/T 1.39.x + Windows 1.39.x](#v068x) | Jun 1, 2026 (~9:34 PM PT) | 🔴 High | **Organization substrate** (`/init organization`, governed source edges, evidence capture, workflow brains, approval-gated promotion), durable **Action commitments**, ticket/delivery integrity, gateway delivery proof, sandboxed execution, OpenClaw/Codex hardening, quieter autonomy, channel-aware release/update, Windows lane fixes, JSONL previews + Pretext polish, agent-aware docs (`gee.edenic.ai`, bundled `gee-docs` skill/CLI hints), Telegram local-file attachments, connector/pipe/org-route hardening. |
| [Gee-Code 0.67.0 + Gee/T 1.37.0 (Mac) / 1.38.0 (PC)](#v0670) | May 30, 2026 (~4:45 PM PT) | 🔴 High | **Multi-channel deployments** (Dev / Beta / Stable update channels — manual opt-in to Beta required), **Configuration Management** feature, **app renamed back to Gee/T** (the-terminal Dock icons go to '?', re-pin from Applications), dark-blue first-launch screen while intro precaches. Same-day PSAs: Opus 4.8 + Claude Code burns Max weekly limit in ~2.5 days; next release defaults `cc-gee-max` to Opus 4.8 — use `cc-gee-high`/`xhigh` to limit. Detailed HTML release notes pending from Neil. |
| [Gee-Code 0.66.3+0.66.5 + Gee/T 1.36.3/1.36.4](#v0663) | May 27, 2026 (~6:30 PM PT) | 🔴 High | **Message Adjudication Gate** (pre-send, source-of-truth contract), Synthesis/Delivery hardening (8 interlocking fixes), **Unified Attachment Substrate** (one AttachmentRef across REPL/web/Pretext/daemon/clipboard/pipe), **Ticket Email + Voice activations**, multi-provider compat (OpenRouter, Cursor agent), MCP identity isolation, Windows PATH fix. Gee/T 1.36.3/1.36.4: Inline Mermaid, Remote Pretext MCP bridge, X OAuth wizard, **Self-Healing Updater** (auto-repairs stale MCP entries). v0.66.5 = two PC quick fixes pushed same night. |
| [Gee-Code 0.66.0 + Gee/T 1.36.1](#v0660) | May 26, 2026 (~9:17 PM PT) | 🔴 High | **Outbound integrity (trigger lane)** — pre-send adjudication using ticket adjudicator, narration-detector, drop-proof synthesis fallback. **Scheduled-lane delivery proof** — scheduled sends ship model's real body (not narration), require outbox proof. **heartbeat_gather_state wired into routing**. New **lossless capture substrate** + activity-review policy. **Activity-wake watcher**. Cost tagging Phase B1+B2 (voice + embeddings). Watchdog no longer kills healthy long triggers. Gee/T 1.36.1: inline mermaid + SVG persistence + connector auto-repair. |
| [Gee-Code 0.65.0 + Gee/T 1.36.0](#v0650) | May 23, 2026 (~2:09 PM PT) | 🔴 High | **X (Twitter) OAuth lands** (accounts, pagination, bookmarks, lists), Slack user-token outbound + SlackRead tools, **model-backed triage default-on**, daemon forced mode-drop reload, Telegram rewrites markdown tables (can't render), **scheduled activations actually deliver final response**, MCP creates GEE_OUTPUT_DIR. Gee/T 1.36.0: **Remote Pretext MCP bridge** (terminals mount remote Pretext sessions; remote session drives local PIPs). Follow-up patch May 24: Telegram delivery interim-text heuristic removed, delegation callback backstops. |
| [Gee-Code 0.64.4 + Gee/T 1.35.3](#v0644) | May 22, 2026 (~12:37 PM PT) | 🔴 High | **user-email attachments as GeeConnect action** (stage bytes to disk, LLM never sees base64), **scheduled delivery channels honored end-to-end** (delivery_channel threads daemon→runner→send_notification with identity-policy + monologue gate), preempt gate trusts inbound origin not delivery targets, Telegram stream resets per SendMessage (no glued-in history), triage parses "delegate this to X", `respond_to_request` joins PURE_AUTONOMOUS_TOOLS, Codex image argv under cap (stage to disk), platform-ops routing narrowed to creation only. |
| [Gee-Code 0.64.3 + Gee/T 1.35.1](#v0643) | May 20, 2026 (~11:30 PM PT) | 🔴 High | **Email sending on behalf of user re-enabled** (with hard guardrails + account exclusions), **LLM-driven delegation**, Slack User Scopes (Gee sees Slack like you), new reference implementations for creating a Gee / building a Brick / setting up Events, Farshid's Cost Analyzer inclusions, remote deployment polish + RunBook in Essential Docs, WIP Twitter OAuth connector. |
| [Gee-Code 0.64.2](#v0642) | May 20, 2026 (~3:24 PM PT) | 🟡 Medium | Slack semantic outbound route resolution, `SendMessage` gee-identity enforcement fix, **Cursor cloud default → composer-2.5** (surfaces in Gee/T pickers; Neil notes "very cheap" and encouraging in personal tests). |
| [Gee-Code 0.64.0 + Gee/T 1.35.0](#v0640) | May 19, 2026 (night) | 🔴 High | **Remote Deployments** — Gee-Code can run as a standalone cloud instance (EC2, etc.) and Gee/T connects over SSH as if local. One-click deploy, SSH tunnel management, Pretext Panel remote connect, cloud credential preservation, OAuth on remote. Slack scopes fix, dup credential fix, ticket dispatch fallback-to-API fix for entitled users. |
| [Gee-Code 0.63.2](#v0632) | May 19, 2026 (mid-day) | 🟡 Medium | **Task* MCP tools** for cross-REPL planning parity (1st-class Task Planning across all REPLs/providers). WIP remote Gee-Code (EC2) prep, better vision for Codex (native `-i`), new XAI aliases (xai-zero, tai, tai-max + reasoning tiers for grok-4.3), ai_pacing tone hardened against doom/gloom, GPT image timeout bump. Deployment-prep release. |
| [Gee-Code 0.63.1 + Gee/T 1.34.1](#v0631) | May 18, 2026 (night) | 🔴 High | **Ticket assignment control plane** (Pending filter, provenance, caps, scope/trusted-assigners), **short↔long ops unified on tickets**, **messaging tokens in Credentials Vault**, **Realtime Voice as own entitlement** + Live Voice Strip, **Brick supervisor on boot** |
| [GeeCode 0.63.0 + Gee/T 1.34.0](#v0630) | May 17, 2026 (AM) | 🔴 High | **Bricks-owned Bug/Feature intake via GTX**, **Realtime Voice preview** in Pretext, inbound phone improvements (car/transfer), long-running ticket lifecycle fixes (no phantom activations / phantom attachments) — 114 commits |
| [GeeCode 1.33.3 + Gee/T 1.62.0](#v1333) | May 12, 2026 (night) | 🔴 High | Long-running tickets adjudicated through completion, **BYOK in Credentials Vault**, new Gee Wizard, OpenClaw robustification, stable panel restoration |
| [GeeCode + Gee/T patch](#v0610-patch) | May 11, 2026 (night) | 🟡 Medium | Ticketing regression fix; Gee/T spaces disconnect/reconnect fix |
| [Gee-Code v0.61.0 + Terminal v1.33.1 + iOS Pretext](#v0610) | May 9-10, 2026 | 🔴 High | Managed-model entitlements, Discord first-class, CLI marketplace, Bricks 0.5/0.6, outbound voice GA, delegation lifecycle reliability |
| [Gee-Code v0.60.2 + Terminal v1.32.1](#v0602) | May 7, 2026 | 🟡 Medium | Reliability follow-up: ticket delivery hardening, per-gee bot tokens, CLI registry, iOS share fix |
| [Gee-Code v0.60.0 + Terminal v1.32.0 + iOS 27](#v0600) | May 5, 2026 | 🔴 High | Ticket-aware execution end-to-end, Slack per-gee identities, outbound phone work ticketable, mobile final-reply push, OpenAI Responses recovery |
| [Gee-Code v0.59.0 + Terminal v1.31.0 + iOS 0.26](#v0590) | May 3, 2026 | 🔴 High | Durable Events System, Tickets/Intake, Mobile Pretext Alpha, xAI voice, semantic cloud search |
| [Gee-Code v0.58.0 + Terminal v1.30.0](#v0580) | Apr 30, 2026 | 🔴 High | Connector plugin framework, Slack inbound, Cloud file browser, Cursor SDK |
| [Gee-Code v0.57.0 + Terminal v1.29.0](#v0570) | Apr 28, 2026 | 🔴 High | Credentials Vault, Gee-tab refactor, Custom Panels/Dashboard, DXF/CAD |
| [Gee-Code v0.56.0 + Terminal v1.28.0](#v0560) | Apr 27, 2026 | 🔴 High | OpenClaw, REPL tiers, Voice calls |
| [Gee-Code v0.55.2 + Terminal v1.27.1](#v0552) | Apr 26, 2026 | 🟡 Medium | /repl gpi, bug fixes |
| [Gee-Code v0.55.1](#v0551) | Apr 25, 2026 | 🟢 Passive | Telegram fix, Google Sheets/Docs/Slides updates |
| [Gee-Code v0.55.0](#v0550) | Apr 25, 2026 | 🔴 High | Objective escalation, model surface, voice routing |
| [Gee-Code v0.54.2 + Terminal v1.26.2](#v0542) | Apr 23, 2026 | 🟢 Passive | GPT-5.5 aliases, Pretext polish |
| [Gee-Code v0.54.1](#v0541) | Apr 23, 2026 | 🟢 Passive | Bug fixes, Telegram fix |
| [Gee-Code v0.54.0](#v0540) | Apr 22, 2026 | 🟡 Medium | Delegation, Skills system, House voice |

---

<a name="v070x-big-beta"></a>
## Gee Beta — Outcome Loops, Org/Containers, Scalable Tasks, MS365, Windows, Single Installer (Jun 18, 2026 ~10:14 PM PT)

**Posted:** Neil, Gee Test (Core), Jun 18 ~10:14 PM PT. Reviewed again by MG on Jun 19 after Mariciel asked for a plain-English test queue.
**Impact:** 🔴 High — this is a substrate and packaging shift, not a small feature release.

**Neil summary:** “Huge New Release” with 127 commits. Neil highlighted generalized workflow systems (`/org` and `/container`), outcome loops, a scalable task system on tickets, cross-platform Mac/PC support, and a single installer bundle. He also noted the new version is on the Beta Channel and asked testers to report issues because the move from component installer to single install bundle may have boundary bumps.

### 🎯 Most Impactful For Mariciel

**Outcome Loops are the headline, but they need sandbox testing first.** Gee can now hold an objective, queue work, inspect evidence, verify progress, and continue until done, blocked, or escalated. That is powerful for long-horizon work, but it should be tested on low-risk goals before touching NLYM/Edenic/GTEK deliverables.

**Org + Container systems make parallel work more real.** Task sessions and delegation workers run in isolated git-worktree containers, backed by durable task queues and leases. This should reduce collisions, but the first few real uses should be watched closely.

**Single installer + Windows support are the adoption story.** Gee is moving toward normal install UX: one DMG for Mac, one EXE for Windows. This matters for broader beta users, but installer transitions are high-risk enough to avoid upgrading during critical work.

### What Changed

| Area | What changed | Why Mariciel cares |
|---|---|---|
| Outcome Loop system | Durable loops can hold goals, success criteria, evidence, next actions, and continue across turns/restarts until done, blocked, or escalated. `/loop report --act` can let a loop fire follow-up actions with gates. | Closest thing yet to Gee owning a real outcome, but should start with harmless sandbox objectives. |
| Org substrate + containers | `org_*` tooling, `/org` parity, containerized task-session/delegation worktrees, durable task queue, leases, and scheduler concurrency knobs. | Safer parallel work and more scalable delegation; inspect worktree behavior before trusting it with client repos. |
| Scalable task system | Ticket-backed task queue can scale horizontally to many agent instances. | Gee becomes compute/token-bound more than time-slice-bound; useful later for large review/build work. |
| MS365 connector | Server-side Microsoft 365 connector for mail, calendar, and files with OAuth in Terminal. | Microsoft/Outlook users become first-class. Not immediate for NLYM Workspace, but useful for broader client contexts. |
| Windows support | Windows process lifecycle, daemon survival, UTF-8 config/registry I/O, Windows smoke CI, BYOP credential prompt fix. | Gee is no longer Mac-only in practice; helpful for broader beta and non-Mac stakeholders. |
| Single DMG / EXE install | Terminal app and gee-code engine bundled into one platform installer with checksums and install scripts. | Major productization win, but also the risk Neil explicitly flagged for testing. |
| DynamicHarness + TaskGraph | Pattern compiler matured with true loops, harness-in-harness, sequence composition, architect-designed graphs, and live colored DAG progress in Pretext. | Best supervised testing surface because the workflow is visible. |
| Operations panel | Events rebranded as Operations with health cards and in-app event-driver creation UI. | Makes background automation easier to inspect. |
| Telegram/channel upgrades | Group routing, collective gee addressing, smarter human/gee/bot routing, and channel-session continuity fix. | Reduces lost context in group/channel workflows. |
| Realtime voice | Voice activation across Gee/T; screenshots and DOM scene capture feed voice sessions by default. | Improves voice/session context, but needs privacy-aware testing. |

### ⚠️ Caution

- **Do not upgrade mid-critical work.** Installer/package transition is the likely rough edge.
- **Do not use Outcome Loops on NLYM/Edenic/GTEK deliverables first.** Start with a sandbox goal and inspect evidence/closure behavior.
- **Watch task isolation.** Containers/worktrees are designed to prevent collisions, but first use should be supervised.
- **MS365 connector is new surface area.** Treat account permissions and outbound behavior carefully.

### ✅ To Explore

- [ ] Run `/version` and confirm exact local Gee-Code + Gee/T versions and Beta availability.
- [ ] If upgrading, do it during a low-risk window and note whether the single DMG path replaces the old component installer cleanly.
- [ ] Run one visible TaskGraph/DynamicHarness task and inspect live DAG progress.
- [ ] Run one tiny Outcome Loop with harmless success criteria; confirm it stops cleanly.
- [ ] Inspect a containerized task/delegation worktree and confirm repo isolation.
- [ ] Open Operations panel and confirm event-driver health cards are understandable.

---

<a name="gt1425"></a>
## Gee/T 1.42.5 Beta — crash + attachment fixes (Jun 12, 2026 ~5:48 PM PT)

**Posted:** Neil, Gee Test (Core), Jun 12 ~5:48 PM PT.  
**Impact:** 🟡 Medium — beta stability + attachment-flow fixes; useful if testing side tabs, iOS image sending, or agent attachment workflows.

**Neil summary:** "new beta 1.42.5. mostly fixing a few bugs that were introduced. Side tab adding was crashing, photo send from iOS was broken, agent attachments were dropping a variable name."

**What changed:**
- Fixed side-tab adding crash in Gee/T beta.
- Fixed broken photo send from iOS.
- Fixed agent attachments dropping a variable name.

**MG take:** Treat this as a targeted Gee/T beta repair build, not a broader Gee-Code release. No mg workflow change needed unless Mariciel hits side-tab, iOS photo-send, or attachment regressions.

---

<a name="v0701"></a>
## Gee-Code 0.70.1–0.70.3 + iOS App 0.31 — Exa Search, Fable Aliases, Docs, iOS Polish (Jun 9, 2026 ~10:35 AM–3:27 PM PT)

**Posted:** Neil, Gee Test (Core), Jun 9 ~10:34 AM–3:27 PM PT.
**Impact level:** 🟡 Medium

### Summary
Neil posted same-day follow-ups after the `0.70.0` autonomy release: iOS Build `0.31` fixes iOS 27 compatibility, link rendering, web click-throughs, and keyboard behavior; Gee-Code `0.70.1` adds Exa agentic web-search and documentation updates; `0.70.2` adds Fable support with native Anthropic API aliases and Claude Code aliases; `0.70.3` renames `fable-low` / `cc-gee-fable-low` to `fable-zero` / `cc-gee-fable-zero`. Neil also noted Fable is billed at 2x Opus 4.8.

### 🎯 Most Impactful For You

**Exa search is the main desktop learning target.** Test it on a contained current-fact research task and compare the answer quality, source traceability, and speed against the existing search path before relying on it for partner/client research.

**Fable is a small sandbox-only test for now.** The aliases matter because they signal native support, but the 2x Opus 4.8 cost note means do not casually route normal work through it.

**iOS 0.31 is the mobile confidence check.** Since the fixes touch links, click-throughs, and keyboard behavior, test the exact flows you use when reviewing Gee updates from your phone.

### What Changed

| Area | What changed | Why Mariciel cares |
|---|---|---|
| Exa agentic web-search | New web-search path in Gee-Code `0.70.1`. | Potentially better research quality for live/company/product lookups; needs source-quality spot check. |
| Documentation | Docs updated alongside the Exa/Fable releases. | Good chance to practice finding feature docs through `/version browse` or bundled docs rather than relying on Neil's chat. |
| Fable support | Native Anthropic API aliases and Claude Code aliases added in `0.70.2`; renamed in `0.70.3` from `fable-low` to `fable-zero`. | Useful to know for model-routing tests, but expensive enough to keep sandboxed. |
| Fable billing | Neil noted Fable is billed at 2x Opus 4.8. | Prevents accidental high-cost testing while Mariciel is still learning model/cost behavior. |
| iOS App 0.31 | Fixes for iOS 27, link rendering, web click-throughs, and keyboard behavior. | Directly affects mobile Pretext/review workflows and whether phone-side testing feels reliable. |

### ✅ To Explore

- [ ] Run `/version` and confirm whether local Gee-Code sees `0.70.3`.
- [ ] Try one Exa-backed current-fact search and compare it with the normal search path.
- [ ] Confirm `fable-zero` / `cc-gee-fable-zero` aliases are present; do not use old `fable-low` naming.
- [ ] Run at most one tiny Fable sandbox comparison and note whether the quality justifies the 2x Opus 4.8 billing.
- [ ] Open the updated docs/release notes and confirm where Exa/Fable guidance lives.
- [ ] On iOS 0.31, test link rendering, web click-through, and keyboard behavior.

---

<a name="v0700"></a>
## 🚀 Gee-Code 0.70.0 + Gee/T 1.41.0 Mac / 1.42.0 Windows + iOS App (30) — Loops, Task Substrate, TaskGraph, Dynamic Harnesses, Packaging (Jun 8, 2026 ~11:42 PM PT)

**Requires:** Beta selected for Gee-Code and Gee/T. After changing channels, fully restart Gee/T and restart daemons. Windows beta path is now much more complete, but treat it as beta-quality.

### Summary
Neil announced a major autonomy and productization release: Gee-Code `0.70.0`, Gee/T `1.41.0` on Mac, Gee/T `1.42.0` on Windows, and iOS App `30`, available on Beta channels. The core shift is from single-session execution toward durable, visible, parallel work: Loops for long-running outcome ownership, a ticket-backed Task Substrate for scalable work units, TaskGraph/Dynamic Harnesses for structured orchestration, and Pretext/Mermaid visibility so workflows are watchable instead of hidden.

### 🎯 Most Impactful

**TaskGraph + Dynamic Harnesses are the immediate Mariciel win.** They make complex work easier to trust: research branches, implementation/verification stages, debates, tournaments, and fan-out synthesis can run as visible DAGs in Pretext instead of buried agent work. This is the best sandbox to test before using Loops or high-volume Tasks for real NLYM/Edenic/GTEK workflows.

### What's New

| Area | What changed | Why Mariciel cares |
|---|---|---|
| Loops system (Alpha) | Durable autonomy loops can hold goals, success criteria, evidence, next actions, and continue until done, blocked, or needing human judgment. | Moves Gee closer to owning outcomes like “watch this issue until fixed” or “keep improving this spec nightly.” Start with sandbox loops only. |
| Task Substrate | Ticket-backed, lease-aware work units can be queued, delegated, resumed, checked, and closed with evidence. | Foundation for parallel worker-style execution and safer long-running operations. Important for scale, but needs closure/approval spot-checking. |
| TaskGraph | REPL-native DAG workflows with visible dependency maps, branching, parallel work, and fan-in synthesis. Presets include fan-out synthesis, debate, tournament, iterate-until-verified, and sequence. | Best immediate feature to test: visible structure makes multi-step AI work easier to supervise. |
| Dynamic Harnesses | Gee can choose and compose TaskGraph patterns automatically based on task shape. | Less need to pick an orchestration pattern manually; prompts like “compare approaches” or “iterate until this passes” can map to the right workflow. |
| Pretext DAG / Mermaid visibility | Inline Mermaid rendering and live DAG substrate support landed in Terminal/Pretext. | Workflow execution becomes inspectable in the UI, which is key for trust and learning. |
| Single DMG / EXE install path | First real packaging path for macOS and Windows, bundling app/runtime pieces toward a normal install experience. | Big Friends & Family beta signal: less “developer setup required” over time. |
| Windows beta end-to-end | Windows can install, launch, resolve dependencies, run Gee-Code, and support core Pretext/Terminal/background paths. | Windows is becoming a real supported surface, useful for broader beta users. |
| iOS App (30) | New mobile version described as more functional and focused. | Worth testing once the desktop beta path is stable. |
| Hardening | Task-session isolation, delegation/worker hardening, ticket hygiene, curated test gates, PR CI, Windows-safe process/config handling, OpenClaw/ACP/MCP cleanup, prompt/channel-etiquette updates. | Reduces substrate fragility, but this release touches many core systems at once. Test in small loops. |

### New Commands / Surfaces

- `TaskGraph` tool / REPL workflow presets: fan-out synthesis, debate, tournament, iterate-until-verified, sequence.
- `DynamicHarness` composition layer for auto-selecting and nesting workflow patterns.
- Tasks workspace and navigation surfaces for ticket-backed task state.
- Inline Mermaid/DAG visualization in Pretext.
- Single DMG / EXE packaging path and release-console wiring.

### ⚠️ Caution

- **Loops are alpha.** Use sandbox goals first; confirm they stop cleanly and ask for judgment at the right time.
- **Substrate-heavy release.** Tasks, tickets, delegation, Pretext, Terminal packaging, Windows, and iOS all moved. Expect rough edges.
- **Do not start with client deliverables.** First test with non-critical workflows, then graduate to NLYM/Edenic/GTEK once evidence, closure, and approval behavior are clear.
- **Windows is beta-quality.** Big milestone, not a promise that every user environment is clean yet.

### ✅ To Explore

- [ ] Run one visible TaskGraph fan-out synthesis in Pretext and confirm the DAG is readable.
- [ ] Try one Dynamic Harness prompt: “compare these approaches and recommend the best one.”
- [ ] Start one tiny Loop with explicit success criteria and verify it ends as done/blocked/needs-human rather than drifting.
- [ ] Inspect a Task-backed workflow for ticket evidence, lease/ownership state, and closure notes.
- [ ] Test the iOS build 30 path after desktop beta is stable.
- [ ] Track whether single DMG/EXE packaging changes the Friends & Family beta onboarding plan.

---

<a name="v0690"></a>
## 🚀 Gee-Code 0.69.0 + Gee/T 1.40.0 — Prompt Doctrine, Org Substrate, Multiplex Tasks, TaskGraph/DynamicHarness (Jun 3, 2026 ~10:33 PM PT)

**Requires:** Beta selected for both the Gee/T app and Gee-Code builds. After changing channels, fully restart Gee/T and restart daemons; `/channel` should report `beta`, not `legacy`.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), Jun 3 ~10:33 PM PT (Gee-Code 0.69.0 + Gee/T 1.40.0). Neil followed up Jun 4 ~8:01 AM PT: make sure both Gee/T app and Gee-Code are set to Beta, then restart Gee/T and daemons.

### Summary
This is a major platform-hardening and orchestration release. The headline: Gee gets stronger capability-use doctrine, organization substrate promotion, unlimited simultaneous ticket-backed Task sessions, TaskGraph + DynamicHarness orchestration, commitment capture as follow-up tickets, Pretext canvas improvements, sandbox/credential hardening, per-user routing, and more delivery-proof guardrails.

### 🎯 Most Impactful For You

1. **Multiplex Task sessions** ⭐⭐⭐ — This is the practical “software factory” unlock: multiple simultaneous tasks with scheduler control and concurrency limits. Useful for parallel QA/build/research, but should be tried on bounded work first.
2. **TaskGraph + DynamicHarness** ⭐⭐⭐ — Workflow has been renamed/evolved into a self-planning orchestration layer with fan-in result threading and Mermaid output. Good candidate for multi-step NLYM Pay Voucher QA/build flows once stable.
3. **Commitments → tickets** ⭐⭐⭐ — Promises and follow-ups are now captured end-to-end as tickets. This directly supports MG’s loop-closing role, but watch for duplicate/stale commitments during the first few days.
4. **Organization substrate promotion** ⭐⭐ — Native onboarding tools and BYOP-aware org skill make `/init organization` more real. Still test on a narrow docs surface before broad Edenic/NLYM use.
5. **Sandbox + credential hardening** ⭐⭐ — Terminal fallback for missing keys and sandboxed execution improve safety, but artifact/output paths should be watched after the upgrade.
6. **Access policy + outbound guardrails** ⭐⭐ — Per-user Slack policy, per-gee inbound policies, and outbound `never_do` scoping are directly relevant to email/Slack guardrail audits.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Prompts Upgrade** | Capability-use doctrine, house-voice authority, harness-first substrate model, bundled-skills for org substrate. | Should improve tool choice and reduce model-jargon drift. |
| **Organization substrate** | Org driver promoted; native onboarding tools; BYOP-aware org skill; six-step CLI; init-organization route. | Makes org-aware Gee setup more operational, but still needs bounded testing. |
| **Multiplex Task sessions** | Unlimited simultaneous scheduled tasks with scheduler control plane, concurrency limits, ticket-backed ownership, and Terminal Tasks view. | Enables real parallel execution instead of one sequential work lane. |
| **TaskGraph + DynamicHarness** | Workflow → TaskGraph; DynamicHarness can self-plan/compose; caller-model inheritance; fan-in result threading; Mermaid output. | Better orchestration for multi-step build/research/QA work. |
| **Commitments → tickets** | RecordCommitment/RecordPromise, strict-schema extraction, success contracts, continuation preservation. | Promises should resume cleanly instead of being dropped or duplicated. |
| **Pretext canvas** | Zoomable/pannable Mermaid, slash suggestions, exact clipboard, PIP thumbnail/preview sizing, jsonl preview, faster first tab. | Better visible planning/debugging surface in The Terminal. |
| **Credentials & sandbox** | Terminal-prompt fallback for missing keys; sandboxed bash policy; non-code outputs routed to sandbox. | Safer runtime; watch artifact locations. |
| **Access policy & guardrails** | Owner-only Slack default, per-gee inbound policies, AgentsPanel guardrails restructure, outbound `never_do` scoped to outbound tools. | Important for external-send safety and Slack/email scope reviews. |
| **Windows hardening** | Git/CLI spawn fixes, credential-prompt hang fix, process groups, daemon lifecycle, UTF-8 IO, six Windows Terminal builds. | Mostly Windows-lane, but signals broad runtime hardening. |
| **Daemon & delivery** | Inbound activations prioritized, trigger text replies, Telegram attachment separation, ack noise suppression, SendMessage identity hardening, gateway-proof ticket delivery. | Better background reliability and fewer false delivery claims. |
| **Prime + per-user routing** | Deterministic per-user prime via gateway, per-device inbound routing, companion-namespaced registry. | More predictable routing for Mariciel/MG surfaces. |
| **Cost Analyzer** | In-window Usage page with per-user/bucket/category + infra stacks. | Useful for future Edenic cost visibility. |

### ⚠️ Caution
- **Do not broad-run new org/task substrates yet.** Start with one bounded, low-risk docs/project surface.
- **Watch the sandbox behavior.** Bash may now reject expected project cwd operations unless routed correctly; generated artifacts may land differently.
- **Outbound/email guardrails still need audit.** The release improves policy scoping, but mg@edenic.co and mariciel@gtekpartners.com exclusions remain a known blocker until checked.
- **Task concurrency needs restraint.** Multiplex Tasks are powerful, but should use explicit concurrency limits to avoid noisy or duplicate work.

### ✅ To Explore
- [ ] Confirm Settings shows Beta for both Gee/T app and Gee-Code; restart Gee/T + daemons; verify `/channel` reports `beta`.
- [ ] Confirm Gee-Code 0.69.0 + Gee/T 1.40.0 installed.
- [ ] Review the new Tasks view in The Terminal.
- [ ] Try TaskGraph/DynamicHarness on a bounded non-production workflow.
- [ ] Test commitment capture on one low-risk follow-up and confirm it creates one clean ticket.
- [ ] Re-check sandbox artifact routing for non-code outputs.
- [ ] Continue email-on-behalf/account-exclusion guardrail audit before any external-send use.

---

<a name="v068x"></a>
## 🏢 Gee-Code 0.68.x + Gee/T 1.39.x + Windows 1.39.x — Organization Substrate, Commitments, Delivery Integrity, Agent-Aware Docs (Jun 1, 2026 ~9:34 PM PT)

**Requires:** Beta channel selected for both Gee/T app updates and Gee-Code builds. Neil said users who followed Saturday's instructions should automatically pick this up.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), Jun 1 ~9:34 PM PT (Gee-Code 0.68.x + Terminal/Gee/T 1.39.x + Windows 1.39.x).

### Summary
This is a hardening-heavy release with a new organizational deployment substrate. The headline: Gee can now reason about organization surfaces through `/init organization`, capture evidence, track governed source edges, and promote above procedural memory with approval gates. It also turns Gee's own promises into durable follow-up tickets, tightens ticket continuation/delivery proof, adds sandboxed execution policy, improves OpenClaw/Codex recovery, preserves release channels on reinstall, improves Windows support, and adds a new agent-aware documentation surface at `https://gee.edenic.ai` plus bundled `gee-docs` skill/CLI hints.

### 🎯 Most Impactful For You

1. **Organization substrate + `/init organization`** ⭐⭐⭐ — This is directly relevant to Edenic/NLYM operating-system work, but it should be tested on a bounded surface first. Do not point it at everything until behavior is understood.
2. **Action commitments become durable tickets** ⭐⭐⭐ — Useful for MG's follow-through role. Watch for whether this reduces dropped promises without creating duplicate tracker noise.
3. **Delivery proof + SendMessage identity hardening** ⭐⭐ — Important for scheduled/heartbeat reliability and the Telegram/SMS guardrails. First few outbound/background runs after update should be watched.
4. **Sandboxed execution + output routing** ⭐⭐ — Good safety improvement. Confirm generated reports still land in `$GEE_OUTPUT_DIR` and not scattered working directories.
5. **Agent-aware docs (`gee.edenic.ai`) + bundled `gee-docs`** ⭐⭐ — Likely reduces future setup/debugging friction. Worth one daytime review pass.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Organization substrate** | Governed source edges, evidence capture, workflow brains, approval-gated promotion above procedural memory. | Foundation for treating Edenic/NLYM/GTEK as structured org surfaces instead of loose files. |
| **`/init organization`** | Discover → populate → follow flow wired into CLI. | Potentially useful for onboarding Gee to an org's content/surfaces. Test carefully. |
| **Action commitments** | Promises Gee makes become durable follow-up tickets that resume on retry. | Reduces dropped commitments; watch for duplicate/noisy follow-ups. |
| **Ticket & delivery integrity** | Continuation contracts preserved; partial deliveries stay open; follow-ups resume rather than duplicate. | Should improve long-running tasks and background delivery reliability. |
| **Delivery proof** | Gateway proof required before marking something delivered; SendMessage sender identity hardened. | Prevents false “sent” status and wrong-sender issues. |
| **Sandboxed execution** | Sandboxed bash policy + non-code outputs routed to contained workspace. | Safer execution and cleaner artifact routing. |
| **OpenClaw / Codex hardening** | Gee tools first-class in ACP, health-check + repair in Settings, poisoned-session recovery. | Better recovery when Codex/OpenClaw sessions get wedged. |
| **Model aliases + pure default** | Grok/xAI build aliases; interactive auto-REPL defaults to pure mode. | Note only; no default model change recommended for mg. |
| **BYOP & pipe hardening** | Baseline tools in BYOP; bounded persistent-pipe seed to avoid Codex 1MiB cap. | More reliable cross-tool operation. |
| **Quieter autonomy** | Duplicate/confused/attachment/holdoff/refusal acks suppressed; iteration-limit notice added. | Should reduce noisy background pings. |
| **Channel-aware release/update** | Channel preserved on reinstall; per-channel wheel feeds; release-console binary matrix. | Prevents falling off Beta after reinstall. |
| **Windows lane** | 1.39.1 Windows-only release, comspec CLI spawn, git binary resolution for empty graph. | Useful for Windows testers, not Mariciel's Mac unless supporting others. |
| **Faster first Gee tab** | Stale-tolerant snapshots, stale-first refresh, delayed first-mount polling. | Faster Terminal startup. |
| **JSONL previews + Pretext polish** | Inline `.jsonl` previews, webview sizing, exact clipboard, recents dropdown. | Helpful for logs and Gee state inspection. |
| **Docs & discovery surface** | Harness-first mental model, generated agent docs + `llms.txt`, bundled skills, `RecordCommitment`/`Promise`, absolute cross-links. | Better self-serve docs and tool hints. |
| **Telegram attachments** | Real local-file attachments via SendMessage clarified in house voice + prompt docs. | Useful for sending reports/files; quiet-hour gates still apply. |
| **Connector / pipe / org-route** | Account required for email handles, bounded persistent-pipe seed, `/init organization` route wired. | More reliable connector/org routing. |

### ⚠️ Caution
- **Do not run `/init organization` across a broad workspace yet.** Start with a bounded docs surface and confirm what it writes/records.
- **Watch for SendMessage identity failures.** Hardening is good, but first post-update sends may reveal old config mismatches.
- **Quiet autonomy should reduce noise, not hide real blockers.** If background runs go silent, check delivery proof/logs before assuming no work happened.
- **Sandboxed output routing may change where artifacts land.** For user-facing artifacts, keep using `$GEE_OUTPUT_DIR` explicitly.

### ✅ To Explore
- [ ] Confirm Gee-Code 0.68.x + Gee/T 1.39.x installed after Beta-channel auto-update.
- [ ] Open `https://gee.edenic.ai` and skim the new agent-aware docs.
- [ ] Try bundled `gee-docs` skill/CLI hints during a low-risk setup/debug task.
- [ ] Test `/init organization` on one small bounded Edenic/NLYM surface during a daytime interactive session.
- [ ] Watch next scheduled/background SendMessage for delivery proof + identity behavior.

---

<a name="v0670"></a>
## 🔀 Gee-Code 0.67.0 + Gee/T 1.37.0 (Mac) / 1.38.0 (PC) — Multi-Channel Deployments, Configuration Management, App Rename (May 30, 2026 ~4:45 PM PT)

**Requires:** App update + **manual Settings change to keep getting Beta updates** (see below). Old "the-terminal" Dock icons will break ('?') — must delete and re-pin from Applications. Detailed HTML release notes pending from Neil.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 30 ~4:45 PM PT (Gee-Code 0.67.0 + Gee/T 1.37.0 Mac / 1.38.0 PC).

### Summary
Three structural shifts plus pending Configuration Management substrate. (1) **Multi-channel deployments** — Dev / Beta / Stable update channels now exposed in Settings. Default may not be Beta; explicit opt-in required to keep receiving the early builds the test group has been on. Dev = internal only; Stable = future public deployment. (2) **App renamed back to Gee/T** from the brief "the-terminal" rebrand. Old Dock pins go to '?' on update — must delete and re-pin from Applications. (3) **Configuration Management feature** introduced (details TBD in Neil's pending HTML notes). (4) Lots of other features/QoL/bug fixes — Neil flagged HTML release notes coming later. Same-day PSAs worth holding alongside this release: Opus 4.8 + latest Claude Code burns through Max weekly limit in ~2.5 days; next Gee-Code release will default `cc-gee-max` to Opus 4.8 — switch to `cc-gee-high` or `cc-gee-xhigh` to cap token usage. Neil also reiterated OpenAI Subscription (Codex + ChatGPT-Max via Gee's REPL with GPT-5.5 max reasoning) currently outperforms Claude Code in his testing. Next release also bringing a beads-derived **Workflow** system (plan-as-graph → parallel execution → synthesis) targeting Claude Code Workflow parity.

### 🎯 Most Impactful For You

1. **Set update channels to BETA in Settings** ⭐⭐⭐ — Without this, you fall off the beta train and stop receiving the cadence of builds the Core test group is on. Open Gee/T → Settings → set both **App Updates** and **Gee-Code Builds** to **BETA**. Do not select Dev. Stable is the future public channel, not where Core testing lives today.
2. **Fix Dock icon** ⭐⭐ — Any pinned "the-terminal" icon goes to '?' after this update. Delete the broken Dock pin, open Applications → Gee/T, re-pin. One-time fix, but it'll bite if skipped (you'll think the app is broken — Alex hit this last week before the rename).
3. **Model picker discipline for next release** ⭐⭐ — Once the next Gee-Code lands, `cc-gee-max` will default to Opus 4.8 with the heavy token burn. Pre-decide: routine work on `cc-gee-high`, save `cc-gee-max` (Opus 4.8) for hard problems only. Or shift more weight to the OpenAI Subscription path Neil is recommending.
4. **Configuration Management** ⭐⭐ — Headlined as a feature but details pending. Likely relevant to mode/gee config surface (objectives, schedule, seeds, follow-ups). Wait for HTML notes before re-organizing any operating files.
5. **Dark-blue first-launch screen is expected** ⭐ — Not a crash. Intro movie is precaching. Sit tight on first boot post-update.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Multi-channel deployments** | Settings → App Updates + Gee-Code Builds each get Dev / Beta / Stable channel selectors. | Core test group must explicitly choose Beta to stay current; Stable lags Beta, Dev is internal. |
| **App renamed back to Gee/T** | Mac app bundle and Dock identity flip from "the-terminal" → "Gee/T". | Pinned old icons break to '?' — re-pin from Applications. |
| **Configuration Management** | New feature surface (details pending HTML notes from Neil). | Likely affects mode/gee config; hold structural changes until notes land. |
| **Dark-blue precache splash** | First post-update launch may show a dark blue screen while intro movie precaches. | Expected, not a hang. |
| **Lots of features/QoL/bug fixes** | Neil flagged "ton of new features, functionality, quality of life and bug fixes" in addition to Config Management. | HTML release notes pending; this row is a placeholder to expand later. |
| **(Heads-up, next release) Opus 4.8 default for cc-gee-max** | The next Gee-Code build will set cc-gee-max → Opus 4.8. | Token burn is heavy — Neil ran out of Max weekly limit in 2.5 days. Use cc-gee-high / cc-gee-xhigh for routine work. |
| **(Heads-up, next release) Workflow system** | Beads-REPL-derived tooling: plan-as-graph → parallel execution → synthesis, usable by any model. | Built to outperform Claude Code's Workflow feature. Will be one of the main reasons to upgrade. |

### ⚠️ Caution
- **Do not skip the Settings change.** If you don't set App Updates + Gee-Code Builds to Beta, you'll silently stop getting updates and assume Neil has paused releases. He hasn't; the channel just defaulted off you.
- **Don't install if Neil pings a hold.** Earlier on May 28 + May 29, Neil twice posted "🚨 Please don't install the new version of gee/t — multi-channel work is fragile." Those holds resolved by ~4:45 PM PT May 30 ("All Good Now" + this release post). Watch for similar pauses around the next release.
- **Next release will hit token budget hard** if you stay on cc-gee-max. Decide your model defaults now, before the upgrade.
- **HTML release notes pending.** Treat the feature surface as partially documented until the HTML drops. Don't restructure operating files on assumptions about Configuration Management.

### ✅ To Explore
- [ ] **Update + set Beta channels in Settings.** Confirm App Updates = Beta and Gee-Code Builds = Beta. Restart Gee/T.
- [ ] **Fix Dock pin.** Delete old "the-terminal" pin (broken '?'), re-pin Gee/T from Applications.
- [ ] **Watch for Neil's HTML release notes.** Add a follow-up here once they land — especially Configuration Management details.
- [ ] **Re-read this tracker scan's delivery** — first scheduled run on v0.67.0; confirm the notepad ping arrives and Git push succeeds end-to-end.
- [ ] **Decide model defaults before the next release** drops the Opus 4.8 cc-gee-max default on you.

---

<a name="v0663"></a>
## 🛡️ Gee-Code 0.66.3 + Gee/T 1.36.3/1.36.4 — Message Adjudication Gate, Unified Attachments, Ticket Email/Voice (May 27, 2026 ~6:30 PM PT)

**Requires:** Standard upgrade. v0.66.5 = two PC quick fixes pushed same night (no separate notes from Neil).
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 27 ~6:30 PM PT (Gee-Code 0.66.3 + Terminal 1.36.3 Mac / 1.36.4 PC).

### Summary
Five thematic clusters: (1) **Pre-send Message Adjudication Gate** — the ticket adjudicator now runs *before* SendMessage dispatches, blocking responses that don't satisfy the ticket's success contract; it was post-hoc before. (2) **Synthesis & Delivery hardening (8 interlocking fixes)** — narration-only fallbacks rejected, scheduled sends ship the model's actual body (not internal narration), outbox-proof enforced before claiming delivery, drop-proof synthesis fallback, watchdog stops killing healthy long-running triggers. (3) **Unified Attachment Substrate** — REPL/web/Pretext/daemon/clipboard/pipe all converge into one AttachmentRef system with session-scoped staging; attachments referenced (not inlined), preventing ARG_MAX blowups. (4) **Tickets activated via email and voice** — same lifecycle as text triggers. (5) Multi-provider compat (OpenRouter, Cursor agent tool events), MCP identity isolation, system_utility entitlement class, Windows PATH fix. Gee/T 1.36.3/1.36.4: inline mermaid SVG, Remote Pretext MCP bridge, X OAuth wizard, **self-healing updater** (auto-repairs stale MCP entries).

### 🎯 Most Impactful For You

1. **Pre-send Message Adjudication Gate** ⭐⭐⭐ — Direct system-level backstop for MG's standing rule "send final deliverables only, no narration." Adjudicator now blocks "Let me check…" style sends before they ship, with a reason. This is the long-tail bug fix you've been wanting at the substrate layer.
2. **Scheduled-lane delivery proof + watchdog fix** ⭐⭐ — Combined with the v0.66.0 changes, scheduled jobs (like *this* tracker scan) now ship the real model body and the watchdog won't kill healthy long-running triggers. The Gee Release Tracker cron-miss scenario gets harder to trigger.
3. **Unified Attachment Substrate** ⭐⭐ — When Edenic/NLYM clients send attachments via email or paste large files, no more ARG_MAX blowups; one model across all ingress.
4. **Ticket Email + Voice activations** ⭐ — Inbound email and voice calls can now create tickets the same way text does. Useful when Neil emails GTEK questions or NLYM members reach out by phone.
5. **Self-healing updater + auto-repair connector hooks** ⭐ — Reduces the manual "rectify" step Alex Carloss hit on the v0.65.0 upgrade. Stale MCP entries clean themselves up.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Pre-send Adjudication Gate** | SendMessage runs through ticket adjudicator *before* dispatch, blocked with reason if contract not met. | Substrate-level enforcement of "final deliverables only." Was post-hoc, now a real gate. |
| **Synthesis & Delivery Hardening (8 fixes)** | Narration rejected, scheduled sends ship real body, outbox-proof required, drop-proof synthesis fallback, watchdog respects healthy long triggers. | Eliminates the "scheduled job ran but nothing arrived" and "internal narration shipped as final reply" classes. |
| **Unified Attachment Substrate** | All ingress paths (REPL, web, Pretext, daemon, clipboard, pipe) converge to AttachmentRef with session-scoped staging. | One model, no ARG_MAX blowups, same behavior for every ingress path. |
| **Ticket Email + Voice Activations** | Companion server routes inbound email and voice into ticket lifecycle. | Email/voice now first-class triggers like SMS/chat. |
| **Cost Tagging: Voice + Embeddings** | Sentinel-table dedupe + 4 voice + 7 embedding sites instrumented. | Per-mode/per-day rollups across text, voice, and embeddings — no silent blind spots. |
| **Lossless Capture + Activity Review** | Append-safe JSONL substrate + ignore/digest/promote/alert policy per heartbeat. | Foundation for "what did my Gee do today?" tooling. |
| **Multi-Provider Compat** | OpenRouter vendor/model routing, tool_call ID dedupe, Cursor agent tool events, streaming-suffix recovery. | Provider portability hardened. |
| **system_utility entitlement** | New entitlement class for predictive suggest + system credentials. | Tighter permission surface. |
| **MCP Identity Isolation** | Mode identity injected into Codex MCP at launch; daemon gees can't inject into Pretext panels they don't own. | Cross-mode contamination closed. |
| **Twitter/X Read Fixes** | Tweet + thread endpoints fixed (routing was wrong). | `GeeConnect(service="twitter")` reads now resolve correctly. |
| **Windows PATH Resolution** | CLI detection + terminal rendering on Windows. | Fix for "couldn't find own binary" on PC. |
| **Gee/T 1.36.3: Inline Mermaid** | Mermaid diagrams render inline as SVG; SVGs stay mounted across re-renders. | Diagrams from agent output show as images, not raw fences. |
| **Gee/T: Remote Pretext MCP Bridge** | Terminal MCP server bridges remote Pretext tools — cloud/SSH gees can drive local Terminal surfaces. | Remote Gee-Code instances can now drive your local Terminal. |
| **Gee/T: X OAuth Wizard** | Full OAuth: connect, paginate, reconnect, disconnect. | Personal Twitter linkage via connector wizard. |
| **Gee/T: Self-Healing Updater** | Auto-detects + repairs stale MCP entries and broken update state. | Fewer manual "rectify" sessions on upgrade. |
| **Gee/T: Shared Gee Domain Controls** | Mode settings/model picker/deployment config extracted to reusable component. | UI cleanup; single source of truth. |

### ⚠️ Caution
- **Adjudication gate may block previously-silent sends.** If a scheduled job or heartbeat starts reporting blocked finals with a reason, that's the new gate doing its job — read the reason, don't bypass. The fix is to make the message satisfy the ticket contract.
- **Mode identity injection is stricter.** If you see "identity mismatch" errors on a delegation or Pretext panel, check the mode is consistent across daemon/Pretext/Codex.
- **v0.66.5 has no published notes** — Neil said "Just pushed 2 quick versions for PC fixes." Treat as Windows/CLI polish.

### ✅ To Explore
- [ ] **Test a scheduled lane** — fire one of MG's scheduled jobs and confirm: (a) outbox proof is logged, (b) the final body that ships matches the model's actual SendMessage call, (c) no narration leaks through.
- [ ] **Try an email-triggered ticket** — send mg@edenic.co a structured inbound and confirm a ticket is created the same way SMS/chat does.
- [ ] **Attempt an inline mermaid diagram** in a Pretext reply (e.g., NLYM rollout flow). Confirm SVG renders and persists through panel re-renders.
- [ ] **Audit Cost Analyzer rollup** for voice + embeddings — voice usage should now appear in per-mode tallies for the first time.

---

<a name="v0660"></a>
## 📮 Gee-Code 0.66.0 + Gee/T 1.36.1 — Outbound Integrity, Scheduled-Lane Delivery Proof, Heartbeat Routing (May 26, 2026 ~9:17 PM PT)

**Requires:** Standard upgrade.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 26 ~9:17 PM PT (Gee-Code 0.66.0 = 27 commits since v0.65.1; gee/t 1.36.1 = 2 commits).

### Summary
Foundational substrate work for outbound trust and scheduled execution. (1) **Outbound integrity for the trigger lane** — pre-send adjudication using the ticket adjudicator as source of truth, universal synthesis turn for adjudicator-rejected finals, drop-proof synthesis fallback, narration detector extended to mid-sentence pivots, hard reject on narration-only synthetic fallbacks. (2) **Scheduled-lane delivery proof** — scheduled fallback ships the model's *real* SendMessage body (not narration text), requires outbox proof before claiming delivery, merges scheduled route file when activation context is gee-hq, instruments SendNotification dispatch. (3) **heartbeat_gather_state wired into routing layer** — the model sees the same standing-tasks/objectives snapshot the heartbeat read produces, without re-calling it every turn. (4) New **lossless capture substrate** (events/lossless_capture.py) + **activity_review** policy + **activity-wake watcher**. (5) Cost tagging Phase B1+B2 — sentinel dedupe + 4 voice-emit sites + 7 embed sites. (6) Watchdog stops killing healthy long-running triggers; SendMessage dedupe time-window backstop. (7) Gee/T 1.36.1: inline mermaid + SVG persistence fix + connector auto-repair hooks.

### 🎯 Most Impactful For You

1. **Scheduled-lane delivery proof** ⭐⭐⭐ — This very tracker scan is a scheduled job. Outbox-proof requirement + real-body shipping fixes the long-tail "scheduled job ran but didn't deliver" class. The May 20 catch-up commit (where a 4 PM PT scan missed Neil's late posts) is exactly the kind of bug this layer addresses upstream.
2. **Outbound integrity (trigger lane)** ⭐⭐⭐ — Pairs with the v0.66.3 pre-send adjudication gate to make "Let me check…" leaks structurally impossible. Aligns with MG's standing rule.
3. **Heartbeat state in routing** ⭐⭐ — The model now sees standing tasks + objectives without an extra tool call per activation. Should reduce token spend on heartbeat reads.
4. **Activity-wake watcher** ⭐⭐ — New event driver surfaces recent activity bursts as wake triggers. Means a Gee won't sit idle after a flurry of external signals (e.g., a string of NLYM treasurer emails) without ever being activated.
5. **Cost tagging Phase B1+B2** ⭐ — All AI spend (text/voice/embeddings) flows through a single audit log. Per-mode/per-day rollups stop having silent blind spots.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Pre-send Adjudication (trigger lane)** | Ticket adjudicator runs before SendMessage; rejected finals get a universal synthesis turn; narration-only fallbacks hard-rejected. | Substrate-level enforcement of "no narration as final." |
| **Scheduled-Lane Delivery Proof** | Scheduled sends ship model's actual body, require outbox proof, merge scheduled route file when context is gee-hq, SendNotification instrumented. | Scheduled jobs (like this tracker) stop being silently lost. |
| **heartbeat_gather_state in routing** | Routing layer pre-loads standing tasks/objectives snapshot. | Less re-fetching per activation. |
| **events/lossless_capture.py** | Append-safe JSONL of every activation event. | Foundation for "what did my Gee do today?" + activity-wake. |
| **activity_review policy** | Decides what's wake-worthy per heartbeat (ignore/digest/promote/alert). | Backpressure visible, never silent. |
| **Activity-Wake Watcher** | Event driver surfacing recent activity bursts as wake triggers. | Gee doesn't sit idle after relevant external signals. |
| **Cost Tagging Phase B1 + B2 (#147)** | Sentinel dedupe + 4 voice-emit sites + record_embedding_event + 7 embed call-sites. | Voice + embedding spend now visible in rollups. |
| **Watchdog fix** | No longer kills healthy long-running triggers (was treating "running for a while" as "stuck"). | Long jobs (deep research, scheduled scans) complete. |
| **SendMessage dedupe time-window backstop** | Duplicate sends across worker forks caught even in subprocess path. | No double-deliveries. |
| **Channel-thread context preservation** | Most-recent outbound preserved when building channel-thread context. | Follow-on replies see what Gee just said. |
| **Socket GET param encoding** | make_api_request uses _encode_query_params (not raw string interpolation). | Fixes &, =, space edge cases. |
| **Twitter read routing fixes** | Twitter read routing + tweet/thread endpoints (3d00c02, 9e815bb). | Reliable read-side access. |
| **URL reads default to server fetch** | WebFetch-style by default, not browser PIP. | Less Terminal real-estate waste. |
| **AI-pacing tests** | Compact + minimal verbosity profiles get explicit pacing tests. | Channel-etiquette regressions caught at unit-test time. |
| **Gee/T 1.36.1: Inline Mermaid in PretextPanel** | Mermaid code-fences render as diagrams (new getInlineMermaidMetrics + 'mermaid' kind in InlineMediaLayout). | Diagrams stop showing as raw code blocks. |
| **Gee/T: Mermaid SVG persistence fix** | useMermaidSvg hook owns SVG via React state (no DOM mutation). | "Diagram flashes then disappears" bug fixed. |
| **Gee/T: Connector auto-repair hooks** | Terminal connector setup auto-repairs broken hook wiring. | Smoother first-run setup. |

### ⚠️ Caution
- **Watchdog change is a behavior shift.** Long-running jobs that previously got killed (sometimes acceptably) will now run to completion. Confirm no runaway loops exist in scheduled jobs.
- **Activity-wake watcher can cause new activations.** If you start seeing unexpected heartbeats fire mid-day, check the activity policy — it may be classifying signal bursts as wake-worthy.
- **Cost rollups will look different** with voice + embeddings now in the audit log. Don't be surprised if total spend in dashboards shifts after upgrade.

### ✅ To Explore
- [ ] **Confirm the tracker scan + Telegram heartbeats** still deliver post-upgrade. Outbox proof should be visible in scheduled runs.
- [ ] **Review activity_review policy** in essential docs to understand what gets promoted to wake.
- [ ] **Check cost rollup** for first per-mode voice/embedding line items.

---

<a name="v0650"></a>
## 🐦 Gee-Code 0.65.0 + Gee/T 1.36.0 — X (Twitter) OAuth, Slack User-Token, Remote Pretext MCP Bridge (May 23, 2026 ~2:09 PM PT)

**Requires:** Gee/T 1.36.0 install. Note: Alex Carloss hit a Python 3.14 PATH issue on upgrade ("ENOENT for gee-code binary") — self-rectified, but worth knowing the upgrade may need manual PATH fix on some machines.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 23 ~2:09 PM PT.

### Summary
Two flagship adds and a bundle of routing/credential fixes. (1) **X (Twitter) OAuth lands** — accounts, pagination, bookmark folders, list reads via GeeConnect. (2) **Slack user-token outbound + SlackRead/SlackReadTopology** — read Slack with user perspective. (3) **Model-backed triage now default-on**, broader self-delegate detection. (4) Daemon forced mode-drop reload + richer status/trace diagnostics. (5) Fixes: routing honors explicit out-of-band channels, Telegram mode-install match, credentials gee-scope normalization, full vault-key surfacing, **Telegram rewrites markdown tables** (Telegram can't render them), **scheduled activations actually deliver final response**, MCP creates GEE_OUTPUT_DIR before export. (6) Docs site rebranded to **Gee Operating Manual** with OS-level sections; user-email canonical service + attachment action documented. (7) Gee/T 1.36.0: **Remote Pretext MCP bridge** — terminals can mount remote Pretext sessions; the remote session can control the local Terminal (invoke PIPs, etc.) via MCP. X OAuth in ConnectorsPanel. Short Gee names fix.

**Follow-up patch (May 24 ~7:09 PM PT):** Removed the interim-text heuristic that could create noisy or premature Telegram updates. Added stronger backstops for delegation callbacks and interim Telegram reply handling.

### 🎯 Most Impactful For You

1. **X (Twitter) OAuth lands** ⭐⭐ — Personal Twitter is now connectable via the wizard. Useful if you want Gee to read your timeline, bookmarks, or post drafts for review. Mirrors Gmail connector flow.
2. **Telegram markdown table rewriting** ⭐⭐ — Direct fix to a recurring Telegram delivery problem: tables rendering as garbled text. Affects MG heartbeat digests if they ever include tabular data.
3. **Scheduled activations actually deliver final response** ⭐⭐ — Companion to v0.66.0's scheduled-lane delivery proof. This v0.65.0 fix is the first half — scheduled jobs deliver instead of silently dropping. Direct relevance to this tracker.
4. **Telegram delivery patch (May 24)** ⭐⭐ — Interim-text heuristic was creating noisy Telegram pings; removed. Stronger delegation callback backstops. Cleaner heartbeat behavior.
5. **Remote Pretext MCP bridge** ⭐ — Cloud-hosted Gee can now drive your local Terminal via MCP. Pairs with v0.66.3's expansion. Future option for the cron-miss issue if you move the tracker to a cloud instance.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **X (Twitter) OAuth** | Connect personal X account; read timeline, bookmark folders, lists; paginate. | Personal Twitter connector parity with Gmail. |
| **Slack user-token outbound + SlackRead** | Outbound + read with user-perspective scopes. | Gee sees Slack the way you do. |
| **Model-backed triage default-on** | LLM-driven triage is now the default, not opt-in. | More intelligent routing; verify the first few activations match intent. |
| **Daemon forced mode-drop reload** | Daemon can drop a mode and reload cleanly. | Cleaner restart cycles. |
| **Richer status/trace diagnostics** | More info on activation state. | Faster debugging. |
| **Routing honors out-of-band channels** | Telegram mode-install match. | Heartbeat → Telegram delivery is correct. |
| **Credentials gee-scope normalization** | Full vault-key surfacing. | All vault entries discoverable. |
| **Telegram rewrites markdown tables** | Tables converted to text Telegram can render. | No more garbled tables in Telegram digests. |
| **Scheduled activations deliver final response** | First half of the scheduled-delivery fix series. | Scheduled jobs reach the user. |
| **MCP creates GEE_OUTPUT_DIR** | Before export, ensures dir exists. | No first-run export failures. |
| **Docs: Gee Operating Manual rebrand** | Docs site reorganized with OS-level sections; user-email canonical service + attachment action documented. | Easier reference for the new attachment substrate. |
| **Gee/T 1.36.0: Remote Pretext MCP bridge** | Terminals mount remote Pretext sessions; remote sessions control local PIPs via MCP. | Cloud Gee drives local Terminal. |
| **Gee/T: X OAuth in ConnectorsPanel** | Wizard for X account connect/reconnect/disconnect. | UI parity for Twitter. |
| **Gee/T: Short Gee names fix** | UI bug fix. | Cleaner display. |
| **Patch (May 24): Telegram heuristic removed** | Interim-text heuristic that fired noisy/premature Telegram updates removed. | Less Telegram spam from in-flight activations. |
| **Patch: Delegation callback + interim Telegram backstops** | Stronger safety nets. | Cleaner async handoff. |

### ⚠️ Caution
- **Python 3.14 PATH issue on upgrade** — Alex hit `ENOENT for gee-code binary` and had to manually rectify. If you have a hand-rolled update fix, expect to redo it.
- **Model-backed triage default-on is a behavior change.** Watch the first few activations to confirm routing matches intent.
- **X OAuth is real now, not WIP.** Easy to connect by accident if you're poking around the connector wizard; only connect when you actually want to.

### ✅ To Explore
- [ ] **Connect personal X via wizard** — only if you want Gee read access to your timeline/bookmarks. Confirm scopes before authorizing.
- [ ] **Send a Telegram message with a table** — confirm the new rewriter produces readable output.
- [ ] **Test a scheduled lane** — confirm delivery lands (this is the first half of the fix; v0.66.0 added the outbox-proof second half).
- [ ] **Skim the Gee Operating Manual** rebrand for the new OS-level sections, especially user-email + attachment docs.

---

<a name="v0644"></a>
## 📎 Gee-Code 0.64.4 + Gee/T 1.35.3 — User-Email Attachments, Scheduled Delivery Channels Honored (May 22, 2026 ~12:37 PM PT)

**Requires:** Standard upgrade.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 22 ~12:37 PM PT.

### Summary
Big substrate release on attachments and scheduled delivery. (1) **user-email/attachment as a GeeConnect action** — Read/thread responses include `attachments[]` metadata; a single follow-up call stages bytes to `~/.gee-code/modes/<mode>/ingress_attachments/` and returns a local_path. The LLM never sees raw base64; Read/Summarize take over from disk. (2) **user-email follow-up trio** — search formatter prepends `[id]` so read → thread → attachment chains without raw_result; attachment hints (filename, mime_type, part_id) thread through; stage path resolves the active daemon mode instead of only env. (3) **Preempt gate trusts inbound origin, not delivery targets** — heartbeat → delegate_async(delivery_channel=sms) is correctly preemptible; real user SMS → OG → worker stays immediate via carried inbound_route. (4) **Telegram stream resets per SendMessage** — two SendMessages in one activation are two independent messages, not the second containing the first's history glued in front. (5) **Triage parses "delegate this to X"** — was capturing as target; now correctly routes to named recipient. (6) **respond_to_request joins PURE_AUTONOMOUS_TOOLS** — workers that started a delegate_async can complete their own callback on the canonical path, with regression test pinning the pairing. (7) **Scheduled delivery channels honored** — delivery_channel threads through daemon → runner → send_notification with identity-policy enforcement and a new monologue gate; a 9 AM SMS digest actually arrives on SMS. (8) Codex image argv stays under cap (stage to disk, pass via path). (9) Terminal updater + stale-MCP self-heal. (10) Platform-ops routing narrowed to creation only — gees can edit schedule.md, seeds, follow-ups, and trigger daemon reloads directly again.

### 🎯 Most Impactful For You

1. **Scheduled delivery channels honored end-to-end** ⭐⭐⭐ — Direct, foundational fix for MG's scheduled lanes. The monologue gate + identity-policy enforcement is the layer that made later scheduled-delivery proofs (v0.65.0, v0.66.0) possible. This tracker scan benefits directly.
2. **user-email attachments as GeeConnect action** ⭐⭐⭐ — Architecturally clean: the LLM never sees raw base64, files stage to disk and Read takes over. When NLYM members or Edenic partners email PDFs, Gee can now actually use them without prompt-context blowups.
3. **Telegram stream resets per SendMessage** ⭐⭐ — Fixes a confusing UX bug where successive Telegram messages glued prior context in front. Cleaner heartbeat digests.
4. **Preempt gate trusts inbound origin** ⭐⭐ — Real user SMS bypass remains immediate; heartbeat delegations correctly preemptible. Important for SMS-bound interactive sessions.
5. **Platform-ops routing narrowed to creation only** ⭐ — Direct relevance to MG's heartbeat: editing schedule.md / seeds / follow-ups now stays direct again instead of being routed through gee-platform-ops. Faster maintenance loops.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **user-email attachment as GeeConnect action** | Read/thread responses include attachments[] metadata; follow-up call stages bytes to `~/.gee-code/modes/<mode>/ingress_attachments/`, returns local_path. | LLM never sees base64. Read/Summarize work from disk. |
| **user-email follow-up trio** | search formatter prepends [id]; attachment hints thread through; stage path resolves active daemon mode. | Cleaner read → thread → attachment chains. |
| **Preempt gate by inbound origin** | heartbeat-originated work is preemptible; real-user-originated stays immediate. | Correct priority handling across channels. |
| **Telegram stream resets per SendMessage** | Each SendMessage is an independent message. | No more glued-in prior context. |
| **Triage parses "delegate this to X"** | Regex routes correctly to named recipient. | Natural-language delegation works. |
| **respond_to_request in PURE_AUTONOMOUS_TOOLS** | Workers complete own callbacks on canonical path. | No more bypassing through discover_tools/Bash. |
| **Scheduled delivery_channel threaded** | daemon → runner → send_notification with identity-policy + monologue gate. | Scheduled job's specified channel actually used. |
| **Codex image argv under cap** | Image inputs stage to disk, pass via file path. | No ARG_MAX overflow on Codex image calls. |
| **Terminal updater + stale-MCP self-heal** | Auto-update recovers from prior partial states; ghost MCP entries from defunct sessions removed. | Smoother upgrades. |
| **Platform-ops routing narrowed to creation only** | gees edit schedule.md, seeds, follow-ups, and reload daemon directly; gee-platform-ops router only handles creation. | Faster routine maintenance loops. |

### ⚠️ Caution
- **Attachment paths are mode-scoped.** `~/.gee-code/modes/<mode>/ingress_attachments/` — confirm cleanup policy and disk usage if you start receiving large PDFs frequently.
- **Preempt gate change can shift activation ordering.** If a heartbeat task feels slower than before, it may be correctly yielding to real-user inbound.

### ✅ To Explore
- [ ] **Send yourself an email with a PDF attachment** to mg@edenic.co; verify the new flow stages the file and lets Read/Summarize work from disk.
- [ ] **Run a scheduled job with explicit channel="telegram"** and confirm it lands on Telegram (not the daemon default).
- [ ] **Try "delegate this to gtek"** in a triage message and confirm correct routing to the named target.

---

<a name="v0643"></a>
## ✉️ Gee-Code 0.64.3 + Gee/T 1.35.1 — Email-on-Behalf Re-enabled, LLM-Driven Delegation, Slack User Scopes (May 20, 2026 ~11:30 PM PT)

**Requires:** New Gee/T install (1.35.1). Standard upgrade flow: Gee/T install restarts daemon, fetches new Gee-Code, updates. Force-restart if needed.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 20 ~11:30 PM PT.

### Summary
Eight changes land in this release: (1) **Slack User Scopes** — Gee can now see Slack the way you do (your channels, your DMs), not just bot-scope content. (2) **New reference implementations + tools** for the three foundational extension paths: creating a Gee, building a Brick, setting up Events. (3) **Farshid's Cost Analyzer** inclusions. (4) **Deployment improvements** for Remote (the v0.64.0 EC2 path) + a RunBook added to Essential Docs. (5) **LLM-driven delegation** — delegation routing now uses model-driven selection rather than purely rule-based. (6) **Email sending on behalf of user re-enabled** — but with hard guardrails and account exclusions to prevent the kind of unintended sends that motivated the earlier disable. (7) **WIP Twitter OAuth connector**. (8) Fixes and polish.

### 🎯 Most Impactful For You

1. **Email-on-behalf re-enabled with guardrails** ⭐⭐ — Direct relevance to mg's outbound rules. Your current rules.md says "Email is for final consolidated reports only" and standing orders forbid sending without explicit user direction. The new guardrails are upstream system defense, not a relaxation of your contract. **Action: confirm `outbound_permissions` and `allowed_accounts` are set conservatively for mg before any email send-on-behalf path activates.** If you have `mg@edenic.co` listed anywhere as a send-from identity, audit it.
2. **LLM-driven delegation** ⭐ — Changes how `delegate_async` chooses targets. If you've noticed delegations going to unexpected workers, this is now model-driven and should improve, but also warrants a watch for the first few delegations to confirm routing matches intent. Worth a sanity check on your next NLYM/Edenic delegation.
3. **Reference implementations for Gee/Brick/Events** ⭐ — This is the unblocker for the open robustification sweep items: MCP wizard (Granola), GCP wizard, and one event watch (flight/stock). If you wanted to build a Brick or wire an event watcher and couldn't find a clean starting point, Neil just shipped one.
4. **Slack User Scopes** — Lower priority today (mg has no live Slack workspace), but if Edenic onboards Slack or you're invited to a partner workspace, this matters.
5. **Cost Analyzer (Farshid's contributions)** — Aligned with your commercial-terms posture. More visibility into per-task / per-mode cost.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Slack User Scopes** | Gee can authenticate with user-level Slack scopes (not just bot scopes). | Gee sees the same Slack you see, including DMs and private channels you're in. |
| **Reference: Create a Gee** | Worked example of building a new mode from scratch. | Lowers learning curve for spawning a new specialized gee (e.g., a dedicated NLYM gee post-7/1). |
| **Reference: Build a Brick** | Worked example of constructing a Brick end-to-end. | Direct unblocker for the robustification sweep items. |
| **Reference: Setup Events** | Worked example of wiring an Events watcher. | Direct unblocker for the flight/stock event-watch backlog item. |
| **Cost Analyzer (Farshid contributions)** | Cost surfacing/analysis improvements. | Better cost visibility for the Console API / Commercial Terms workflow. |
| **Remote deployment polish + RunBook** | Stability improvements on the v0.64.0 EC2 path + documented deployment runbook in Essential Docs. | Smoother cloud Gee-Code experience. |
| **LLM-driven delegation** | Delegation routing uses model-driven target selection. | More intelligent routing; better intent matching for delegated tasks. |
| **Email-on-behalf re-enabled** | Outbound email from Gee identity is allowed again, with hard guardrails and account exclusions. | Important capability returns, but the guardrails are the headline — system defense, not a permission relaxation. |
| **WIP Twitter OAuth connector** | Work-in-progress OAuth path for Twitter. | Future capability for social monitoring or posting; not production yet. |
| **Fixes & Polish** | Misc bug fixes. | Standard maintenance. |

### ⚠️ Caution

- **Email-on-behalf needs audit before relying on it.** Confirm guardrails + account exclusions match Mariciel's outbound rules (rules.md: "Email is for final consolidated reports only"). Do NOT assume the upstream guardrails replace mg's standing orders — they are additive, not a substitute.
- **LLM-driven delegation is a behavior change.** First few delegations after upgrade should be watched to confirm routing matches intent — particularly for any delegation involving Gtek or sensitive-client modes.
- **Twitter OAuth is WIP** — do not wire any production workflow to it yet.

### ✅ To Explore

- [ ] **Audit email-on-behalf config**: check that account exclusions cover `mg@edenic.co`, `mariciel@gtekpartners.com`, and any other identity that should never auto-send. Confirm guardrails before relying on the capability.
- [ ] **Try a reference implementation**: pick one of the three (Create a Gee / Build a Brick / Setup Events) to land one of the 3 remaining robustification sweep items. Easiest win: the Events reference unblocks the flight/stock event-watch.
- [ ] **Read the RunBook** in Essential Docs when you next consider moving any workflow to a remote Gee-Code instance (cost-saving or laptop-asleep mitigation for the Gee Release Tracker cron-miss issue).
- [ ] **Watch the next delegation** for routing-match check (LLM-driven selection).
- [ ] Cost Analyzer: check whether new per-mode/per-task cost views are exposed in Gee/T.

---

<a name="v0642"></a>
## 🩹 Gee-Code 0.64.2 — Slack Semantic Routes, SendMessage Identity Fix, Cursor Composer-2.5 Default (May 20, 2026 ~3:24 PM PT)

**Requires:** Gee-Code patch only (no Gee/T release noted). Standard upgrade flow.
**Impact level:** 🟡 Medium
**Posted:** Neil, Gee Test (Core), May 20 ~3:24 PM PT.

### Summary
Three things land: (1) **Slack outbound routes now resolve semantically** — message routing in Slack respects intent rather than literal target lookups. (2) **`SendMessage` gee-identity enforcement fix** — the sender identity tied to a gee is now enforced correctly on outbound messages (relevant for the per-gee bot tokens / messaging-tokens-in-vault rework from v0.63.1). (3) **Cursor cloud default model bumped to composer-2.5** and surfaced in Gee/T model pickers. Neil's note: "Composer 2.5 is very cheap and personal tests are pretty encouraging." Farshid replied that 2.0 was "really bad" — so there's a delta worth noticing.

### 🎯 Most Impactful For You

1. **`SendMessage` identity enforcement** ⭐ — Direct relevance to mg's Telegram routing. The mandatory `channel="telegram"` standing order in heartbeat depends on identity being enforced cleanly across the bot token → gee mapping (v0.63.1 vault work). This patch closes a gap there.
2. **Cursor composer-2.5 default** — If you ever fall back to Cursor for code work, the default model just got cheaper and better. Worth noting for any cost comparison vs. Claude/Opus on routine code tasks.
3. **Slack semantic routing** — Lower priority for mg today (no live Slack workspace), but matters when GTek or Edenic eventually onboard Slack.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Slack semantic outbound routes** | Routing resolves by intent, not literal name match. | Reduces "wrong channel" misroutes on outbound Slack messages. |
| **`SendMessage` gee-identity enforcement** | Outbound messages now strictly carry the gee's identity. | Closes a per-gee bot-token enforcement gap from v0.63.1. |
| **Cursor cloud → composer-2.5** | New default model for Cursor cloud path; appears in Gee/T pickers. | Cheaper + better than composer-2.0 (per Neil + Farshid feedback). |

### ⚠️ Caution

- **No standing-order changes** — The mandatory `channel="telegram"` template in heartbeat rules.md still applies. This patch fixes plumbing; it does NOT change the contract.
- **Composer-2.5 is new** — Neil's personal tests are "encouraging" but it's not yet battle-tested at scale. Don't switch any production-y workflow off Claude based on this alone.

### ✅ To Explore

- [ ] No action required for mg flow — this lands transparently.
- [ ] If you ever poke Cursor for a side experiment, composer-2.5 is now the default.
- [ ] Note for future: SendMessage identity enforcement may surface a previously-silent bug if any mode was sending under a stale identity — watch for any `identity mismatch` errors in delegation/outbound logs.

---

<a name="v0640"></a>
## 🚀 Gee-Code 0.64.0 + Gee/T 1.35.0 — Remote Deployments: Gee-Code on EC2, Gee/T SSH-Connect (May 19, 2026 ~10:42 PM PT)

**Requires:** New Gee/T install (1.35.0). Standard upgrade flow: Gee/T install restarts daemon, fetches new Gee-Code, updates. Force-restart if needed.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 19 ~10:42 PM PT.

### Summary
Gee-Code can now run as a **standalone cloud instance** (EC2 etc.) and Gee/T connects to it over SSH as if local. Five new capabilities: (1) **One-click deploy to new instances**, (2) **SSH tunnel management**, (3) **Pretext Panel connect to remote instances over SSH** (also supports local "remote" instances via the Remote Pretext dropdown), (4) **Cloud credential preservation** — credentials/connectors are now segmented by deployment (local vs. remote), (5) **OAuth support** on remote instances. Bug fixes: Slack scopes update issue resolved, duplicate credential issues fixed, ticket-system dispatch bug fixed (was falling back to API for entitled users — addressed underlying issues too).

### 🎯 Most Impactful For You

1. **Cloud-resident Gee-Code** ⭐ — Run mg or any mode as a cloud instance instead of tied to the MacBook. For mg specifically, this means heartbeat / scheduled activations could continue while the laptop sleeps (the Gee Release Tracker missed-cron problem becomes obsolete). It also means client-sensitive modes like gtek could live in their own isolated cloud sandbox.
2. **Credentials segmented by deployment** — Local vs. remote credential pools are separate. Practical: you can keep client-confidential GTek API keys in a cloud instance the laptop never touches, while mg's personal credentials stay local. Aligned with commercial-terms posture.
3. **Ticket dispatch fallback fix** — The bug where entitled users were getting dispatched to API instead of their entitlement is fixed. If you've been seeing any "this should have used Max" routing surprises, this likely resolves them.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **One-click deploy to new instances** | Spin up a new cloud Gee-Code instance from the Terminal. | Lowers operational friction for cloud Gee-Code. |
| **SSH tunnel management** | Terminal manages the SSH tunnels to remote Gee-Code instances. | Hands-off connection lifecycle. |
| **Pretext Panel connect to remote** | Pretext panels can target remote Gee-Code over SSH; Remote Pretext dropdown also supports local "remote" instances for testing. | UI parity local vs. remote. |
| **Cloud credential preservation** | Credentials/connectors segmented by deployment. | Local and remote credential pools stay isolated. |
| **OAuth on remote** | OAuth flows work on remote instances. | Full connector parity in cloud. |
| **Slack scopes update fix** | Slack permission/scope updates now apply cleanly. | Resolves a known intermittent connector issue. |
| **Duplicate credential fix** | Resolves the issue where credentials could appear duplicated. | Cleaner Credentials Panel. |
| **Ticket dispatch fallback fix** | Entitled users no longer get dispatched to API by mistake. | Routing matches entitlement. |

### ⚠️ Caution

- **Don't migrate mg to cloud yet** — Mariciel's whole laptop-first workflow (MacBook 16-inch, Sequoia, Half Moon Bay) is tuned around local Gee-Code. Cloud Gee-Code is great for *new* modes (a hypothetical 24/7 NLYM Pay Voucher support gee, an isolated GTek client sandbox), not for moving existing modes.
- **Cloud cost surface is new** — EC2 hours, storage, and egress now exist as a potential cost line. No "free tier" assumed. Don't deploy speculatively.
- **OAuth on remote needs a separate auth pass** — Credentials are segmented by deployment, so OAuth-backed connectors will need to re-auth on the cloud instance.

### ✅ To Explore

- [ ] Read the deploy flow before doing anything (no immediate need; this is "interesting capability, hold for now")
- [ ] Consider whether the GTek confidential-client surface is a fit for a cloud-isolated deployment later in 2026
- [ ] Note the missed-cron solution: if mg ever moves to cloud, the 6 AM Gee Release Tracker catch-up scan stops being a thing

---

<a name="v0632"></a>
## 🚀 Gee-Code 0.63.2 — Task* MCP Tools, Remote-Deploy Prep, XAI Aliases, Tone Hardening (May 19, 2026 ~2:46 PM PT)

**Requires:** Gee-Code patch only (no Gee/T release). Standard upgrade flow.
**Impact level:** 🟡 Medium — patch in service of v0.64.0.
**Posted:** Neil, Gee Test (Core), May 19 ~2:46 PM PT. Neil's framing: *"This is mostly a release to help with some stuff I'm doing around deployments."*

### Summary
Patch release that lays groundwork for v0.64.0 remote deployments. **Task Planning becomes 1st-class across all REPLs/providers** — adds `Task*` MCP tools so any provider can hit them with parity, plus native `Task*` handlers and allowlist/prompt/noise-filter surfacing. WIP plumbing for running Gee-Code remotely (EC2) — add remote-domain update controls + stabilize remote-domain connections. **Better vision for Codex** — inject Codex images via native `-i` flag. **New XAI aliases**: `xai-zero`, `tai`, `tai-max`, plus reasoning-effort tiers added to the grok-4.3 alias class. **ai_pacing tone hardened against doom/gloom framing** — forecasts and progress updates stay positive/momentum-focused. GPT image generation gets a timeout bump for slow generations.

### 🎯 Most Impactful For You

1. **Task* MCP tools for cross-REPL planning** — If you ever invoke Gee-Code through a non-default REPL (Codex, etc.), task planning now has parity. Matters less for your daily Pretext+REPL flow.
2. **ai_pacing tone hardening** — Forecasts and AI Pacing language tuned to avoid doom/gloom. Should make MG's mode-instructions feel more steady; the existing tone.md guidance ("don't sugarcoat, don't doom spiral") gets reinforced at the model layer.
3. **XAI aliases** — `tai` and `tai-max` are new shortcuts. Not relevant today (you're on Max + Console), but worth knowing for the gee-release-tracker.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Task* MCP tools** | Task planning surfaced as MCP tools — cross-REPL/cross-provider parity. | Plan-once, execute-anywhere. |
| **Native Task* handlers + allowlist/prompt/noise-filter** | Built-in handlers with operator controls. | Better default plan-mode UX. |
| **WIP remote Gee-Code (EC2)** | Foundation for v0.64.0. Remote-domain update controls. | Preps the cloud-deploy story. |
| **Codex vision (`-i` flag)** | Codex provider supports image input natively. | Image input parity across providers. |
| **XAI: `xai-zero`, `tai`, `tai-max`** | New model aliases. | Shorthand for XAI routing. |
| **grok-4.3 reasoning tiers** | Adjustable reasoning effort. | Cost/quality trade. |
| **ai_pacing tone hardened** | Forecasts no longer drift toward doom/gloom. | Steadier model voice. |
| **GPT image timeout bump** | Slow image generations no longer time out. | Reliability for image-gen flows. |

### ⚠️ Caution

- **None for mg's daily flow** — This patch is mostly infrastructure for v0.64.0. The tone hardening is a behavior change but in the right direction.

### ✅ To Explore

- [ ] No action needed — this patch ships transparently. v0.64.0 is the real story.

---

<a name="v0631"></a>
## 🚀 Gee-Code 0.63.1 + Gee/T 1.34.1 — Ticket Assignment Control Plane, Brick Supervisor, Vault for Messaging Tokens (May 18-19, 2026)

**Requires:** New Gee/T install (1.34.1). Standard upgrade flow: Gee/T install restarts daemon, fetches new Gee-Code, and updates. Force-restart if needed.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 18 ~10:19 PM PT.

### Summary
Tickets get a serious lifecycle + authority upgrade. New **Pending lane filter**, **provenance line** on every ticket, **cap-breach trapping**, and explicit **start-now / add-as-objective / approve-and-assign** actions. **Assignment Scope dropdown**, **Trusted Peer Assigners**, and **per-hour/per-day caps** land in mode guardrails — Gees can now assign tickets to themselves or others, scoped from "no self-motivation" all the way to "motivate the entire system." Net: a complete end-to-end system for Gees to autonomously (or with human intervention) drive work. Short and long-running operations now use tickets consistently — Gees keep continuity, communication, and coherence across both. **Messaging tokens move into the Credentials Vault** (Telegram / Slack / Discord secrets no longer in plain config). **Realtime Voice becomes its own entitlement** (admin grant/revoke independent of credits; falls back to credits if no explicit flag). **Live Voice Strip** ships — sticky band above the prompt with state dot, partial transcript, and a 14-bar mic-driven waveform; routes `realtime_not_entitled` inline. **Brick supervisor on boot** — each Brick's declared `runtime.services` autostarts once per cold start. Polish: Brick review panel closes on Accept (no more stuck overlay), ConnectorsPanel surfaces legacy inline messaging tokens with a badge + option to migrate to Vault.

### 🎯 Most Impactful For You

1. **Ticket assignment control plane** ⭐ — The big one. **Trusted Peer Assigners** + **per-hour/per-day caps** in mode guardrails means you can let mg autonomously kick off NLYM Pay Voucher support work, or let gtek pull tickets from you, without spinning up unbounded delegations. This is the missing safety rail for autonomous Gee-to-Gee work.
2. **Short ↔ Long running ops unified on tickets** — Gees now use tickets consistently for both. Translation: Pay Voucher pilot biweekly support cycles, GTek client deliverables, and personal multi-day learning loops all get the same continuity, communication, and coherence guarantees. No more "wait, what state was that delegation in?" moments.
3. **Messaging tokens in Credentials Vault** — Same posture as BYOK API keys. Telegram/Slack/Discord secrets out of plain config files. Aligned with the commercial-terms / post-credential-leak hardening posture. **Migrate the Telegram token used by heartbeat/scheduled SendMessage.**
4. **Brick supervisor on boot** — When you build a Brick (Pay Voucher operator surface, GTek dashboard), its declared services autostart on cold boot. Hands-off Brick runtime, no "did I start that?" overhead.
5. **Realtime Voice as its own entitlement** — Admins can grant or revoke independent of credits. Cleaner separation of concerns: turn it off for client-sensitive modes without touching the credit pool.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Pending lane filter + provenance line** | Filter tickets to the pending lane; every ticket shows where it came from. | Cleaner triage of inbound work. |
| **Cap-breach trapping** | Tickets that exceed configured caps get trapped before they fire. | Hard safety rail for autonomous delegation. |
| **Start now / Add as objective / Approve & assign** | Explicit one-click actions from the pending lane. | One-click conversion of intake → work. |
| **Assignment Scope dropdown** | Pick who a ticket can be assigned to. | Authority scoping for Gee-to-Gee handoff. |
| **Trusted Peer Assigners** | Per-mode whitelist of peers that can assign tickets to you. | Controls who can wake which Gee. |
| **Per-hour / per-day caps in guardrails** | Mode-level limits on how often a Gee can be activated. | Stops runaway loops; budgets autonomous work. |
| **Gee-to-Gee ticket assignment (permissive levels)** | From "no self-motivation" → "motivate entire system." | End-to-end autonomous driving of work with explicit authority limits. |
| **Short ↔ Long running ops on tickets** | Both operation classes use tickets consistently. | Continuity across operation lengths. |
| **Messaging tokens in Credentials Vault** | Telegram / Slack / Discord secrets move to vault. | Out of plain config; commercial-terms aligned. |
| **Realtime Voice entitlement** | Independent flag; falls back to credits if unset. | Admin-controlled voice access. |
| **Live Voice Strip** | Sticky band above prompt: state dot, partial transcript, 14-bar mic-driven waveform. Reflects real RMS while listening, breathing while speaking. Routes `realtime_not_entitled` inline. | Visible feedback for realtime voice state; no generic error. |
| **Brick supervisor on boot** | Each Brick's `runtime.services` autostarts once per cold start. | Hands-off Brick runtime. |
| **Brick review panel closes on Accept** | No more stuck overlay. | Polish. |
| **ConnectorsPanel legacy token badge** | Inline messaging tokens flagged with a badge + "move to Vault" option. | Migration path for old installs. |
| **Stable conversational context across short/long ops** | Continuity guarantee across operation lengths. | Less context loss on long delegations. |

### ⚠️ Caution

- **Assignment caps need calibration** — Set conservative per-hour/per-day caps in `mg` guardrails *before* enabling autonomous assignment. Start low; raise after observing real volume.
- **Trusted Peer Assigners is an authority surface** — Only whitelist peers you actually want waking this Gee. Don't reflexively add all siblings; gtek is the only one that makes sense for mg right now.
- **Migrate inline messaging tokens to Vault** — Use the new ConnectorsPanel badge to move the Telegram token (used by heartbeat/scheduled `SendMessage`) out of plain config. Don't leave it inline.

### ✅ To Explore

- [ ] Set per-hour/per-day caps in `mg` mode guardrails — start conservative
- [ ] Configure Trusted Peer Assigners for mg (likely just `gtek` for now)
- [ ] Try the Pending lane filter + provenance line on the next inbound ticket
- [ ] Migrate the Telegram token from inline config to Credentials Vault
- [ ] Confirm Realtime Voice entitlement state on the Edenic-account Anthropic key
- [ ] Watch for the Live Voice Strip next time you click the mic in Pretext
- [ ] (When you build a Brick) declare `runtime.services` in `brick.yaml` and verify supervisor autostart on cold boot

---

<a name="v0630"></a>
## 🚀 GeeCode 0.63.0 + Gee/T 1.34.0 — Bricks-Owned Bug/Feature Intake, Realtime Voice, Phone Improvements, Ticket Lifecycle (May 17, 2026)

**Requires:** New Gee/T install (1.34.0). Standard upgrade flow: Gee/T install restarts daemon, fetches new GeeCode, and updates. Force-restart if needed.
**Impact level:** 🔴 High (114 commits)
**Posted:** Neil, Gee Test (Core), May 17 ~9:43 AM PT.

> ⚠️ **Version-number sanity check:** Neil's headline labels these as "GeeCode (1.34.0) & Gee/T (1.63.0)" but the body says "Gee 0.63.0 / Terminal 1.34.0." The body is canonical — SelfStatus on this machine confirms `gee-code v0.63.0`. Same Neil-transposition pattern as the May 12 release. **Trust the body, not the headline.**

### Summary
The Bug Report and Feature Request system was refactored to use the Bricks framework as an end-to-end test of how a user could build a functioning system from the components. The Brick system now owns Bug & Feature intake: `/br` and `/fr` flow through GTX (Gee Ticket Exchange — a mechanism for tickets to be handed off across IP boundaries) → user's Brick → back to sender. Experimental Realtime Voice preview lands in the Pretext panel (mic button left of `>`); Gee's voice + identity can control the surface. Big improvements in inbound phone calling — works much better on speaker phone in car, can transfer between Gees, voice parameters editable in Activation matrix. Long-running ticket polish: implicit-final closure ends "phantom activations," per-thread artifact ledger ends "phantom attachments." Plus many QoL and bug fixes.

### 🎯 Most Impactful For You

1. **Inbound phone improvements (car / speaker phone / Gee-to-Gee transfer)** ⭐ — Direct fit for Mariciel's actual life: driving Luke, juggling NLYM/Edenic/GTek between school pickup and meetings. Speaker-phone reliability + the ability to transfer between Gees (mg → gtek for a client question, e.g.) turns the phone into a real working surface, not just a dictation channel.
2. **Realtime Voice preview in Pretext** — Click the mic left of `>` in the Pretext panel. Gee's voice + identity can control the surface. Worth a low-stakes test in mg mode before relying on it for anything billable.
3. **Long-running ticket lifecycle fixes** — Implicit-final closure removes "phantom activations" (tickets that kept re-firing); per-thread artifact ledger removes "phantom attachments." If you've noticed delegations seemingly re-running or attachments showing up in weird threads, this is the fix.
4. **Bricks-owned Bug/Feature intake (`/br` / `/fr`)** — Mostly system-internal, but conceptually it's a worked example: a real production system built end-to-end on the Bricks framework. If/when you build your own Brick (e.g., NLYM Pay Voucher surface or a GTek client dashboard), the `/br` `/fr` flow is the canonical reference.
5. **Activation matrix voice parameters** — Edit voice + style guidance for Phone & Realtime Voice per-Gee. Means mg can sound different from gtek on a phone call without you reconfiguring at runtime.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Bricks-owned Bug/Feature intake** | `/br` and `/fr` flow through GTX (Gee Ticket Exchange) → your Brick → back to sender. End-to-end test of user-buildable systems on the Bricks framework. | Reference implementation for building your own Bricks. Bugs/features now cross IP boundaries cleanly. |
| **Experimental Realtime Voice preview** | Click the mic in the Pretext panel (left of `>`). Gee's voice + identity can control the surface. | Voice-driven control of Pretext surfaces — early preview, worth testing. |
| **Inbound phone improvements** | Call the number you text. Much better on speaker phone in car. Can transfer between Gees. | Phone becomes a real working channel for driving / mom-mode. mg ↔ gtek handoffs over a single call. |
| **Activation-matrix voice parameters** | Edit voice parameters for Phone & Realtime Voice per-Gee (style guidance). | Per-Gee voice + tone tuning. |
| **Long-running tickets: implicit-final closure** | No more phantom activations after a ticket should have ended. | Delegations stop silently re-firing. |
| **Per-thread artifact ledger** | Ends "phantom attachments" — attachments stay scoped to the thread they belong to. | Cleaner artifact accounting on multi-Gee work. |
| **Many QoL + bug fixes** | 114 commits worth. | General reliability lift. |

### ⚠️ Caution

- **Realtime Voice is experimental ("preview")** — Don't put it on a client-facing path until you've tested it on personal/Gee-dev work. Same boundary discipline as the ChatGPT Plus / Codex decision.
- **Phone transfer between Gees** — Confirm that mg → gtek transfer respects entitlement boundaries. Client-sensitive callers should land on gtek directly, not bounce through mg first.
- **Headline vs body version numbers** — Use `/version` after upgrade. Trust `0.63.0 / 1.34.0` (body), ignore `1.34.0 / 1.63.0` (headline).

### ✅ To Explore

- [ ] Test inbound phone on speaker phone in car — try a mg ↔ gtek transfer mid-call
- [ ] Try Realtime Voice preview in Pretext (mic button) on a low-stakes task in mg mode
- [ ] Edit voice parameters for mg in Activation matrix — confirm mg sounds different from gtek
- [ ] Trigger a `/br` to see the new GTX flow end-to-end
- [ ] Verify long-running delegations no longer phantom-activate (rerun a Pay Voucher pilot ticket and watch the activation log)
- [ ] Confirm `gee-code --version` and Gee/T `/version` both report the canonical numbers

---

<a name="v1333"></a>
## 🚀 GeeCode 1.33.3 + Gee/T 1.62.0 — Long-Running Tickets, BYOK Vault, Gee Wizard, OpenClaw (May 12, 2026)

**Requires:** New Gee/T install (1.62.0). The Gee/T install should restart the daemon, fetch the new GeeCode, and update. If not: force-restart the daemon and/or fully exit Gee/T and relaunch after the downloader updates it.
**Impact level:** 🔴 High
**Posted:** Neil, Gee Test (Core), May 12 ~11:17 PM PT.

> ⚠️ **Version-number sanity check:** Neil's message labels these as "GeeCode (1.33.3) & Gee/T (1.62.0)" — but the prior tracker entry had GeeCode at 0.61.0 and Gee/T at 1.33.1. The "1.33.3" number almost certainly belongs to Gee/T (post-1.33.1), and the GeeCode number is likely a new 0.6x. **Verify with `/version` after install** and correct this entry.

### Summary
Long-running tickets become first-class lifecycle objects — they can now be handed between Gees and humans and tracked through full adjudication to completion. BYOK (Bring-Your-Own-Key) support lands in the Credentials Vault, with the entitlements system respecting user-supplied keys. A new Gee Wizard ships, hooked into Gees with either a base scaffold or AI-supported creation that detects the system configuration. OpenClaw is robustified — Claws are back and re-mated with Gees. Gee/T finally restores panels stably on reboot and runs more memory-efficiently.

### 🎯 Most Impactful For You

1. **BYOK in Credentials Vault** ⭐ — Mariciel's commercial-terms posture aligns perfectly here. Add the Edenic-account Anthropic API key to the vault and entitlements should respect it for client-sensitive work, rather than routing through managed-model defaults. **This is the feature to test first.**
2. **Long-running tickets adjudicated through completion** — Gee↔Human/Gee handoff with lifecycle tracking. Directly relevant to NLYM Pay Voucher pilot support workflows, GTEK client deliverables, and any multi-day delegation that previously fell off the canvas.
3. **New Gee Wizard** — Lower friction for spinning up additional gees as the workload grows (e.g., a dedicated NLYM treasurer gee post-July 1). AI-supported creation that reads system config means less hand-rolled mode.json wiring.
4. **OpenClaw robustification** — If OpenClaw was on the unstable list, it's worth re-checking integrations.
5. **Stable panel restoration** — Direct fix for the v1.33.0 blank-panel-on-boot class of bug. Memory efficiency improvements mean longer Gee/T sessions without restart.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Long-running tickets adjudicated through completion** | Tickets can be handed between Gee ↔ Human/Gee; full lifecycle tracking through resolution | Multi-day delegations stop falling off the canvas |
| **BYOK in Credentials Vault** | Add your own keys to the vault; entitlements system respects them | Commercial-terms work uses *your* API key, not the managed default |
| **New Gee Wizard** | Hooked into Gees; base scaffold OR AI-supported creation that detects system config | Friction down for adding new gees |
| **OpenClaw robustification** | Claws "back and happily mated with Gees" | OpenClaw integrations reliable again |
| **Stable panel restoration on reboot** | Gee/T restores panels correctly; memory-efficient | Direct fix for v1.33.0-class regressions |

### ⚠️ Caution

- **Verify the actual version numbers** with `/version` after install. Neil's labeling appears swapped.
- **BYOK behavior** — Confirm which lanes/entitlements respect the BYOK and which still go through managed defaults. Test with a non-sensitive call first before routing client work.
- "Lingering bugs in Gee/T" were mentioned in the May 11 patch note; some may still be present in 1.62.0.

### ✅ To Explore

- [ ] **Test BYOK first** — Add Edenic Anthropic API key to Credentials Vault, run a lane that should pick it up, confirm entitlements route through BYOK (not managed default)
- [ ] Verify version numbers with `/version`; correct this tracker entry
- [ ] Place a long-running delegation and confirm it tracks through completion across a Gee↔Human handoff
- [ ] Try the new Gee Wizard for a small scaffold gee (low-stakes test before NLYM treasurer gee)
- [ ] Reboot Gee/T and confirm panels restore cleanly
- [ ] Re-check OpenClaw if previously flaky

---

<a name="v0610-patch"></a>
## 🩹 GeeCode + Gee/T Patch — Ticketing Regression Fix (May 11, 2026)

**Impact level:** 🟡 Medium (bug fix)
**Posted:** Neil, Gee Test (Core), May 11 ~11:23 PM PT.

### Summary
Quick double-fix release. GeeCode patch addresses a regression in the ticketing system. Gee/T patch fixes the issue where spaces were disconnecting/reconnecting or failing to connect. Neil flagged "still some lingering bugs in Gee/T" to be cleaned up the following day — which became the May 12 1.62.0 release.

### What Was Fixed

| Issue | Fix |
|---|---|
| Ticketing regression in GeeCode | Resolved in patch |
| Gee/T spaces disconnect/reconnect or fail to connect | Resolved in patch |

### ⚠️ Caution

- Neil explicitly said lingering Gee/T bugs would land the next day — this patch was a stabilizer, not a stopping point. Move forward to **1.62.0** (May 12 release above).

---

<a name="v0610"></a>
## 🚀 v0.61.0 + Terminal v1.33.1 + iOS Pretext — Entitlements, Discord, CLI Marketplace, Bricks (May 9-10, 2026)

**Requires:** New Gee/T install (1.33.1, **not** 1.33.0 — that build was pulled). Daemon restart. iOS TestFlight Pretext update.
**Impact level:** 🔴 High
**Heads-up from Neil (May 9 ~4:30 PM PT):** v1.33.0 was published then immediately flagged 🚨 *"DON'T INSTALL THIS VERSION"* — panels loaded blank on boot (restore-on-boot bug, sessions were fine). All-clear came May 9 ~10:07 PM PT with **v1.33.1**: *"Issue addressed — new version is good to install."*

### Summary
Big functional release. Managed-model entitlements are enforced at runtime — clamping is no longer a manual user concern; the system grants/enforces per-lane entitlements and refuses to boot lanes on un-entitled models. Discord ships as a first-class user channel (DMs and @-mentions create tickets, dedicated activation lane, wizard connector). The CLI marketplace lands — gees can discover, audit, install, and trust CLIs from the Printing Press Library (~50 tools across travel, commerce, SEO, dev, finance, research). Bricks 0.5/0.6 introduce reusable "Your Software, Your Service" building blocks with intake flow, evolution handoff from Pretext, and live operator surfaces. Outbound phone calls reach GA — Grok Voice 1.5 + GPT Realtime 2 power both inbound and outbound, integrated into the ticket system. Delegation lifecycle is reliable end-to-end. Plus daemon hardening (memory maintenance in subprocess, no more SIGSEGV cascades), per-gee Telegram token scoping, runtime doctor, terminal-state leak fixed.

Neil's framing: *"You no longer need to clamp. Gee can acquire specialized CLIs as a task demands them. The shift is from using someone else's Software-as-a-Service to building Your Software, Your Service."*

### 🎯 Most Impactful For You

1. **No more clamping** — Entitlements enforce model/provider correctness automatically. One less thing to remember; one less way to accidentally burn budget on the wrong model.
2. **Bricks (0.5 + 0.6)** — Reusable building blocks that turn workflows/data/know-how into Gee-runnable software. NLYM Pay Voucher operator surfaces, Edenic deal trackers, GTEK client dashboards are now natural Bricks candidates. Worth a learning session before standing up the next custom workflow.
3. **CLI marketplace** — Gees can pull in specialized CLIs (finance, research, productivity, archives) on demand. Audit/install/trust flow stays explicit. Useful as the Edenic and GTEK workflows mature.
4. **Discord as first-class channel** — DMs and @-mentions create tickets, replies thread correctly. NLYM Discord-first chapters (if any go that route) and Edenic deal rooms can now have a dedicated gee identity.
5. **Outbound calling GA** — A gee can place a call, talk to a human, and relay the answer back into the ticket. NLYM treasurer outreach, GTEK client check-ins, Edenic LP coordination all become delegated voice work.
6. **Delegation lifecycle reliability** — `delegation_resolved` emits on timeouts and pre-activation paths; canvas surfaces stop holding stuck input locks. Big quality-of-life for long-running mg workflows.
7. **Daemon won't die from memory maintenance** — Maintenance runs in a subprocess; SIGSEGV no longer takes down the daemon and websocket. Less mystery downtime.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Managed-model entitlements** | Runtime checks fail closed; lanes refuse to boot on un-entitled models; denials surface as incidents | Clamping is obsolete — system enforces correctness |
| **Discord first-class channel** | DMs + @-mentions create tickets, dedicated Discord activation lane, wizard connector | Same shape as Slack/Telegram — per-gee or prime-gee patterns supported |
| **CLI marketplace** | Curated 31-CLI manifest + Printing Press Library (~50 tools), install/audit/trust flow, MCP sidecar registration, native-tool precedence | Active toolbelt is no longer limited to what shipped in the wheel |
| **Bricks 0.5 + 0.6** | Net-new brick creation with intake flow, "New Brick" file menu entry, authoring handoff, Pretext evolution-handoff gesture | First-class "Your Software, Your Service" primitive |
| **Outbound phone GA** | Grok Voice 1.5 + GPT Realtime 2 for inbound and outbound; gee-initiated calls are ticket-backed; delegated voice tasks | Calls become tracked work units within long-running objectives |
| **Memory maintenance subprocess** | SIGSEGV in maintenance no longer takes down daemon + companion WebSocket | Daemon stability up materially |
| **Autonomous delivery hardening** | Route context preserved, late WIP suppressed after final delivery, delegation lifecycle progress reaches canvas | Final-reply correctness end-to-end |
| **Per-gee Telegram token scoping** | Generic triggers can't borrow another gee's legacy token; routed cross-gee replies land via the polling owner | Cleaner cross-gee identity boundaries |
| **Delegation lifecycle reliability** | `delegation_resolved` emits on timeouts and pre-activation paths | Canvas surfaces stop holding stuck input locks |
| **Credentials guidance pinned** | GetCredential/ListCredentials self-identify as the first stop | Gees stop trying to read encrypted credentials.json directly |
| **Runtime doctor** | First-run diagnosis is friendlier; pipe-startup handling for non-interactive launches | Lower setup friction |
| **Terminal-state leak fixed** | Final replies no longer contain internal "current state matches the done-state…" verification text | Cleaner user-facing replies |
| **Per-lane model selectors autosave** | Clamp/Fallback and per-activation-lane dropdowns persist on change | No more "I thought I saved that" |
| **Ticket list pagination** | 50-row IntersectionObserver-driven infinite scroll | Busy queues stay responsive |
| **Pretext link actions** | Link context menu, hit-testable code-block paths/URLs, header display-name toggles, split-open routing | More natural link/file interactions |
| **Pretext scrollbar draggable + tickets toggle** | Two persistent UI papercuts gone | Smoother day-to-day Pretext use |
| **Auth status polling faster** | Quieter background work in long-running sessions | Less ambient overhead |
| **iOS inline media + tappable links** | Generated media renders inline; mobile media + shared Pretext URLs are tappable | No out-of-app round trip on mobile |
| **iOS streaming steadier** | Improved mobile Pretext streaming behavior | Mobile becomes a reliable secondary surface |
| **iOS processing pin masking** | Pin's surface fill covers pin band, composer reserve, and bottom chrome reserve | Cleaner mobile transcript |
| **iOS WIP off reply channel** | Progress no longer leaks into user-visible reply stream on mobile | Mobile final replies stay clean |
| **Misc papercuts** | Deep memory search restored, PUT API requests preserved, PEP 668 installer fix, secret archives ignored | Quality-of-life |

### New Commands / Capabilities

- **Bricks:** `New Brick` from the Pretext file menu; "evolve this" handoff gesture from any direction in Pretext.
- **CLI marketplace:** `cli` skill auto-discovered by gees with native-tool precedence; install/audit/trust flow available before execution.
- **Discord activation lane:** Same shape as Slack/Telegram/SMS in Agents panel; duplicate AutonomyPanel removed.
- **Outbound voice:** Gee places call → ticket created → ticket tracks call lifecycle → result threaded back.

### ⚠️ Caution

- **DO NOT install Gee/T 1.33.0** — that build was pulled (blank-panel restore-on-boot bug). **Use 1.33.1 or later.** If you somehow installed 1.33.0, panels will load blank but sessions are intact; updating to 1.33.1 fixes it.
- **Outbound voice still being tuned** — Neil flagged ongoing refinement of barge-in, speaker-turn detection, and background-noise normalization. Use for low-stakes calls first.
- **Bricks are 0.5/0.6** — first cut. Expect API/UX evolution. Treat early Bricks as throwaway prototypes until 1.0.
- **CLI marketplace trust is explicit** — discover everything, execute nothing until installed/audited/enabled. Don't approve CLIs reflexively.

### ✅ To Explore

- [ ] Update Gee/T to **1.33.1** (verify with `/version`); restart daemon
- [ ] Stop manually clamping; verify entitlements enforce on a mode that should reject a non-entitled model
- [ ] Test Discord connector if relevant (Edenic deal rooms? NLYM chapter coordination?)
- [ ] Try one Brick — small operator surface for an existing recurring workflow (e.g. NLYM Pay Voucher pilot status panel, Edenic monthly portfolio refresh)
- [ ] Browse the Printing Press CLI catalog — pick 1-2 tools that map to current work (research, finance, productivity)
- [ ] Place a low-stakes outbound call to validate voice quality + ticket lifecycle
- [ ] Confirm canvas surfaces no longer hang waiting for delegation resolution on a timed-out delegate

---

<a name="v0602"></a>
## 🩹 v0.60.2 + Terminal v1.32.1 — Reliability Follow-up (May 7, 2026)

**Requires:** Update Gee/T (should auto-update Gee-Code; verify with `/version`). Restart daemon if stale.
**Impact level:** 🟡 Medium
**Heads-up from Neil (May 7 ~8 AM PT):** *"Tracking down some unstableness in the latest gee/t — seems leaky. Stay tuned."* — expect a v0.60.3 patch shortly.

### Summary
Stability-and-hardening release on top of v0.60.0. Tightens ticket-aware execution end-to-end (delegation, daemon work, external requests, terminal replies, SendMessage all share explicit ticket lifecycle). Per-gee bot identity for Slack **and Telegram** with route context preserved. Outbound phone work, daemon login, and activation routing now integrate with tickets. Native tools exposed through MCP; CLI skill discoverable with native-tool precedence; PEP 668 install handling. Plus iOS layout/framerate fixes and the iOS share extension working again.

### 🎯 Most Impactful For You

1. **Terminal replies no longer close tickets early** — WIP/interim messages stop accidentally marking tickets/activations done. Big for mg's interim "still working" sends during long-running work.
2. **Phone-call work is ticketable** — Outbound voice flows create, route, track, and close work like other requests. Useful when MG calls on your behalf during NLYM/GTEK coordination.
3. **iOS sharing works again** — Share-sheet into the iOS app is fixed; combined with framerate/layout improvements, mobile Pretext is more usable for between-meeting checks.
4. **Per-gee Telegram bot tokens** — Telegram now matches Slack: connector tokens scoped per gee with route context preserved. Cleaner mg vs. gtek separation on Telegram.
5. **CLI Registry** — New registry exposing common/useful CLIs. Worth exploring as you build more automation.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Ticket-aware execution end-to-end** | Delegation, daemon work, external requests, terminal replies, SendMessage all share explicit ticket lifecycle | Tickets/activations no longer get closed by WIP messages |
| **Per-gee Slack + Telegram bot identity** | Connector tokens scoped per gee; route context preserved through reply paths | Right gee replies from the right identity in both Slack and Telegram |
| **Mobile Pretext final-reply delivery** | Route-context kwargs accepted for final reply delivery; background push works | Mobile gets final answers reliably even when webview is backgrounded |
| **Outbound phone work tracked** | Voice flows integrate with ticket substrate | Calls become trackable work units |
| **Daemon login + activation routing** | Cleaner authenticated runtime posture; activation routing integrates with tickets | Long-running gees have explicit auth state |
| **Phone call quality** | Better noise cancellation + turn waiting | Cleaner voice calls |
| **Native tools through MCP** | Native tools exposed via MCP; CLI skill discoverable with native-tool precedence | Better cross-tool reachability |
| **PEP 668 install handling** | Installer respects externally-managed Python environments | Fewer install failures on modern Python |
| **Worker failure routing** | Failure results preserve delivery routes | Errors get back to the right surface |
| **Gateway attachments** | Body and attachments split only after stream finalization | Cleaner attachment delivery |
| **BYOP output dedup** | Duplicate final text suppressed when only whitespace diverges | Less noise in final replies |
| **GitHub intake state sync** | Linked ticket state follows issue state changes | Tickets/issues stay in sync |
| **iOS layout + framerate** | Layout improvements + framerate fixes | Smoother mobile Pretext |
| **iOS share extension** | Sharing into the iOS app works again | Mobile workflow restored |

### ✅ To Explore

- [ ] Check `/version` after update — should report 0.60.2 / 1.32.1
- [ ] Restart daemon and `/restart` Pretext panels (Farshid hit a stuck-version bug — see `/restart` follow-up below)
- [ ] Watch for v0.60.3 — Neil flagged unstableness in v0.60.2 he's already chasing
- [ ] Test iOS share extension on a useful link
- [ ] If using Telegram with multiple gees, verify per-gee bot identity routing

### ⚠️ Known Issues

- **Stuck version on Pretext spaces** — Farshid reported (May 7) that only Terminal spaces update on launch; Pretext spaces don't update, `/restart` in Pretext yields no update, ⌘R is greyed out in menu. Neil's diagnosis: `/restart` uses `os.execv(sys.executable, ...)` which re-execs with the same Python interpreter — site-packages are cached at process start. Workaround: full daemon restart from terminal.
- **General leakiness in gee/t** — Neil tracking down. Patch expected.

---

<a name="v0600"></a>
## 🚀 v0.60.0 + Terminal v1.32.0 + iOS TestFlight 27 — Ticket-Aware Execution + Outbound Calls (May 5, 2026)

**Requires:** Daemon restart + new Gee/T install + iOS TestFlight v27
**Impact level:** 🔴 High

### Summary
Big functional release — operationalizes the Tickets and Events substrates that debuted in v0.59. Ticket-aware execution is now end-to-end: delegated work, daemon runs, external requests, and final replies share one lifecycle. Redis-backed ticket events are first-class — CLI, daemon, companion, and UI processes stay in sync on request state. Final replies are explicit (WIP/interim no longer accidentally close tickets). Slack per-gee bot identities ship — each gee replies from the right Slack identity with preserved route context. Outbound phone calls land — gees can make calls on your behalf, tracked as ticketable work. Mobile Pretext gets background final-reply push. Plus OpenAI Responses recovery, MCP/native tool fixes, reference autonomy examples packaged, and Slack/SMS/Telegram activation defaults aligned.

Neil's framing: *"Functionality and tightening of all the features we debuted on Sunday, plus the ability for Gees to make outbound calls on your behalf."*

### 🎯 Most Impactful For You

1. **Outbound calls — Gees can call on your behalf** — Phone calls become ticketable work. NLYM chapter treasurer support, GTEK client check-ins, Edenic coordination calls all become routable, trackable work.
2. **Ticket-aware execution end-to-end** — One lifecycle across delegation, daemon work, external requests, terminal replies, SendMessage. Cleaner Pay Voucher pilot support workflows when you wire ReportBug into the pilot.
3. **Final replies are explicit** — WIP/interim messages no longer close tickets. mg's "still working" sends won't accidentally mark activations done.
4. **Slack per-gee bot identity** — When Edenic Slack workflows go live, each gee replies from its own bot identity with route context intact.
5. **Mobile Pretext background push** — Final answers reach iOS even when the app is backgrounded. Useful for delegated work that finishes while you're in a meeting.
6. **Reference autonomy examples packaged** — Heartbeat, pure responder, schedule-only patterns are now easier to study and copy. Useful as you build more autonomous Gees.
7. **Per-venue suggestions controllable** — `/suggestions [on|static|off]` per surface. Turn off the ticker where it distracts, leave it on where it helps.

### What's New

| Feature | What it does | Why it matters |
|---|---|---|
| **Ticket-aware execution end-to-end** | Delegation, daemon runs, external requests, final replies share one lifecycle | One mental model across all execution paths |
| **Redis-backed ticket events** | CLI, daemon, companion, UI processes stay in sync on request state | First-class request-state coordination across processes |
| **Explicit final replies** | WIP/interim no longer closes tickets/activations | Long-running tasks track correctly |
| **Outbound phone calls** | Gees can make calls on your behalf, ticket-tracked | Calls become routable trackable work |
| **Slack per-gee bot identity** | Each gee replies from the right Slack identity, route context preserved | Multi-gee Slack setups stay disambiguated |
| **Slack threading/routing sturdier** | Per-bot replies route through SendMessage with context attached | Slack reply paths preserve context |
| **Slack etiquette + channel context tools** | `SlackChannelContext` + better answer awareness | Gees answer Slack with channel context |
| **Daemon login groundwork** | Long-running gees have a clearer authenticated runtime posture | Auth posture clarified for autonomous gees |
| **Mobile Pretext background final-reply push** | Final answers reach mobile even when webview is backgrounded | Delegated work completes visibly on phone |
| **Mobile session/model selection improved** | iOS/mobile Pretext can switch sessions and models more safely | Cleaner mobile multi-session work |
| **Per-venue suggestions** | `/suggestions [on|static|off]` controls suggestion ticker per surface | Quiet surfaces where suggestions distract |
| **OpenAI Responses recovery** | Orphaned tool-output 400s are handled instead of stranding runs | Fewer stuck runs from OpenAI provider |
| **MCP/native tool discovery** | Native tools exposed through MCP; iMessage chat alias tolerated | Better tool reachability |
| **Reference autonomy examples** | Heartbeat, pure responder, schedule-only patterns packaged | Copyable templates for new autonomous gees |
| **Cost analyzer enterprise access** | Edenic slug checks match real DynamoDB state; denials log why | Less brittle Edenic enterprise gating |
| **gee-t Slack connector setup** | Connector wizard/panel polish + cleaner messaging rows | Easier Slack setup |
| **gee-t tickets denser** | Stable short IDs + single-row layout | Busy ticket queues scan faster |
| **gee-t markdown previews** | Plans and reports render as markdown by default; raw source still available | Readable-first artifact opening |
| **gee-t webviews** | Fixed UA + popup handling; behaves more like Chrome | Fewer embedded-browser oddities |
| **gee-t activation profiles** | Custom data lives behind a dedicated modal | Cleaner activation profile management |
| **Slack/SMS/Telegram activation defaults aligned** | Channel activations start closer to right runtime posture | Less per-channel surprise |

### New Commands / Tools

| Command | What it does | When to use it |
|---|---|---|
| `/suggestions [on\|static\|off]` | Per-venue control of suggestion ticker | Quiet surfaces where it distracts |
| Outbound call (via gee) | Gee places phone calls on your behalf | Delegated coordination calls |

### ⚠️ Caution

- **Auto-update on Gee/T boot is new and "needs testing"** — Neil flagged that Gee/T will look for newer Gee-Code on boot and try to restart daemon + Pretext. May or may not work. Belt-and-suspenders: restart daemon manually + `/restart` Pretext + install new iOS TestFlight.
- **iOS sharing broken in v27** — Fixed in v0.60.2 (May 7).

### ✅ To Explore

- [ ] Confirm `/version` shows 0.60.0 (or 0.60.2 if already past)
- [ ] Try `/suggestions off` on a Pretext panel where the ticker is noisy
- [ ] Read the packaged reference autonomy examples (heartbeat, pure responder, schedule-only) — useful as you build more gees
- [ ] If you want outbound calls, test with a low-stakes call first
- [ ] iOS TestFlight v27 — install if you haven't

---

<a name="v0590"></a>
## 🚀 v0.59.0 + Terminal v1.31.0 + iOS TestFlight 0.26 — Events System, Tickets, Mobile Pretext (May 3, 2026)

**Requires:** Daemon restart + new Gee/T install
**Impact level:** 🔴 High

### Summary
Massive release. Three big new substrates land at once: (1) **Durable Events System (Beta)** — Gee can watch real-world signals (live flight ETAs, etc.) and trigger actions when conditions fire. Full event substrate, dispatch, watcher registry, and lifecycle policy. (2) **Canonical Tickets + Product Intake (Beta)** — bug reports, feature requests, approvals, and objectives all flow through one ticket substrate that projects to GitHub and routes to specific Gees via labels. (3) **Mobile Pretext (Alpha)** on iOS TestFlight — full Gee-Code on phone, segmented by your autonomous Gees into discrete channels, with HealthKit, voice dictation, native attach sheet. Plus xAI/Grok realtime phone voice, semantic search in GeeCloud + Google Drive, Pure REPL with auto skill promotion, and Telegram threading fixes.

Neil's framing: *"These are powerful new substrates that unlock Gee's potential to run organizations and their workflows."* He flagged he'll *"refine & robustify this week"* — expect rough edges.

### 🎯 Most Impactful For You

1. **Tickets system + ReportBug / ReportFeature / SubmitProductReport** — Big upgrade for project tracking. NLYM Pay Voucher bugs, GTEK client requests, Edenic action items can flow through one canonical ticket substrate that auto-projects to GitHub and routes to the right Gee via labels. `⌘⇧T` opens the Tickets panel. Worth wiring into your Pay Voucher pilot support workflow once stabilized.
2. **Mobile Pretext (Alpha) — iOS TestFlight v0.26** — Full Gee-Code on phone with each autonomous Gee in its own channel. Press-and-hold the `+` button for voice dictation. Useful for between-meeting checks on NLYM, Edenic, GTEK matters. Still Alpha — Neil's words: *"doesn't compete with Telegram, except that Gees have their own channels."*
3. **`!!health` on iOS** — Connects Apple Health to mg/Gee-Code. Could surface sleep/activity/recovery context into mg's daily briefings if you want it.
4. **Semantic search in GeeCloud + Google Drive** — `cloud_files_list --search/--semantic` does semantic search across cloud files. Big win for finding Edenic deal docs or GTEK contracts when you don't remember the exact filename.
5. **Durable Events System** — Watcher-based triggers tied to real-world signals. Demoed with a live flight-ETA watcher (Gee called Neil 30 min before landing). Forward-looking application: NLYM Pay Voucher uptime watchers, GTEK deadline events, Edenic deal milestone triggers. Beta this week.
6. **Telegram replies thread back to originating activation** — Replies now thread into the right activation instead of starting fresh. Cleaner async context for mg Telegram briefings.
7. **Status bar reflects live `/model` switches** — When you swap models mid-session inside a mode, the bar updates immediately. Useful when juggling fast/cheap vs. full models across a long session.
8. **CWD resolves from spawning panel (PR #100)** — Continued work on the working-directory fix from v0.57. "This directory" continues to mean what you're looking at.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Durable Events System (Beta)** | Substrate + dispatch + outbound action execution + watcher registry + lifecycle policy. Events agent tool (list_kinds/list/get/upsert/patch/start/stop/restart/ensure_defaults). Events tab in Terminal w/ Mode filter. Voice replies route as events for idempotency. | Forward-looking: monitor Pay Voucher uptime, GTEK deadlines, Edenic milestones with watcher-based triggers. Beta — explore but don't depend on it yet. |
| **Canonical Tickets + Product Intake (Beta)** | `gee_code/tickets/` substrate; approvals/objectives/intake all mirror in. ReportBug / ReportFeature / SubmitProductReport tools project to GitHub w/ gee-objective + routing labels. Tickets sidebar + panel (⌘⇧T). Implicit github_issues trigger — every autonomous gee wakes on `gee:NAME` / `team:TEAM` / `all-gees` labels. | Pay Voucher pilot support workflow: ReportBug → GitHub → routed to designated Gee. GTEK client work tracked through tickets. Edenic action items tracked uniformly. |
| **Pure REPL + Procedural Skill Promotion (Experimental)** | New "pure" tier with deliberately small toolset (file primitives, semantic memory, Skill, Discover, Command, instrumented shell_probe). `/promote` + `/candidates` commands. Auto-promotion every 5 turns. BYOP MCP bridges into parent trace via `{session_id}.mcp.jsonl` sidecar. | Learning mode — Gee identifies repeatable patterns and promotes them to durable skills automatically. Forward-looking quality of life. |
| **xAI/Grok realtime phone voice** | New voice provider: grok-voice-think-fast-1.0; `REALTIME_VOICE_PROVIDER=xai`. Pre-warmed provider WebSocket on inbound calls (cuts pickup silence). Named-prime greeting (e.g. "Og"). Twilio "Just a moment, connecting you now" feedback during boot. Async tool results inject as system context, not user input. | Voice calls feel snappier on pickup; no more conversational restarts when Gee runs a tool mid-call. |
| **Mobile Pretext (Alpha) — iOS TestFlight v0.26** | Direct delivery: iOS POSTs `gateway_reply` straight to companion (drops 1 HTTPS hop). HealthKit + Location ports. Native attach sheet (Camera/Photo Library/Files). Voice dictation. Inertial scrolling; keyboard resize stability. Background bookkeeping so ACTIVATION_END fires immediately. | Use mg from your phone. Each autonomous Gee gets its own channel. Voice dictation via press-and-hold `+`. |
| **Conversational continuity** | Channel-thread per-message cap raised 300→4000 chars. Heartbeat activations excluded from inbound-event transcripts via `exclude_types`. usage_context module fix. | Longer messages stay in one piece; less heartbeat noise polluting transcripts. |
| **GitHub-as-substrate** | File-first token store (`~/.gee-code/auth/tokens.dat`) — no more Keychain prompts. Repo-aware `resolve_token_for(repo)` prefers ambient `gh auth`, falls back to Gee bot. `intake/projectors/github.py` syncs projection state into local objectives. `GEE_CODE_TOKEN_STORE=file` and `GEE_CODE_DISABLE_KEYRING` env overrides. | Should resolve the keychain permission loop bug Farshid hit on v0.58. Cleaner auth handling. |
| **Semantic search in GeeCloud + Google Drive** | `cloud_files_list --search/--semantic` flags | Find Edenic deal docs / GTEK contracts by topic, not filename. |
| **Slack connector wizard** | Manifest-driven copyable code blocks, plugin v1.1.0 | Easier Slack connector setup if you want autonomous Gees triggered from Slack. |
| **Google OAuth wizard fix** | React 18 strict mode mountedRef reset (was sticking) | Google OAuth setup actually completes now. |
| **Telegram replies thread back** | Replies route into originating activation | Async Telegram context preserved. |
| **Status bar reflects live `/model` switches** | Live update inside gee modes | Visual confirmation when swapping models mid-session. |
| **Daemon WIP correctness** | Interim sends don't wind down monitor; deliverable=True bypasses heuristic | mg interim "still working" sends don't silence tool logs. |
| **CWD from spawning panel (PR #100 follow-up)** | Continues v0.57 working-dir fix | "This directory" = active panel cwd. |
| **Email /media attachments** | No longer materialize as login HTML | Email attachment handling fixed. |
| **Pretext clipboard** | Table cells serialize correctly to clipboard markdown | Copy-paste from Pretext tables works. |
| **Caret on dimmed collapsed spaces** | Visible on hover | Small UI polish. |
| **Git packfile writes** | Guarded against concurrent-panel corruption | Reduces git corruption risk when multiple panels touch the same repo. |
| **Trader Kalshi fee math** | Proper net-PnL accounting in shadow trades | Niche — only relevant if you're using the trader/Kalshi integration. |
| **Subscription-tier external CLI footer** | Shows both effective + list price | Cost transparency. |
| **cost-analyzer reverse-proxy** | At `/cost-analyzer/*`, gated on Edenic enterprise | Edenic-specific cost tooling. |
| **Provider event payloads** | Sanitized + capped before IPC/log | Cleaner provider logs, less log bloat. |
| **Voice task callback** | Delivery restored; fail-closed if missing callback metadata | Voice routing reliability. |
| **Windows Releases** | `tt-win-release.sh --patch/--minor/--major` ships Windows-only hotfixes (1.30.1 → 1.30.2 → 1.31.0 unified). Windows pipe spawner: PATH delimiter, PATHEXT, install.json gee_code_bin lookup. Help → Check for Updates on non-mac. REPL skips PromptSession in stream-json mode. | Not directly relevant on macOS, but unblocks any Windows users on your team. |

### New Commands / Tools

| Command | What it does | When to use it |
|---|---|---|
| `⌘⇧T` | Open Tickets panel in Terminal | Manage bug reports, feature requests, approvals, objectives in one place |
| `ReportBug` (MCP tool) | Create a GitHub issue for a bug, with optional Gee routing labels | NLYM Pay Voucher bug reports during pilot |
| `ReportFeature` (MCP tool) | Create a GitHub issue for a feature request | GTEK client feature requests |
| `SubmitProductReport` (MCP tool) | Canonical product intake record routed to Gee lanes | Higher-ceremony intake than ReportBug/ReportFeature |
| `/promote` | Promote a procedural candidate to a reusable skill (dry-run by default) | Pure REPL learning workflow |
| `/candidates [--detail]` | List procedural promotion candidates from Layer 5 memory | Pure REPL learning workflow |
| `cloud_files_list --search` / `--semantic` | Semantic search GeeCloud + Google Drive | Find files by topic, not filename |
| `!!health` (iOS) | Connect Apple Health to Gee/Gee-Code | iOS only — Mobile Pretext Alpha |
| Press-and-hold `+` (iOS) | Voice dictation in Gee iOS | iOS only — Mobile Pretext Alpha |
| `REALTIME_VOICE_PROVIDER=xai` (env) | Use xAI/Grok realtime phone voice | Faster voice pickup |
| `GEE_CODE_TOKEN_STORE=file` (env) | File-first token store, skip Keychain | If you hit Keychain permission loops |
| `GEE_CODE_DISABLE_KEYRING` (env) | Disable Keychain entirely | Same — Keychain workaround |

### ⚠️ Caution / Beta

- **Events System** — Beta. Driver coverage is thin (UA1008 flight-ETA watcher is the only real one shipped). Expect rough edges this week.
- **Tickets / Product Intake** — Beta. Tickets are not yet "innately" used by autonomous Gees — Neil notes you may need to brief your Gees on the new system explicitly via the explainer doc.
- **Mobile Pretext (iOS)** — Alpha. Neil: *"still doesn't compete with Telegram, except for the fact that Gees have their own channels."*
- **Pure REPL + Skill Promotion** — Experimental. Auto-promotion every 5 turns is on by default in pure mode.

### ✅ To Explore

- [ ] Run `/restart Gee-Code` and confirm daemon picks up v0.59.0
- [ ] Download new Gee/T install (Terminal v1.31.0)
- [ ] Open Terminal — find the new **Tickets** sidebar/panel (`⌘⇧T`); explore how bugs/features/approvals/objectives mirror in
- [ ] Try **ReportBug** on a real Pay Voucher pilot issue to see how GitHub projection works
- [ ] Install **iOS TestFlight v0.26** if you want phone access; test press-and-hold `+` voice dictation
- [ ] If on iOS, try `!!health` to connect Apple Health
- [ ] Test `cloud_files_list --semantic "edenic deal terms"` (or similar) on your GDrive
- [ ] Confirm Telegram replies to mg now thread into the originating activation
- [ ] Watch the status bar when you `/model` switch inside mg — should update live

### Briefing for autonomous Gees (per Neil's note)

Neil flagged that autonomous Gees aren't innately instructed about the new Events/Tickets system. There's an explainer doc with a briefing section that should be sent to your Gees so they actually start using it. **Action:** ask mg to look for and ingest the events/tickets explainer doc once you have access to it.

---

<a name="v0580"></a>
## 🚀 v0.58.0 + Terminal v1.30.0 — Connector Framework, Slack Inbound, Cloud Files (Apr 30, 2026)

**Requires:** Daemon restart + `/restart Gee-Code` (and `gee-code setup all` if using Cursor agents)
**Impact level:** 🔴 High

### Summary
Big infrastructure release. Three things land that change the surface area: (1) A typed connector plugin framework — adding new connectors is now ~50 lines instead of bespoke code per integration. (2) Slack inbound goes first-class — autonomous Gees can be triggered by Slack messages with multi-user routing. (3) Cloud file browser in The Terminal — Google Drive accounts, folder CRUD, drag-and-drop upload that auto-indexes into RAG. Plus Cursor SDK as a new provider, default model swap to gpt-5-zero on fresh installs, and a stack of correctness fixes.

### 🎯 Most Impactful For You

1. **Cloud file browser + auto RAG indexing** — Drop GTEK contracts, Edenic deal docs, or NLYM policy files into the Terminal file tree, and they get auto-indexed into Gee's knowledge base. Big workflow upgrade for document-heavy work.
2. **Slack inbound listener** — If Edenic or GTEK uses Slack, you can now trigger autonomous Gees from Slack messages. Path-3 Slack is finally first-class.
3. **Telegram decoupled from SMS rules** — Telegram messages from Gee now use rich formatting and attachment-first guidance instead of inheriting SMS terseness. Telegram briefings and reports will be more readable.
4. **WIP monitor correctness** — Only `deliverable=true` sends stop the progress monitor. MG's interim "still working on it" sends won't silence tool logs anymore.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Connector plugin framework** | 9 typed plugins (Slack, Telegram, MCP-stdio, MCP-http, GCP, Codex OAuth, Claude OAuth, Plaid, Google OAuth) on one declarative ConnectorPlugin contract + generic ConnectorWizard | Foundation for fast new integrations — adding a connector ≈ 50 lines |
| **Slack inbound listener** | Socket Mode WebSocket → normalized trigger payload; multi-user routing via slack_user_id → mode | Edenic/GTEK: autonomous Gees triggered from Slack messages |
| **Cloud file browser** | GDrive account switching, folder CRUD, drag-and-drop upload with auto RAG indexing, cached folder lists | Drop deal docs/contracts/policy files, auto-indexed into Gee's RAG. ~3,800 lines net in FileTree |
| **Cursor SDK provider** | Gee owns outer session/context/MCP tools; Cursor handles inference. composer-2 cloud / auto local | New backend option for code-heavy work |
| **Default model: gpt-5-zero** | Fresh installs use API-backed OpenAI by default; existing configs preserved | New DEFAULT_MODEL constant routes session/bootstrap/daemon/UI fallbacks through one place |
| **WIP monitor correctness** | Only `deliverable=true` SendMessage stops inline progress monitor | Interim sends no longer silence [wip] updates or tool logs |
| **Telegram rules decoupled from SMS** | TRIGGER_TELEGRAM_RULES (rich formatting, attachment-first) replaces SMS rules; voice-note transcription-first guidance | Telegram messages from Gee read as Telegram, not SMS |
| **Voice callback route preserved** | voice_agent_task propagates through delegate_async + worker_result | Active-call replies stay in-call instead of starting new outbound calls |
| **Plaid balances in dollars** | Dedicated balance formatter with per-currency rollup | Cleaner Plaid output; 75/75 gee_connect tests pass |
| **Pretext polish** | PIPs route to originating space; model selection preserved across modes; viewport scaling lock defaults off; context chips stay correct | Less PIP/space drift across Edenic/GTEK/mg |

### New Commands / Tools

| Command | What it does | When to use it |
|---|---|---|
| `gee-code setup all` | Re-run setup (needed for Cursor agent support post-upgrade) | After upgrading to v0.58 if you want Cursor agents |
| Credentials Manager (Gee/T panel) | Store API keys in scoped vault | Adding API keys for new connectors |

### ⚠️ Caution

Neil flagged: "Be careful with the connectors & credentials — had to push this version to fully test." Treat connector + credential workflows as beta this week. Farshid filed a daemon crash bug (keychain permission loop wrote a 26GB log file) — patch in flight.

### ✅ To Explore

- [ ] Run `/restart Gee-Code` and confirm daemon picks up v0.58.0 (already on it per `/version`)
- [ ] Open the Cloud file tab in Terminal — drag a small test doc (e.g., a meeting note) and confirm RAG indexing
- [ ] Test a Telegram briefing from MG and confirm rich formatting / attachment handling improved
- [ ] If using Cursor: run `gee-code setup all` and add Cursor API key via Credentials Manager

---

<a name="v0570"></a>
## 🚀 v0.57.0 + Terminal v1.29.0 — Credentials Vault, Gee-Tab Refactor, Custom Panels (Apr 28, 2026)

**Requires:** Daemon restart + new Gee/T download
**Impact level:** 🔴 High

### Summary
Major Terminal surface refactor. Eight new panels (Account, Agents, Connectors, Credentials, Endeavors, Messages, Objectives, Teams) replace the old Gee-tab layout on a shared PanelShell. Credentials Vault lands — daemon parks missing-key requests, you resolve via SMS deep link or Vault panel. Custom Panels + `/dashboard` lets Gee scaffold declarative dashboards. Pretext PIP screenshots mean Gee can finally see its own workspace. Plus DXF/CAD preview, editable Objectives panel, Google Slides fix (batchUpdate now actually works), and a working-directory fix that distinguishes daemon launch cwd from active panel cwd.

### 🎯 Most Impactful For You

1. **Credentials Vault** — When MG needs an API key it doesn't have (e.g., a new GTEK client tool), the daemon parks the request and surfaces it via SMS deep link or the Vault panel. No more silent failures on missing keys.
2. **Editable Objectives panel** — The Objectives panel is now the authoring surface, with a history audit trail. You can directly view/edit MG's tracked objectives (Gee Release Tracker, recipe manager, etc.) in the Terminal.
3. **Working-dir fix** — "This directory" finally means what you're looking at, not where the daemon launched. Saves a lot of confusion when MG operates on the wrong path.
4. **Google Slides fix** — batchUpdate now dispatches by MIME type, so MG can actually edit Google Slides decks. Useful for GTEK client deliverables.
5. **Cost controls** — Removal of compounding heartbeat-driven unbound expenses. Background MG runs are cheaper.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Credentials Vault** | Daemon parks missing-key requests; webapp resolves via SMS deep link; full Vault panel in Terminal Gee tab | No more silent failures when MG hits a missing API key |
| **Gee-tab refactor** | 8 new panels (Account, Agents, Connectors, Credentials, Endeavors, Messages, Objectives, Teams) on shared PanelShell | Cleaner Terminal Gee tab; better navigation |
| **OpenClaw runtime in Terminal** | Typed AiProviderRuntime for OpenClaw gateway (status/start/stop/health/installCli) wired into new panel suite | OpenClaw provider lifecycle now visible/managed from Terminal |
| **Custom Panels + `/dashboard`** | Declarative panels at right-sidebar/panel/pretext-pip + NL skill that scaffolds, wires, and verifies dashboards | Tell MG "build me a dashboard for X" and it scaffolds one |
| **Pretext PIP screenshots** | New `pretext_screenshot` MCP tool captures any PIP shell (browser, file, terminal, GNA, nested) | AI can finally see its workspace — useful for visual-context tasks |
| **DXF / CAD support** | Full DXF preview (INSERT/ARC/TEXT/LEADER/HATCH/ELLIPSE/SOLID/DIMENSION/MTEXT, ACI layer colors, parse-stats HUD) + zoom/pan + DxfEdit tool | Niche but landed — relevant if any Edenic deals involve CAD files |
| **Editable Objectives** | Objectives panel = authoring surface with history audit trail | View/edit MG's tracked objectives directly |
| **Google Docs/Slides fix** | batchUpdate dispatches by MIME type; writeControl plumbed through | Slides actually works now — GTEK client decks editable |
| **Working-dir fix** | Prompts distinguish daemon launch cwd from active panel cwd | "This directory" = what you're looking at |
| **Phone-call hardening** | Twilio media websocket handshake fixes + target-speaker gate for inbound voice | Voice call reliability up |
| **Performance** | Panels stay mounted across Gee tab switches; AIWorkspace pauses polling off-tab; readEvents scan ~2.5× faster | Faster Terminal, less background work |
| **comms_send wakes target daemon** | Peer messages activate autonomous modes via trigger handler | Inter-Gee comms (e.g., MG → GTEK Gee) reliably trigger autonomy |
| **Cost controls** | Removal of compounding heartbeat-driven unbound expenses | Background MG runs cost less |

### New Commands / Tools

| Command | What it does | When to use it |
|---|---|---|
| `/dashboard` | NL skill that scaffolds + wires + verifies a custom panel | "MG, build me a dashboard for cohort metrics" |
| `pretext_screenshot` (MCP) | Capture any PIP shell visually | When MG needs to "see" a PIP to debug or understand state |
| Objectives panel (Gee tab) | View/edit tracked objectives with history | Inspect what MG is tracking; edit directly |
| Credentials panel (Gee tab) | Manage scoped API keys | Add/rotate keys for connectors |

### ✅ To Explore

- [ ] Open the Terminal Gee tab — explore the 8 new panels (Account, Agents, Connectors, Credentials, Endeavors, Messages, Objectives, Teams)
- [ ] Open the Objectives panel and confirm "Gee Release Tracker" objective is visible/editable
- [ ] Try `/dashboard` and ask MG to scaffold a simple panel
- [ ] Test a Google Slides edit via MG (e.g., update a slide title in a GTEK deck) and confirm it works
- [ ] Confirm "this directory" now matches the active panel cwd, not the daemon launch dir

---

<a name="v0560"></a>
## 🚀 v0.56.0 — OpenClaw, REPL Tiers, Voice Calls (Apr 27, 2026)

**Requires:** Daemon restart + New Gee/T download
**Impact level:** 🔴 High

### Summary
The biggest release since v0.55.0. Three things matter most: (1) OpenClaw turns any Anthropic "claw" into a full Gee provider — your Gee gets context + tooling backed by Claude's raw power. (2) `/repl gpi` is now production-ready and expanded to 6 tiers — this is your go-to for any long or complex task, saving ~28% cost and ~30% response time. (3) You can now ask Gee to call you, or call Gee directly — voice is live.

### 🎯 Most Impactful For You

1. **`/repl gpi`** — Use this by default for any Edenic research, GTEK analysis, or multi-step coding work. Cheaper, faster, smarter on long tasks. Switch with `/repl gpi` at the start of any session.
2. **OpenClaw ACP** — If you have an Anthropic claw provisioned, you can now build Gee instances backed by it. Relevant when spinning up dedicated Gees for Edenic or GTEK client work.
3. **Activation matrix split** — Runtime posture and prompt preset are now independent. You can tune how much compute Gee uses (FULL/MID/LEAN) separately from how it communicates. Useful for cost management on GTEK deliverables.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **OpenClaw ACP** | New gateway provider peer to Claude/OpenAI/Gemini; `/openclaw` slash command + status-bar picker | Edenic: spin up a dedicated Gee backed by a Claw for deal research. GTEK: scoped client Gee with full tooling. mg: more model flexibility |
| **`/repl gpi` graduates** | Now production-ready; expanded to 6 tiers (gpi, spark, fast, focus, xp, ml); +6.5pp efficacy, −14% wall time, −30% TTFT, −28% cost vs spark | mg/GTEK: use `/repl gpi` as default on any long task. Reduces cost and latency materially |
| **Phone-call barge-in** | Twilio VAD with adaptive noise floor; voice routes through daemons with per-Gee voice profiles; "ask Gee to call you" works | mg: ask MG to call you for a verbal briefing. Useful when you're away from keyboard |
| **Activation matrix split** | Runtime posture (FULL/MID/LEAN) now resolves separately from prompt preset; status bar shows `AUTO · CUSTOM` when modified | GTEK: run LEAN posture on routine tasks to reduce cost. Edenic: FULL for deep research sessions |
| **Pretext polish** | Per-space accent theming, paste-region persistence, file-menu refactor, multi-worktree picker, browser PIPs auto-mute when minimized | Quality of life — spaces now color-coded (CTRL+click space to set color, CTRL+click '+' for dividers) |
| **DeepSeek V4** | Added as native provider with 1M context window | Long-document analysis: entire GTEK contracts or Edenic decks in a single context |
| **Model picker cleanup** | GPT-5.5 family, chatgpt-zero no-reasoning aliases, Gemini 3.1 Flash | More options in the model picker |
| **Credential Framework** | End-to-end autonomous operation via PIP for onboarding | Simplifies setting up new Gees for Edenic/GTEK use cases |

### New Commands

| Command | What it does | When to use it |
|---|---|---|
| `/openclaw` | Switch to OpenClaw provider or check status | When you want a Claw-backed Gee |
| `/repl gpi` | Activate GPI REPL tier (most efficient) | Start of any long/complex session |
| `/repl spark` | Spark tier | Balanced sessions |
| `/repl fast` | Fast tier | Quick lookups, short tasks |
| `/repl focus` | Focus tier | Deep single-task work |
| `/repl xp` | XP tier | Experimental |
| `/repl ml` | ML tier | ML-specific workloads |
| `/repl auto` | Let router decide tier | Default / let Gee choose |

### ✅ To Explore

- [ ] Try `/repl gpi` at the start of next Edenic or GTEK session — confirm it feels faster
- [ ] CTRL+click a space to set a color; CTRL+click '+' to add a divider
- [ ] Say or type "call me" to MG and test the voice call feature
- [ ] Check the status bar — confirm it shows `AUTO · CUSTOM` after changing runtime posture
- [ ] Open `/openclaw` in the composer and explore what providers are available

---

<a name="v0552"></a>
## 🚀 v0.55.2 + Terminal v1.27.1 — /repl gpi Beta (Apr 26, 2026)

**Requires:** Daemon restart
**Impact level:** 🟡 Medium

### Summary
This release introduced `/repl gpi` as a beta feature — the pi-inspired REPL that became production in v0.56.0. Also includes hardening fixes for tool outputs, heartbeat reliability, and Anthropic tooluse. Terminal v1.27.1 adds compact Pretext tool previews and preserves Telegram trigger settings.

### 🎯 Most Impactful For You

1. **`/repl gpi` (beta)** — Already superseded by the production version in v0.56.0, but this is where it originated. No action needed since you're on v0.56.0.
2. **Heartbeat fixes** — Activation type and lane tagging improved. MG's scheduled tasks (like the 6am release scan) are more reliable after this fix.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **`/repl gpi` beta** | Pi-style cache barrier + terminate-after-tools hint + parallel-tool coordinator | Superseded by v0.56.0 production version — use `/repl gpi` there |
| **Flash-history pointer upgrade** | More efficient context compression in long sessions | Fewer context resets mid-task on long Edenic or GTEK work sessions |
| **Heartbeat hardening** | Activation type/lane tagging + section parsing fixes | MG's heartbeat tasks (6am scans, daily standing orders) more reliable |
| **BYOP compact tool results** | Cleaner output when using your own API keys | Less noise in responses during GTEK/Edenic tasks |
| **Terminal v1.27.1** | Compact Pretext tool previews; Telegram trigger preserved on Agentics save | Quality of life — Telegram automation settings no longer reset |

### New Commands

| Command | What it does | When to use it |
|---|---|---|
| `/repl gpi` | GPI REPL tier (graduated to production in v0.56.0) | Use the v0.56.0 version — same command |

### ✅ To Explore

- [ ] Confirm Telegram trigger settings are preserved after opening/saving Agentics panel

---

<a name="v0551"></a>
## 🚀 v0.55.1 — Google Sheets/Docs/Slides Updates + Telegram Fix (Apr 25, 2026)

**Requires:** Daemon restart
**Impact level:** 🟢 Passive

### Summary
Quick patch on top of v0.55.0. Two notable additions: Google Sheets/Docs/Slides now support targeted updates (edits and cell additions/deletions) instead of full rewrites — a significant workflow improvement. Telegram regression from v0.55.0 fixed.

### 🎯 Most Impactful For You

1. **Google Sheets/Docs/Slides edits** — This is a big one for GTEK. MG can now update specific cells, add rows, edit slide text, or modify doc sections without rewriting the entire file. Your cohort model workbook and GTEK deliverables can now be updated surgically.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Google Sheets targeted updates** | Add/edit/delete specific cells and rows (not full rewrites) | GTEK: MG can update your cohort model, billing trackers, or client deliverable sheets directly. Edenic: update deal trackers cell by cell |
| **Google Docs targeted edits** | Edit specific sections of a Doc | Edenic: update meeting notes or deal memos without overwriting the whole file |
| **Google Slides targeted edits** | Edit specific slides | GTEK: update client decks without full regeneration |
| **Telegram fix** | Regression from v0.55.0 patched | Telegram notifications and multi-agent comms restored |

### New Commands

*No new slash commands — feature is accessed via MG instructions (e.g., "update row 5 of my cohort model with X")*

### ✅ To Explore

- [ ] Ask MG to update a specific cell in your cohort model workbook to test the targeted Sheets edit
- [ ] Ask MG to edit a specific section of a Google Doc (e.g., update a line in an Edenic meeting note)

---

<a name="v0550"></a>
## 🚀 v0.55.0 — Objective Escalation, Model Surface, Voice Routing (Apr 25, 2026)

**Requires:** Daemon restart + Terminal update
**Impact level:** 🔴 High

### Summary
33-commit release across nine themes. The standout: Objectives now have a full escalation ladder with blocker states — MG can flag when it's stuck and why, instead of silently failing. DeepSeek V4 and GPT-5.5 aliases expand the model surface. Voice routing goes live — tasks can route through daemons and results surface in active calls. The activation matrix gets smarter with runtime posture/prompt preset decoupled.

### 🎯 Most Impactful For You

1. **Objective escalation ladder** — MG can now formally surface blockers on tracked objectives (like the Gee Release Tracker, recipe manager, GTEK deliverables). Instead of silently stalling, MG will escalate with a structured blocker state. This closes a major loop in autonomous work.
2. **Runtime posture / prompt preset decoupled** — You can now set FULL/MID/LEAN compute separately from how Gee communicates. Run LEAN on GTEK routine tasks, FULL on Edenic research.
3. **Voice routing** — Gee can now take voice calls and route results back into active calls. The "ask Gee to call you" feature originates here.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Objective escalation ladder** | Structured blocker state; classifier dispositions; daemon/runner surfacing; heartbeat anti-spam bypass; tool-driven record/reset/archive | mg: MG will now tell you when it's blocked on an objective instead of going silent. Edenic/GTEK: project tracking becomes more reliable |
| **DeepSeek V4 provider** | Direct OpenRouter access to DeepSeek V4 | Cost-efficient alternative for large-context tasks — GTEK doc analysis, Edenic research |
| **GPT-5.5 alias family** | ox repointed at 5.5; direct OpenRouter IDs | More model options in the picker; ox alias now points to latest GPT-5.5 |
| **Voice/realtime routing** | Gateway tasks → daemons; results → active calls | Ask Gee to call you with a briefing; Gee can also receive calls |
| **Runtime posture / prompt preset decoupled** | FULL/MID/LEAN posture independent of communication style | Tune cost and verbosity independently per task |
| **gee-code synthetic mode** | Built-in mode with scoped GNA rendering | Better isolation when running gee-code as a standalone mode |
| **Telegram streaming** | Replies stream as editable blocks | Telegram messages from Gee now feel live, not batch-delivered |
| **Pretext semantic slash search** | `/` + space + query finds commands contextually | Faster command discovery — type `/ flights` and surface relevant slash commands |
| **Origin-space PIP pinning** | PIPs stay anchored to the space that spawned them | Less PIP drift when working across Edenic, GTEK, mg spaces simultaneously |
| **Plaid-status CLI** | Check Plaid connection status from CLI | Useful for diagnosing bank feed issues |
| **Google Drive hardening** | Schema hardening + 500k delegation transport fuse | More reliable GDrive reads/writes on large Edenic or GTEK files |

### New Commands

| Command | What it does | When to use it |
|---|---|---|
| `/ [space] [query]` | Semantic slash search — find relevant commands by describing what you want | Any time you can't remember the exact slash command |
| `plaid-status` | Check Plaid connection status from CLI | Diagnosing bank feed connection issues |

### ✅ To Explore

- [ ] Type `/ ` (slash + space) then describe something you want to do — confirm semantic search surfaces relevant commands
- [ ] Set runtime posture to LEAN in Agentics panel, then run a routine task — confirm status bar shows change
- [ ] Create an objective with a blocker and confirm MG surfaces it via heartbeat escalation
- [ ] Test Telegram streaming — send a message via Gee to Telegram and confirm it streams as editable blocks

---

<a name="v0542"></a>
## 🚀 v0.54.2 + Terminal v1.26.2 — GPT-5.5 Aliases + Pretext Polish (Apr 23, 2026)

**Requires:** Daemon restart
**Impact level:** 🟢 Passive

### Summary
Small patch. GPT-5.5 and Codex 5.5 aliases routed correctly; context-window lookup updated for 5.5 aliases. Pretext portal hidden until slot size settles (reduces wrong-size flashes). Media previews stay inline and centered.

### 🎯 Most Impactful For You

Minimal direct impact — this is infrastructure cleanup. GPT-5.5 aliases now route cleanly if you're using them in any GTEK or Edenic Gees.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **GPT-5.5 / Codex 5.5 aliases** | Correct routing + context-window lookup for 5.5 aliases | GTEK: if any Gee config uses GPT-5.5 alias, it now resolves correctly |
| **Flattened tool-result previews** | Cleaner output in `/pipe` and REPL markdown | Less noise in complex multi-tool sessions |
| **Pretext portal hidden** | Portal hidden until slot size settles — reduces wrong-size flashes | UI polish — fewer visual glitches |
| **Media previews inline** | Stay centered and inline | Cleaner file preview experience |

### ✅ To Explore

- [ ] No action required — passive improvements

---

<a name="v0541"></a>
## 🚀 v0.54.1 — Bug Fixes + Telegram Fix (Apr 23, 2026)

**Requires:** Daemon restart
**Impact level:** 🟢 Passive

### Summary
Quick patch: Farshid's code merged, Telegram multi-agent communication bug introduced in v0.54.0 fixed.

### 🎯 Most Impactful For You

If you were using Telegram for Gee notifications or multi-agent comms, this patch restores reliability. No new features.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Telegram multi-agent fix** | Bug from v0.54.0 fixed | Telegram notifications from MG/GTEK Gees reliable again |
| **Farshid's code merged** | Infrastructure improvements | Backend reliability |

### ✅ To Explore

- [ ] No action required — bug fix only

---

<a name="v0540"></a>
## 🚀 v0.54.0 — Delegation, Skills System, House Voice (Apr 22, 2026)

**Requires:** Daemon restart + Terminal update
**Impact level:** 🟡 Medium

### Summary
10-commit release across five themes. Skills system gets a major rewrite — Gee can now recognize repeating patterns, create skills automatically, and reuse them. Delegation gets smarter — delegated agents can now bind to existing PIPs (badge overlays) instead of spawning new terminal windows. House voice gets a four-tier system (FULL/COMPACT/MINIMAL/OFF) for consistent, model-independent communication quality.

### 🎯 Most Impactful For You

1. **Skills system rewrite** — MG can now identify patterns in your work (recurring Edenic research flows, GTEK billing queries, release scans) and package them as durable skills. This is how the 6am release scan heartbeat gets built. Over time, your most common tasks become faster and more reliable.
2. **PIP binding for delegations** — When MG delegates a sub-task (e.g., running a GDrive search while you work on something else), the worker now overlays a badge on the existing PIP instead of opening a new terminal window. Less clutter.
3. **Four-tier house voice** — FULL/COMPACT/MINIMAL/OFF controls how verbose Gee is across different contexts. Useful for tuning mg mode communication style.

### What's New

| Feature | What it does | Why it matters for your workflows |
|---|---|---|
| **Source-aware skill discovery** | ~689-line rewrite; Gee recognizes patterns and creates/reuses skills automatically | mg: MG packages recurring tasks (release scans, billing queries, Edenic research) as durable skills over time |
| **PIP binding for delegations** | Delegated agents badge-overlay existing PIPs instead of spawning new terminal windows | Less clutter when MG runs parallel tasks (GDrive search, calendar checks) while you work |
| **Human-REPL delegation** | Delegation without requiring a mode scope | More flexible sub-task routing |
| **wake_on_user_click return policy** | Delegated agents can return results when you click back into a PIP | Natural async workflow — results surface when you're ready |
| **Four-tier house voice** | FULL/COMPACT/MINIMAL/OFF wired into channel_etiquette | Control how verbose Gee is per context — useful for SMS vs. Terminal vs. long research |
| **PR lifecycle registration** | Gee-submitted PRs tracked through their lifecycle | For GTEK code work: Gee can submit, track, and respond to PR approvals |
| **App-server approval handling** | Codex elicitation gate fix | Fixes a bug that was blocking autonomous mode on some tasks |
| **Pretext: explicit presentation mode** | File opens now specify `pip` vs `preview` explicitly | Files open in the right mode (minimized PIP vs focused preview) consistently |
| **Space customization** | CTRL+click space to set color; CTRL+click '+' to add divider; move spaces with drag targets | Organize your spaces by project — color Edenic, GTEK, mg distinctly |

### New Commands

| Command | What it does | When to use it |
|---|---|---|
| `CTRL+click [space]` | Set color for a space | Organize spaces by project/context |
| `CTRL+click [+]` | Add a divider between spaces | Group related spaces visually |

### ✅ To Explore

- [ ] CTRL+click on a space to assign it a color (e.g., blue for Edenic, green for GTEK)
- [ ] CTRL+click on the '+' in the spaces bar to add a divider
- [ ] Open Agentics settings and review the House Voice tier options (FULL/COMPACT/MINIMAL/OFF)
- [ ] Ask MG to delegate a sub-task and watch for the PIP badge overlay instead of a new window

---

## Quick Reference — Commands I Actually Use

| Command | What it does | Version introduced |
|---|---|---|
| `/repl gpi` | Most efficient REPL tier — use by default for long/complex tasks | v0.55.2 (beta) → v0.56.0 (prod) |
| `/repl auto` | Let router pick the REPL tier | Always available |
| `/openclaw` | Switch to OpenClaw provider | v0.56.0 |
| `/ [space] [query]` | Semantic slash search — describe what you want | v0.55.0 |
| `/pip` | Open a nested Pretext PIP conversation | v0.54.0 area |
| `/pipe` | Pipe output between tools | Core |
| `CTRL+click [space]` | Set space color | v0.54.0 |
| `CTRL+click [+]` | Add space divider | v0.54.0 |
| `plaid-status` | Check Plaid connection from CLI | v0.55.0 |

---

## File Paths — Where Things Live

| What | Path |
|---|---|
| This tracker | `~/Documents/Gee/mg/gee-release-tracker.md` |
| MG output files | `~/Documents/Gee/mg/` |
| GTEK Gee output files | `~/Documents/Gee/gtek/` |
| Cohort model workbook | `~/Documents/Gee/mg/cohort-model-100-users-04.18.26.xlsx` |
| Daemon logs | `~/.gee-code/logs/` |
| mg mode directory | `~/.gee-code/modes/mg/` |

---

*Maintained by MG — auto-updated at 6am when a new version number is detected in Gee-Code Test iMessage thread.*
