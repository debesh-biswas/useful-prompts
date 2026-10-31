# Tesler's Law

**Summary:** some complexity can't be removed, so the product should carry it.
**Use when:** reviewing forms, configuration, setup flows, and anything that feels like work for the user
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Also called the Law of Conservation of Complexity: every system has a certain amount of complexity that cannot be reduced, only moved. The question is whether the system or the user carries it.

## In practice

- Move complexity into the product: smart defaults, auto-fill, detection (e.g. city from postcode).
- Infer what you can; ask only for what you can't.
- Don't oversimplify to the point that users lose control they need.

## Common violations

- Asking users for information the system already has or can infer.
- Making users format input exactly right instead of handling it.
- Hiding needed controls in the name of simplicity.

## Prompt

```
You are a senior UX designer. Review the UI below using Tesler's Law only.

Tesler's Law: some complexity can't be removed, so the product should carry it (smart defaults, auto-fill), not the user.

1. List every place where the user does work the system could do, most severe first.
2. Give a concrete fix for each: default, inference, or automation (code changes if I shared code).
3. Flag anything simplified so far that users lost needed control.
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Saffer, D. (2009). *Designing for Interaction: Creating Innovative Applications and Devices* (2nd ed.). New Riders. Includes an interview with Larry Tesler on the law.
2. Yablonski, J. Tesler's Law. *Laws of UX*. https://lawsofux.com/teslers-law/
