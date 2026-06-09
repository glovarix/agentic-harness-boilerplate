# Agent Orientation — Agentic Harness

## What this project is

This is an artifact-only prompt engineering harness. It exists to help you
generate, test, and refine prompt templates and their outputs in a structured,
repeatable way. There is no code. There are no scripts. Everything is plain
text — Markdown and CSV.

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
