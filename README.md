# Gee Release Tracker — MG Learning Log

**Purpose:** Running summary of Gee-Code + The Terminal releases, with workflow-specific guidance on what matters most for Edenic, GTEK, and mg mode.
**Source:** Gee-Code Test iMessage chat (Neil)
**Updated:** 2026-05-17

---

## Release Index

| Version | Date | Impact | Theme |
|---|---|---|---|
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
