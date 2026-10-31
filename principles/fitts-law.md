# Fitts's Law

**Summary:** big, close buttons are easier to hit.
**Use when:** reviewing buttons, tap targets, toolbars, or layout of primary actions
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

The time to reach a target depends on the distance to it and its size. Smaller and farther targets take longer to hit and cause more errors.

## In practice

- Make primary actions large and place them near where the user's attention or thumb already is.
- Touch targets at least 44×44pt (iOS) / 48×48dp (Android), even when the visible icon is smaller.
- Leave space between adjacent targets so users don't hit the wrong one.
- Screen edges and corners are effectively infinite targets on desktop.

## Common violations

- Tiny icon buttons and text links as the only way to do a key action.
- Destructive and primary actions placed right next to each other.
- Primary mobile actions at the top of the screen, out of thumb reach.

## Prompt

```
You are a senior UX designer. Review the UI below using Fitts's Law only.

Fitts's Law: big, close buttons are easier to hit. Make primary actions large and near the user's focus; touch targets at least 44×44pt (iOS) / 48×48dp (Android).

1. List every target that is too small, too far, or too close to a neighbour, most severe first.
2. Give a concrete fix for each: size, position, spacing or hit area (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Fitts, P. M. (1954). The information capacity of the human motor system in controlling the amplitude of movement. *Journal of Experimental Psychology*, 47(6), 381–391.
2. MacKenzie, I. S. (1992). Fitts' law as a research and design tool in human-computer interaction. *Human-Computer Interaction*, 7(1), 91–139.
3. Apple. Accessibility. *Human Interface Guidelines*. https://developer.apple.com/design/human-interface-guidelines/accessibility
4. Android Developers. Make apps more accessible. https://developer.android.com/guide/topics/ui/accessibility/apps
5. Yablonski, J. Fitts's Law. *Laws of UX*. https://lawsofux.com/fittss-law/
