# Progressive Disclosure

**Summary:** show details only when needed.
**Use when:** reviewing settings, complex forms, feature-heavy screens, and onboarding
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Show only the most important options at first, and defer advanced or rarely used ones to a secondary screen or step. This makes interfaces easier to learn and less error-prone.

## In practice

- Put the core 80% of use on the first layer; move the rest behind "Advanced" or "More".
- Keep it to two levels. Deeper layers get lost.
- Make the path to the hidden layer obvious and clearly labelled.

## Common violations

- Every setting shown at once.
- Essential options hidden behind an advanced toggle.
- Three or more levels of nested disclosure.

## Prompt

```
You are a senior UX designer. Review the UI below using Progressive Disclosure only.

Progressive Disclosure: show details only when needed. Put the core options first; reveal advanced ones on demand.

1. List what should be on the first layer and what should move to a secondary layer.
2. Flag anything essential that is currently hidden, and any disclosure deeper than two levels.
3. Give a concrete fix for each (code changes if I shared code).
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Nielsen, J. (2006). Progressive Disclosure. Nielsen Norman Group. https://www.nngroup.com/articles/progressive-disclosure/
