# Goal-Gradient Effect

**Summary:** show progress, people speed up near the end.
**Use when:** reviewing multi-step flows, onboarding, checkout, profile completion, and loyalty features
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

The tendency to approach a goal increases with proximity to it. People speed up and are more likely to finish when they can see they are close.

## In practice

- Show progress in multi-step flows: step counters, progress bars, checklists.
- Give an honest head start where it's real (e.g. step 1 already done by signing up).
- Keep the remaining steps visible and short.

## Common violations

- Long flows with no sign of how much is left.
- Progress indicators that jump backwards or are inaccurate.
- Fake progress that users later discover isn't real.

## Prompt

```
You are a senior UX designer. Review the flow below using the Goal-Gradient Effect only.

Goal-Gradient Effect: show progress, people speed up near the end. Show progress (steps, progress bars) and keep remaining steps visible and short.

1. List every place where users can't tell how far they've come or how much is left, most severe first.
2. Give a concrete fix for each, keeping progress honest (code changes if I shared code).
3. In one line, note what already works well.

Flow to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Hull, C. L. (1932). The goal-gradient hypothesis and maze learning. *Psychological Review*, 39(1), 25–43.
2. Kivetz, R., Urminsky, O., & Zheng, Y. (2006). The goal-gradient hypothesis resurrected: Purchase acceleration, illusionary goal progress, and customer retention. *Journal of Marketing Research*, 43(1), 39–58.
3. Yablonski, J. Goal-Gradient Effect. *Laws of UX*. https://lawsofux.com/goal-gradient-effect/
