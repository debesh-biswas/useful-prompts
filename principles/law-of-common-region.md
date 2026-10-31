# Law of Common Region

**Summary:** a shared box makes a group.
**Use when:** reviewing cards, panels, sections, and dense layouts
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Elements inside a clearly defined boundary are perceived as a group. A border or background can override proximity and similarity.

## In practice

- Use cards, panels or background colour to group related content.
- Give each region one clear purpose.
- Don't nest boxes inside boxes unless the hierarchy is real.

## Common violations

- Related controls split across different cards.
- Unrelated content sharing one container.
- Every element boxed, so boxes stop meaning anything.

## Prompt

```
You are a senior UX designer. Review the UI below using the Law of Common Region only.

Law of Common Region: a shared box makes a group. Use cards, panels or backgrounds to group content.

1. List every place where containers group things wrongly, are missing, or are overused, most severe first.
2. Give a concrete fix for each (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Palmer, S. E. (1992). Common region: A new principle of perceptual grouping. *Cognitive Psychology*, 24(3), 436–447. https://pubmed.ncbi.nlm.nih.gov/1516361/
2. Yablonski, J. Law of Common Region. *Laws of UX*. https://lawsofux.com/law-of-common-region/
