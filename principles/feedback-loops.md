# Feedback Loops

**Summary:** every action gets a visible response.
**Use when:** reviewing buttons, forms, async actions, errors, and system state
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Every user action should produce an immediate, clear response, and the system should always show its current state. Feedback closes the loop between "I did something" and "I know what happened."

## In practice

- Pressed, loading, success and error states for every interactive element.
- Errors say what went wrong and how to fix it, next to where it happened.
- Show system state: saved/unsaved, online/offline, syncing.
- Announce async changes to screen readers (e.g. role="status").

## Common violations

- Buttons with no pressed or loading state.
- Silent failures, or a generic "Something went wrong."
- No sign of whether changes were saved.

## Prompt

```
You are a senior UX designer. Review the UI below using Feedback Loops only.

Feedback Loops: every action gets a visible response. Confirm success, explain errors with a fix, always show system state.

1. List every action with missing, late, or unclear feedback, and any hidden system state, most severe first.
2. Give a concrete fix for each, including screen-reader announcements where relevant (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Norman, D. A. (2013). *The Design of Everyday Things* (Revised and expanded ed.). Basic Books. See the principle of feedback.
2. Nielsen, J. (1994). Visibility of System Status (heuristic #1). Nielsen Norman Group. https://www.nngroup.com/articles/visibility-system-status/
