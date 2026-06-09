# Agentic Harness Generation Prompt
*Production-ready — v3.0 — 2026-06-09*

You are an agent running inside an IDE with file-write access. Your sole task is to scaffold an artifact-only project harness by creating the exact folders and files listed below. No code. No evals. No scripts.

## How to execute

Create every folder and file below at the exact path given. Create parent folders before the files inside them. Work in a single pass — do not pause, summarise, or ask for confirmation.

## Target structure

```
.claude/README.md
inputs/README.md
templates/README.md
datasets/README.md
logic/README.md
tests/README.md
outputs/README.md
data/.gitkeep                         (empty file)
README.md
CLAUDE.md
changelog.md
preferences.json
.gitignore
```

## Rules

- Every working folder gets a one-paragraph `README.md` saying what goes in it. These signposts keep the folder alive in git and tell the user what to put there. They are meant to be deleted once the folder has real content.
- `data/` gets a single empty `.gitkeep`; it is local-only working space and is git-ignored.
- `outputs/` holds results, one file per run, and is git-ignored except for its `README.md`.
- Do **not** git-ignore `.claude/`. Do **not** add `.gitkeep` to `.gitignore`.
- Do **not** generate any eval folder, eval template, scoring rubric, grading logic, or evaluation-related file — even if inferred from context.
- Write the files below with the exact text given.

## File contents

### `CLAUDE.md` — write exactly:

````
# Agent Orientation — Agentic Harness

## What this project is

This is an artifact-only prompt engineering harness. It exists to help you
generate, test, and refine prompt templates and their outputs in a structured,
repeatable way. There is no code. There are no scripts. Everything is plain
text — Markdown and CSV.

## Preferences

At the start of every session, read `preferences.json` from the project root and
apply these settings. If the file is missing, use the defaults shown. Never
modify `preferences.json` unless the user explicitly asks.

| Key | Default | Behaviour |
| --- | --- | --- |
| `confirmBeforeGenerate` | `true` | Announce what you are about to produce and confirm before generating. |
| `confirmBeforeSave` | `true` | Ask before writing any file. |
| `confirmBeforeCommit` | `true` | Ask before any git commit. |
| `pushAfterCommit` | `false` | `true` — push to remote after each commit. `false` — commit locally only. |
| `language` | `"en-GB"` | Writing language (`"en-GB"` or `"en-US"`). |

## What to read first

Each folder has a `README.md` explaining what goes in it. Read these before
doing anything else, in this order:

1. `inputs/README.md` — understand the input structure
2. `templates/README.md` — understand the prompt shape
3. `logic/README.md` — understand how a run flows end to end
4. `outputs/README.md` — understand where and how results are written
5. `datasets/README.md` — understand what shared reference data is available

## How inputs flow to outputs

1. A run begins with an input record from `inputs/inputs_examples.csv`
2. The input references a persona (`inputs/personas.csv`) and a context
   (`inputs/long_contexts/`)
3. Check `datasets/` for any reference data relevant to the input
4. Check `logic/` for any workflow, rule, or routing logic that applies
5. Assemble the prompt using `templates/base_prompt.tpl.md`, substituting
   the four placeholders: {{system}}, {{context}}, {{examples}}, {{user_input}}
6. Few-shot examples come from `templates/few_shot_examples.csv`
7. Write the result to `outputs/`, following the naming convention in
   `outputs/README.md`
8. Log any template or persona change in `changelog.md`

## Rules

- Never modify files in `templates/` without incrementing the version in
  `changelog.md`
- Never generate eval logic, scoring rubrics, or grading of any kind
- If an input field is missing or ambiguous, check `inputs/inputs_schema.md`
  before inferring
- New workflows, rules, and logic belong in `logic/` — drop a new Markdown
  file in; no other files need to change
- New shared reference data belongs in `datasets/` — drop a new CSV
  or Markdown file in; no other files need to change
- Commands and API payloads → `.claude/`
````

### `README.md` — write exactly:

````
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
- `preferences.json` — behaviour toggles (confirm before save/commit, language)

`data/` and `outputs/` are git-ignored and must never be committed.
````

### `inputs/README.md` — write exactly:

````
# inputs/

Put your run inputs here. Suggested files:

- `inputs_schema.md` — the fields every input record must have
- `inputs_examples.csv` — one row per run
- `personas.csv` — the roles/voices a run can use
- `long_contexts/` — background documents a run can reference

Start by copying the structure described in `CLAUDE.md`. Delete this note once the folder has real content.
````

### `templates/README.md` — write exactly:

````
# templates/

Put your prompt templates here. Suggested files:

- `base_prompt.tpl.md` — the prompt shape, with the placeholders `{{system}}`, `{{context}}`, `{{examples}}`, `{{user_input}}`
- `few_shot_examples.csv` — worked input/output examples the prompt can draw on

Delete this note once the folder has real content.
````

### `datasets/README.md` — write exactly:

````
# datasets/

Put shared, stable reference data here — lookup tables, taxonomies, code lists, controlled vocabularies, reference CSVs — anything that many runs draw on. This is different from `inputs/` (one record per run) and `outputs/` (results).

To add reference data, just drop a new CSV or Markdown file into this folder. Nothing else needs to change.
````

### `logic/README.md` — write exactly:

````
# logic/

Put your workflow and routing rules here as standalone Markdown files (for example `workflow.md`). The agent reads every file in this folder, so you can add new rules by dropping in a new file — nothing else needs to change.

Delete this note once the folder has real content.
````

### `tests/README.md` — write exactly:

````
# tests/

Put plain-language smoke tests here (for example `smoke_tests.md`) — short checks you run before a batch to confirm the harness is wired correctly. Each test says what to send, what to check, and what counts as a pass. No code.

Delete this note once the folder has real content.
````

### `.claude/README.md` — write exactly:

````
# .claude/

Put canonical API payloads and command snippets here (for example `claude_commands.md`) — the reusable request shapes this harness uses. This folder is committed; do not git-ignore it.

Delete this note once the folder has real content.
````

### `outputs/README.md` — write exactly:

````
# outputs/

Results land here — one file per run, named so a human can find it. This folder is git-ignored, so nothing in it is committed.

**File name:** `{YYYY-MM-DD}-{slug}.md` — today's date plus a short kebab-case description (for example `2026-06-09-welcome-email.md`).

**Each file holds:**

- the result itself
- a short note at the top saying which input it came from and anything worth flagging
````

### `changelog.md` — write exactly:

````
# Changelog

All notable changes to this harness are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2026-06-09

### Added
- Initial harness scaffold.
````

### `preferences.json` — write exactly:

````
{
  "confirmBeforeGenerate": true,
  "confirmBeforeSave": true,
  "confirmBeforeCommit": true,
  "pushAfterCommit": false,
  "language": "en-GB"
}
````

### `.gitignore` — write exactly:

````
data/
outputs/*
!outputs/README.md
.DS_Store
.env
*.log
````

## Global constraints

| Constraint | Rule |
|------------|------|
| Artifact-only | No code, scripts, or evaluation-related files of any kind |
| Complete | Every folder and file above must be created — no omissions |
| Single pass | Create everything in one continuous operation — no pausing |
| Signposts | Every working folder gets a one-paragraph `README.md` describing what goes in it |
| Tone | Neutral and professional — no marketing language, no product or tool names in file contents |
| `CLAUDE.md` | Write the literal content above — do not paraphrase |
