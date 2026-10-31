# Doherty Threshold

**Summary:** respond in under 0.4s.
**Use when:** reviewing loading states, interactions, and perceived performance
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Productivity soars when a computer and its users interact at a pace (under about 400ms) where neither has to wait on the other. Nielsen's related limits: 0.1s feels instant, 1s keeps flow, 10s loses attention.

## In practice

- Give visible feedback on every action within 0.1s, even if the work takes longer.
- When work takes longer than ~400ms, show progress: skeletons, optimistic UI, progress bars.
- Over ~10s, show percentage or time remaining and let users do something else.

## Common violations

- Buttons that do nothing visible until the server replies.
- Blank screens or a lone spinner during loads.
- Spinners that flash for loads under ~300ms.

## Prompt

```
You are a senior UX designer and performance engineer. Review the UI below using the Doherty Threshold only.

Doherty Threshold: respond in under 0.4s. When that's impossible, give instant feedback (optimistic UI, skeletons, progress).

1. List every interaction or load where the user waits without feedback, or waits longer than needed, most severe first.
2. Give a concrete fix for each: make it faster, or make the wait feel shorter (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Doherty, W. J., & Thadani, A. J. (1982). *The Economic Value of Rapid Response Time*. IBM report GE20-0752-0.
2. Nielsen, J. (1993). Response Times: The 3 Important Limits. Nielsen Norman Group. https://www.nngroup.com/articles/response-times-3-important-limits/
3. Yablonski, J. Doherty Threshold. *Laws of UX*. https://lawsofux.com/doherty-threshold/
