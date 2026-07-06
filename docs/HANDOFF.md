# HANDOFF — Gee Release Tracker

**Last updated:** 2026-07-05
**Current status:** Release Tracker is current through Neil’s Gee Test/Core iMessage release note sent **2026-07-05 14:32–14:58 PT** for Gee-Code `0.72.3`, Gee/T `1.43.7` Mac / `1.43.8` Windows, GeeHQ `0.7.1`, and experimental GeeHQ `0.8.1` Mac-only build link. Neil called this a “monster update.” Event Rule work remains intentionally parked.

## Current handoff

Start with `README.md` for the release log and `docs/PROJECT_STATE.md` for the current v0.72.3 test queue.

Current open items:

- Confirm local Gee-Code `0.72.3`, Gee/T `1.43.7` Mac, and GeeHQ `0.7.1` after daemon/Gee-T/HQ restart.
- Work from `docs/PROJECT_STATE.md` Current Test Queue for the supervised testing pass.
- Prioritize tests that map to Mariciel’s real workflows: NLYM Treasurer docs and budget-upload readiness, Edenic release/partner notes, GTek/Garay Games MS365 scan, finance/tax planning guardrails, and release-tracker maintenance.
- Treat the new Geenius provider system as the main thing to understand: routing by intent, entitlement, cost, and feedback is useful, but needs sandbox checks before sensitive work.
- Keep all outbound routing tests draft-only unless Mariciel explicitly approves sending.
- Keep Outcome Loops, Event Rules, OpenClaw/Gee-Claw, task-worker delegation, Computer Use, Remote Spaces, Hermes, and model-provider tests sandboxed until behavior is predictable.
- Use `GetCapabilities(query="...")` for capability-graph testing before claiming a task cannot be done.
- Continue using the pinned Gee Test/Core iMessage chat as the release-intake source.
- Do not commit, push, publish, message Neil, or start live release testing without Mariciel approval.

## v0.72.3 practical focus for MG

Plain English: Gee is getting better at choosing the right model/tool path, keeping long sessions cheaper, finding the right capability, navigating repos, and turning work into gated tasks. That matters because Mariciel’s work crosses sensitive finance, NLYM operations, Gmail/Drive/Calendar/MS365, and code/document updates. The new power is useful only if routing, identity, approvals, and outbound boundaries behave correctly.

Highest-value next tests:

1. Version/restart check.
2. Geenius provider routing on non-sensitive prompts.
3. Capability graph query on common MG tasks.
4. Result-governor retrieval after compacted tool output.
5. Repo index / symbol edit on non-sensitive code.
6. NLYM command center read-only visual check.
7. Draft-only Outcome Loop approval/lease test.
8. Gmail/Drive/Calendar/MS365 connector smoke test.

## Resume trigger

When Mariciel says:

> Let’s create an event rule

resume the Release Tracker Event Rule plan below.

## Parked plan: Release Tracker Event Rule

Start with a safe intake rule, not a fully autonomous updater.

### Recommended Version 1

Use the installed `local_jsonl` watcher to watch a local release-intake JSONL file.

Suggested intake file:

```text
~/.gee-code/custom/release-tracker-inbox.jsonl
```

Suggested row shape:

```json
{"id":"gee-0.72.x-geet-1.43.x-2026-mm-dd","title":"Gee-Code 0.72.x + Gee/T 1.43.x Beta","source":"Neil / Gee Test-Core iMessage","received_at":"2026-mm-ddThh:mm:ss-07:00","body":"...release note text..."}
```

### Intended workflow

1. New release note is added to the intake file.
2. Event driver detects one unseen JSONL row.
3. Gee drafts:
   - Release Tracker update
   - Plain-English summary
   - What matters for MG / Edenic / GTEK / NLYM
   - Test punch list
   - Risks and follow-ups
4. Mariciel reviews before anything is applied.

### Approval boundary

Do **not** automatically:

- edit `README.md`
- edit `docs/PROJECT_STATE.md`
- send Neil anything
- file Reports/bugs
- start release testing

Ask Mariciel first.

## Event watcher facts checked 2026-06-25

Available watcher kinds:

- `activity_review`
- `activity_wake`
- `flight_eta`
- `github_repo`
- `local_jsonl`
- `reddit_subreddit`

Best first watcher: `local_jsonl`.

Possible later watcher: `github_repo`, but only if Gee release notes become available through a repo/issues/PR source.

No confirmed built-in watcher for iMessage, Slack, Gee Test/Core chat, or Neil’s release-note channel.

## Next action when resumed

Use the `create-event-driver` skill. Then inspect `Events(action="list_kinds")`, configure a stopped `local_jsonl` driver first, and preview/list before starting anything live.
