# Serial Position Effect

**Summary:** first and last items are remembered best.
**Use when:** reviewing navigation order, lists, tab bars, and content sequence
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

People best remember the first items in a series (primacy effect) and the last ones (recency effect). Items in the middle are remembered least.

## In practice

- Put the most important items at the start and end of navigation and lists.
- On mobile tab bars, key destinations go first and last.
- Put lower-priority items in the middle.

## Common violations

- The most-used destination buried in the middle of the nav.
- Key information in the middle of a long list or paragraph.
- Alphabetical ordering where priority ordering would help more.

## Prompt

```
You are a senior UX designer. Review the UI below using the Serial Position Effect only.

Serial Position Effect: first and last items are remembered best. Put key items at the start and end of lists and nav.

1. List every list, menu or sequence where important items sit in the middle, most severe first.
2. Give a concrete reordering for each (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Ebbinghaus, H. (1885). *Über das Gedächtnis*. Leipzig: Duncker & Humblot.
2. Murdock, B. B. (1962). The serial position effect of free recall. *Journal of Experimental Psychology*, 64(5), 482–488.
3. Yablonski, J. Serial Position Effect. *Laws of UX*. https://lawsofux.com/serial-position-effect/
