# Visual Hierarchy

**Summary:** the most important thing is the most visible.
**Use when:** reviewing any screen for focus, scannability, and the primary action
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Visual hierarchy is the order in which the eye takes in a design, set by size, weight, colour, contrast, position and spacing. A clear hierarchy guides users to what matters most first.

## In practice

- One clear primary action per screen; secondary actions look secondary.
- Use a type scale with distinct sizes and weights for headings, body and meta text.
- Do the squint test: blur the screen and check what still stands out.

## Common violations

- Several elements competing for attention at the same visual weight.
- Primary and secondary buttons styled the same.
- Important information in small grey text.

## Prompt

```
You are a senior UX designer. Review the UI below using Visual Hierarchy only.

Visual Hierarchy: the most important thing is the most visible. Size, weight, colour and position signal importance; one clear primary action per screen.

1. Describe the order the eye currently reads this screen in, and the order it should.
2. List every element whose visual weight doesn't match its importance, most severe first.
3. Give a concrete fix for each (code changes if I shared code).
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Nielsen Norman Group. Visual Hierarchy in UX: Definition. https://www.nngroup.com/articles/visual-hierarchy-ux-definition/
2. Nielsen Norman Group. 5 Principles of Visual Design in UX. https://www.nngroup.com/articles/principles-visual-design/
