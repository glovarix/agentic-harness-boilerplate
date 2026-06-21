# Agentic Harness — Agent OS

Read every session. Framework only — domain lives in `README.md`, `context/`, `logic.md`.

## Preferences

Read `preferences.json`. Never modify unless asked.

| Key | Default | Behaviour |
| --- | --- | --- |
| `confirmBeforeGenerate` | `true` | Confirm before generating |
| `confirmBeforeSave` | `true` | Ask before writing files |
| `confirmBeforeCommit` | `true` | Ask before git commit |
| `confirmBeforeElevate` | `true` | Ask before workspace → outputs |
| `pushAfterCommit` | `false` | Local commits only |
| `commitOutputs` | `false` | Allow committing outputs/ |
| `commitWorkspace` | `false` | Allow committing workspace/ |
| `commitContext` | `false` | Allow committing context/instructions/ |
| `runEvidenceCheck` | `true` | Inspect local files first |
| `includeSanityCheck` | `true` | Post-job report |
| `organizeByJob` | `true` | outputs/{job}/{date}/{slug}.* |
| `language` | `"en-GB"` | en-GB or en-US |

## Non-negotiables

- Read config + instructions before acting
- Never invent — mark `[UNVERIFIED]`, gaps `—`, missing `[NEEDS SOURCE]`
- Never silently overwrite or drop — discard artifact + new path/suffix
- One clarifying question when blocked
- Deliverable files over chat walls
- Domain never in this file — use `context/`
- No "Let me…" — act, report
- Scripts for repetition; agent for judgment
- Memory in-repo only

## Orient (every session)

1. `preferences.json`
2. `README.md` → **Your harness**
3. `context/instructions/`, `logic.md`
4. `context/sources/` if job needs files

## Flow

```text
context/sources/  →  workspace/working/  →  outputs/
         ↑ context/instructions/ + logic.md
```

Copy sources before editing. Elevate only when `confirmBeforeElevate` allows.

## Rule 0 — "What can you do?"

From `README.md`, `logic.md`. No files. Suggest `/ask`.

## Rule 1 — Classify (first match, then `logic.md`)

| # | Signal | Action |
| --- | --- | --- |
| 1 | setup / configure | `/setup` |
| 2 | smoke test / wiring | `/smoke-test` |
| 3 | handoff | write `workspace/handoffs/{date}-{slug}.md` |
| 4 | domain / rules / terms | edit `context/` |
| 5 | workflow / logic | edit `logic.md` |
| 6 | deliverable | Rules 3–6 |
| 9 | unclear | Rule 2 |

## Rule 2 — One question

> "Deliverable, config change, or wiring check?"

## Rule 3 — Evidence

Read `context/sources/`, `context/instructions/`, `logic.md`, `workspace/`, prior `outputs/`. Missing = say so.

## Rule 4 — Job loop

Orient → classify → plan path → evidence → draft `workspace/working/` → confirm → publish `outputs/` → sanity `.report.md` → report next step.

Small increments. No logic edits mid-batch.

## Rule 5 — Outputs

- Workspace: `{slug}.draft.*`, copies in `workspace/sources/`
- Outputs: `{job}/{date}/{slug}.deliverable.*` + `{slug}.report.md` + `{slug}.discarded.csv` if anything dropped
- Same-day rerun: `_{HHMMSS}` suffix
- Optional: `outputs/job-log.csv`

## Rule 6 — Git

`context/sources/` always ignored. Flip `commit*` → sync `.gitignore`.

## Rule 7 — Handoff

Session full or ending mid-job → `workspace/handoffs/{date}-{slug}.md` with goal, done, decisions, open questions, next step, key paths. Fresh session reads file — not chat history.

## Rule 8 — Smoke test

Entry files exist. Four paths exist. No domain in this file. Commands: setup, orient, ask, smoke-test, handoff.

## Separation

| Generic | Yours |
| --- | --- |
| CLAUDE.md | README.md |
| preferences.json | context/, logic.md |

Add `scripts/` when ops go mechanical. Document in `logic.md`.
