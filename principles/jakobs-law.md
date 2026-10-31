# Jakob's Law

**Summary:** work like the sites people already know.
**Use when:** reviewing navigation, layouts, icons, or interaction patterns for convention breaks
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Users spend most of their time on other sites and apps, so they expect yours to work the same way. Familiar patterns let them transfer what they already know instead of learning something new.

## In practice

- Follow platform conventions: logo top-left links home, cart top-right, search icon is a magnifier.
- Use standard components (native controls, common gestures) before custom ones.
- When you change a familiar pattern, give users a way to keep or ease into the old one.

## Common violations

- Custom scrollbars, gestures, or controls that behave differently from native ones.
- Icons that mean something unusual (a heart that deletes).
- Redesigns that move everything at once with no transition.

## Prompt

```
You are a senior UX designer. Review the UI below using Jakob's Law only.

Jakob's Law: work like the sites people already know. Follow platform conventions; break them only with a clear reason.

1. List every place the UI breaks a common convention for its platform, most severe first.
2. For each, say whether the break is justified. If not, give the conventional fix (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Nielsen, J. (2000). End of Web Design. Nielsen Norman Group. https://www.nngroup.com/articles/end-of-web-design/
2. Yablonski, J. Jakob's Law. *Laws of UX*. https://lawsofux.com/jakobs-law/
