# Postel's Law

**Summary:** accept messy input, give clean output.
**Use when:** reviewing forms, inputs, validation, search, and imports
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Also called the robustness principle: "be conservative in what you do, be liberal in what you accept from others." Originally written for network protocols, it applies directly to how interfaces handle user input.

## In practice

- Accept varied formats: dates, phone numbers with spaces or dashes, trailing whitespace, any letter case in emails.
- Normalise input on the system side instead of rejecting it.
- Output consistent, predictable formats.
- Stay strict where it matters for security and data integrity.

## Common violations

- Rejecting a phone number because it has spaces.
- Validation errors that say "invalid format" without showing the expected one.
- Search that fails on typos or different word order.

## Prompt

```
You are a senior UX designer. Review the UI below using Postel's Law only.

Postel's Law: accept messy input, give clean output. Accept varied input formats; return clear, consistent results.

1. List every input that rejects reasonable variations, or validation that is stricter than it needs to be, most severe first.
2. Give a concrete fix for each: what to accept and how to normalise it (code changes if I shared code).
3. Keep validation strict where security or data integrity require it.
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Postel, J. (1980). RFC 761: DoD Standard Transmission Control Protocol, section 2.10 (Robustness Principle). https://www.rfc-editor.org/rfc/rfc761
2. Yablonski, J. Postel's Law. *Laws of UX*. https://lawsofux.com/postels-law/
