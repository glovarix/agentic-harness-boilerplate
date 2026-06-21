# Agentic Harness

Lean agentic OS — your rules, your sources, your outputs. Agent reads `CLAUDE.md`.

---

## Your harness

*Fill this first. Agent reads every session.*

**Mission:** <!-- one sentence -->

**Inputs:** <!-- context/sources/, pasted text, commands -->

**Outputs:** <!-- what lands in outputs/ -->

**Rules:** <!-- hard constraints -->

**Non-goals:** <!-- what this never does -->

---

## Four folders

```text
context/  →  workspace/  →  outputs/
     ↑            logic.md
```

| Folder | Job |
| --- | --- |
| `context/instructions/` | Your rules |
| `context/sources/` | Read-only files (copy to workspace first) |
| `workspace/` | Drafts, handoffs |
| `outputs/` | Approved work |
| `logic.md` | Your workflow + classification (edit this) |

Behaviour → `preferences.json`. Mechanics → `CLAUDE.md`.

---

## Start

1. Fill **Your harness** above
2. Add rules in `context/instructions/`
3. Edit `logic.md` when you know your workflow
4. `/setup` then `/smoke-test`
5. `context/sources/` → `workspace/` → `outputs/`

| Command | When |
| --- | --- |
| `/orient` | Session start |
| `/ask` | Pick a flow |
| `/handoff` | Continue in fresh session |
| `/smoke-test` | Check wiring |

Fork → rename when stable (e.g. `agentic-myproject`).
