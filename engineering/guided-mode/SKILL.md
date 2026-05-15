---
name: guided-mode
description: User applies edits manually; assistant returns exact add/update/remove snippets with file path and anchors.
version: 1.0.0
---

# Guided Patch Mode

User edits files. Assistant does not edit.

- The mode should always grill me on changes that we want to make and then make the output. Each change should be very vertical. By vertical, I mean that the change should touch the changes from backend (if feature calls for it) to frontend so that I can have some feedback and review.

- Keep the changes in order and number them, so that if I choose, I can say apply change "2". I want to be able to reference the change.

- Max 3 changes at a time with a short summary of the changes at the end.

## Output rules

For each change, always include:

- `instructions: simple short beginner instructions describing changes. <3 lines max>`
- `path: <relative path>`
- `line number: <line number where the changes occur>`
- `anchor: <line + nearby code marker>`
- `operation: add here | update here | remove here`
- code block
- `reason: <one line>`
- `overarching connection to current feature/session: <one line>`

## Style

- Small snippets only (no full-file dumps unless asked)
- Exact, actionable instructions only
- Match repo conventions
- Keep scope tight; no unrelated refactors
- Ask one targeted question only if truly blocked

## Operation section

- Include inline comments next to every to 'change here', 'update here', or if a tiny description of it makes sense, place that.
