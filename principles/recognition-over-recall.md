# Recognition over Recall

**Summary:** show options, don't make people remember.
**Use when:** reviewing navigation, forms, search, and multi-step flows
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Recognising something you see is easier than recalling it from memory, because the interface supplies the cues. Make objects, actions and options visible so users don't have to remember them across screens.

## In practice

- Show recent items, history, and suggestions.
- Use autocomplete, visible menus, and inline hints instead of blank inputs.
- Keep key information visible when the user moves to the next step.

## Common violations

- Commands available only through memorised shortcuts or gestures.
- Placeholder text as the only label (it disappears on typing).
- Asking users to re-enter information shown on a previous screen.

## Prompt

```
You are a senior UX designer. Review the UI below using Recognition over Recall only.

Recognition over Recall: show options, don't make people remember. Use visible menus, recent items, autocomplete and inline hints.

1. List every place where users must remember something the UI could show them, most severe first.
2. Give a concrete fix for each (code changes if I shared code).
3. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Nielsen, J. (1994). 10 Usability Heuristics for User Interface Design (heuristic #6). Nielsen Norman Group. https://www.nngroup.com/articles/ten-usability-heuristics/
2. Budiu, R. (2014). Memory Recognition and Recall in User Interfaces. Nielsen Norman Group. https://www.nngroup.com/articles/recognition-and-recall/
