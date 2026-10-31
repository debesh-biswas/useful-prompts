# Hick's Law

**Summary:** fewer choices, faster decisions.
**Use when:** reviewing menus, settings, pricing pages, forms, or any screen with many options
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

The time it takes to make a decision increases with the number and complexity of choices. Reaction time grows roughly logarithmically with the number of equally likely options.

## In practice

- Cut or group options. Highlight one recommended choice.
- Break long or complex tasks into smaller steps.
- Hide rarely used options behind "More" or advanced settings.

## Common violations

- Navigation with 15+ top-level items.
- Pricing pages with many near-identical plans and no recommendation.
- Forms that ask everything on one screen.

## Prompt

```
You are a senior UX designer. Review the UI below using Hick's Law only.

Hick's Law: fewer choices, faster decisions. Cut options, highlight a recommended one, split long flows into steps.

1. List every place where the number or complexity of choices slows the user down, most severe first.
2. Give a concrete fix for each: what to remove, group, hide, or recommend (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Hick, W. E. (1952). On the rate of gain of information. *Quarterly Journal of Experimental Psychology*, 4(1), 11–26.
2. Hyman, R. (1953). Stimulus information as a determinant of reaction time. *Journal of Experimental Psychology*, 45(3), 188–196.
3. Yablonski, J. Hick's Law. *Laws of UX*. https://lawsofux.com/hicks-law/
