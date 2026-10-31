# Von Restorff Effect

**Summary:** the one thing that stands out gets remembered.
**Use when:** reviewing CTAs, pricing highlights, alerts, and emphasis
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Also called the isolation effect: when several similar items are present, the one that differs is the one most likely to be noticed and remembered.

## In practice

- Make the single most important action or item visually distinct.
- Use emphasis sparingly. If everything stands out, nothing does.
- Don't rely on colour alone. Pair it with shape, size, label or icon for accessibility.
- Keep motion-based emphasis subtle and respect reduced motion.

## Common violations

- Multiple highlighted CTAs competing on one screen.
- Badges, banners and colours on everything.
- Critical warnings styled like normal content.

## Prompt

```
You are a senior UX designer. Review the UI below using the Von Restorff Effect only.

Von Restorff Effect: the one thing that stands out gets remembered. Reserve distinct styling for the one thing that matters most.

1. Name what currently stands out most, and what should.
2. List every case of overused emphasis or under-emphasised critical items, most severe first.
3. Give a concrete fix for each, without relying on colour alone (code changes if I shared code).
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. von Restorff, H. (1933). Über die Wirkung von Bereichsbildungen im Spurenfeld. *Psychologische Forschung*, 18, 299–342.
2. Yablonski, J. Von Restorff Effect. *Laws of UX*. https://lawsofux.com/von-restorff-effect/
