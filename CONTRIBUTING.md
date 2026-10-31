# Contributing

Thanks for adding a prompt. Keep it simple: one prompt per PR.

## Rules

- **Runnable as-is.** The prompt must work when pasted alone into any LLM. No links to
  other files inside the prompt block. The model can't follow them.
- **Placeholders** use `{{UPPER_SNAKE_CASE}}`, e.g. `{{PASTE_COMPONENT_CODE}}`.
- **One prompt per file**, named kebab-case and starting with a verb:
  `audit-ui-with-fitts-law.md`, `generate-design-tokens.md`.
  Law/principle files are named after the law: `principles/fitts-law.md`.
- **Organised by domain**: `ui-ux/`, `frontend/`, `backend/`, `security/`, `testing/`, `debugging/`,
  `devops/`, `principles/`. Stack-specific prompts go inside a domain, e.g. `frontend/react/`.
  A new domain folder needs at least one prompt and a `README.md`.
- **Update the index**: add your prompt to the folder's `README.md`, and the root
  `README.md` if you created a new folder.

## Laws and principles

- Each law gets one file in `principles/` with: a full definition, examples, common
  violations, a single-law prompt that applies it, and a **Sources** section citing the
  original research or primary reference (author, year, title, publication, and a link
  where one exists). Follow the shape of any existing file in `principles/`.
- Prompts that combine several laws must **inline a 1–2 line definition** of each law
  they use (copied from its `principles/` file), so they still work standalone.

## Template

````markdown
# Title

**Use when:** one line describing the situation
**Inputs:** `{{PLACEHOLDER_ONE}}`, `{{PLACEHOLDER_TWO}}`
**Works with:** any LLM (note any tool-specific requirements)

## Prompt

```
The full copy-paste prompt goes here, using {{PLACEHOLDER_ONE}} where needed.
```

## Example (optional)

A short sample input/output.
````
