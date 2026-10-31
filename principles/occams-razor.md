# Occam's Razor

**Summary:** the simplest design that works wins.
**Use when:** reviewing any screen or flow for unnecessary elements and steps
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Among competing solutions that work equally well, prefer the one with the fewest assumptions and elements. In design: remove anything that doesn't serve the user's goal.

## In practice

- For each element, ask: what breaks if we remove it? If nothing, remove it.
- Prefer fewer steps, fields and screens.
- Simplest *that works*. Don't remove things users need.

## Common violations

- Decorative elements, duplicate links, and redundant labels.
- Extra confirmation steps for reversible actions.
- Features added "just in case" that few use.

## Prompt

```
You are a senior UX designer. Review the UI below using Occam's Razor only.

Occam's Razor: the simplest design that works wins. Remove anything that doesn't serve the user's goal.

1. List every element, step or field that could be removed or merged without hurting the user's goal, most impactful first.
2. For each, say what to remove or merge and why it's safe (code changes if I shared code).
3. In one line, note what is already lean.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Encyclopaedia Britannica. Occam's razor. https://www.britannica.com/topic/Occams-razor
2. Yablonski, J. Occam's Razor. *Laws of UX*. https://lawsofux.com/occams-razor/
