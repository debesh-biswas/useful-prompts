# Law of Similarity

**Summary:** things that look alike feel related.
**Use when:** reviewing component consistency, link and button styles, icons, and states
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Elements that share visual traits (colour, shape, size, style) are perceived as related and expected to behave the same way, even when they are apart.

## In practice

- Same function = same style. All links look like links; all primary buttons look the same.
- Different function = visibly different style.
- Use a design system or tokens so similarity is enforced, not remembered.

## Common violations

- Non-clickable text styled like a link.
- Several button styles for the same kind of action.
- Selected and unselected states that look too alike.

## Prompt

```
You are a senior UX designer. Review the UI below using the Law of Similarity only.

Law of Similarity: things that look alike feel related. Same function = same style; different function = different style.

1. List every place where styling is inconsistent for the same function, or misleadingly similar for different functions, most severe first.
2. Give a concrete fix for each (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Wertheimer, M. (1923). Untersuchungen zur Lehre von der Gestalt II. *Psychologische Forschung*, 4, 301–350.
2. Yablonski, J. Law of Similarity. *Laws of UX*. https://lawsofux.com/law-of-similarity/
