# Law of Proximity

**Summary:** related things sit together.
**Use when:** reviewing spacing, forms, cards, and how content is grouped
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Objects that are near each other are perceived as a group. Spacing alone tells users what belongs together, often more strongly than colour or borders.

## In practice

- Put labels closer to their own field than to the next one.
- Use more space between groups than within them.
- Keep actions next to the thing they act on.

## Common violations

- Even spacing everywhere, so nothing reads as a group.
- Labels equidistant between two fields.
- A "Delete" button far from the item it deletes.

## Prompt

```
You are a senior UX designer. Review the UI below using the Law of Proximity only.

Law of Proximity: related things sit together. Group related items; separate unrelated ones with space.

1. List every place where spacing suggests the wrong grouping, most severe first.
2. Give a concrete fix for each, with spacing values (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Wertheimer, M. (1923). Untersuchungen zur Lehre von der Gestalt II. *Psychologische Forschung*, 4, 301–350.
2. Yablonski, J. Law of Proximity. *Laws of UX*. https://lawsofux.com/law-of-proximity/
