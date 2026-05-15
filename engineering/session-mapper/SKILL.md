---
name: session-mapper
description: Map feature idea to files, edits, and implementation snippets without making code changes. Use when user asks which files to change for a feature, requests implementation guidance only, or wants a no-edit planning pass.
---

# Session Mapper

Determine which files likely need updates for feature or idea. Provide concrete suggestions and snippets. Do not edit files unless user explicitly asks.

## Rules

- Never modify code/config/docs in this mode.
- Never run write commands.
- Read-only exploration only.
- If user asks for edits later, switch behavior only after explicit request.

## Workflow

1. Clarify target outcome in one sentence.
2. Explore codebase to map entry points, data flow, UI/API touchpoints, tests.
3. Produce prioritized file list with reason for each file.
4. For each file, propose exact change shape and minimal snippet.
5. Call out risks, migrations, edge cases, and tests user should update.

## Output Format

Use this exact structure:

1) Goal
- One-line restatement.

2) Files to Change
- `path/to/file.ext` - why this file changes.

3) Suggested Updates by File
- `path/to/file.ext`
  - What to add/remove/update.
  - Snippet:

```lang
// minimal example adapted to file style
```

4) Validation Checklist
- Unit tests to add/update.
- Integration/e2e coverage impact.
- Manual checks.

5) Unknowns
- Assumptions made.
- Questions needing user decision.

## Heuristics for File Discovery

- Start from user-facing entry point (route/page/command/handler).
- Follow dependency chain: controller -> service -> repository -> schema.
- Include shared types/contracts and feature flags.
- Include tests nearest changed behavior first, then broader tests.
- Include docs/changelog only if repo convention requires.

## Guardrails for Snippets

- Keep snippets minimal and local to file.
- Match existing naming and patterns in repo.
- Prefer pseudo-diff style bullets when exact code unknown.
- Mark uncertain snippet lines with `TODO:` note.

## Refusal Condition

If asked to edit files while this skill active, respond:
"I can do edits, but you requested planning-only mode. Say 'apply changes' and I will switch to edit mode."
