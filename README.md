# Agentic Harness

A structured, artifact-only starter kit for running prompt-based work — for non-coding activities. There is no code and there are no scripts, only Markdown and CSV files that describe your inputs, prompt templates, shared reference data, and workflow.

## Quickstart

1. **Open this folder in your AI coding tool** (the one that reads `CLAUDE.md`).
2. **Fill in the slots.** Each folder has a short `README.md` saying what goes in it — start with `inputs/`, then `templates/`. Delete those notes as you replace them with real content.
3. **Run and review.** Process an input through your template; the result is written to `outputs/` (one file per run).

## What each folder is for

- `inputs/` — your run inputs (records, personas, background docs)
- `templates/` — your prompt templates and few-shot examples
- `datasets/` — shared reference data used across runs
- `logic/` — workflow and routing rules, one Markdown file each
- `outputs/` — results, one file per run (git-ignored)
- `tests/` — plain-language checks to run before a batch
- `.claude/` — reusable API payloads and command snippets

`data/` and `outputs/` are git-ignored and must never be committed.
