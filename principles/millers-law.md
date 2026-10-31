# Miller's Law

**Summary:** chunk information into small groups.
**Use when:** reviewing dense screens, long lists, forms, navigation, or data displays
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Working memory can hold only a few items at once, about 7±2 in Miller's original paper and closer to 4 chunks in later research. Grouping information into meaningful chunks makes it easier to process and remember.

## In practice

- Format long strings in chunks: phone numbers, card numbers, codes.
- Group form fields and nav items into labelled sections.
- Don't use "7" as a hard limit on menu items. The point is to chunk, not to count.

## Common violations

- Walls of text or long unbroken lists.
- Forms with 20 fields and no sections.
- Codes or numbers shown as one long string.

## Prompt

```
You are a senior UX designer. Review the UI below using Miller's Law only.

Miller's Law: working memory holds only a few items at once. Chunk information into small, meaningful groups.

1. List every place where users must hold or scan too much at once, most severe first.
2. Give a concrete fix for each: how to chunk, group, or label it (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Miller, G. A. (1956). The magical number seven, plus or minus two: Some limits on our capacity for processing information. *Psychological Review*, 63(2), 81–97.
2. Cowan, N. (2001). The magical number 4 in short-term memory: A reconsideration of mental storage capacity. *Behavioral and Brain Sciences*, 24(1), 87–114.
3. Yablonski, J. Miller's Law. *Laws of UX*. https://lawsofux.com/millers-law/
