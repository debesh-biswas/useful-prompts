# Peak-End Rule

**Summary:** the best moment and the last moment stick.
**Use when:** reviewing user journeys, onboarding, checkout, success screens, and error states
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

People judge an experience mostly by how they felt at its most intense point (the peak, good or bad) and at its end, rather than by the average of every moment.

## In practice

- Find the emotional peak of the journey and make it great.
- Design the final screen with care: clear confirmation, what happens next, a moment of delight.
- Find the worst pain points (errors, waits) and soften them with help and good copy.

## Common violations

- A flow that ends on a blank page or generic "Success".
- Error states with no guidance.
- The best moment buried in the middle with no emphasis.

## Prompt

```
You are a senior UX designer. Review the user journey below using the Peak-End Rule only.

Peak-End Rule: the best moment and the last moment stick. Design the key moment and the final screen with care; soften the worst pain points.

1. Identify the current peak (best), the worst moment, and the end of this journey.
2. Give a concrete improvement for each of those three (code changes if I shared code).
3. In one line, note what already works well.

Journey to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Kahneman, D., Fredrickson, B. L., Schreiber, C. A., & Redelmeier, D. A. (1993). When more pain is preferred to less: Adding a better end. *Psychological Science*, 4(6), 401–405.
2. Fredrickson, B. L., & Kahneman, D. (1993). Duration neglect in retrospective evaluations of affective episodes. *Journal of Personality and Social Psychology*, 65(1), 45–55.
3. Yablonski, J. Peak-End Rule. *Laws of UX*. https://lawsofux.com/peak-end-rule/
