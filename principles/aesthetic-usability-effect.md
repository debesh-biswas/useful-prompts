# Aesthetic-Usability Effect

**Summary:** people trust what looks good.
**Use when:** reviewing a UI's visual polish, or checking that good looks aren't hiding usability problems
**Inputs:** `{{UI_TO_REVIEW}}`
**Works with:** any LLM. Paste code, a screenshot, or a description.

## Definition

Users perceive attractive designs as easier to use, and they are more tolerant of minor problems in them. The flip side is that a beautiful UI can hide real usability issues during testing.

## In practice

- Consistent spacing, alignment, type scale and colour make a product feel trustworthy.
- Polish the screens people judge first: onboarding, pricing, checkout.
- In usability tests, watch what users *do*, not just what they say they like.

## Common violations

- Inconsistent spacing, misaligned elements, or mixed font styles that make the product feel broken.
- Decoration that hurts readability or contrast.
- Shipping a pretty design without testing whether tasks actually succeed.

## Prompt

```
You are a senior UX designer. Review the UI below using the Aesthetic-Usability Effect only.

Aesthetic-Usability Effect: people trust what looks good. Polish visuals, but never let looks hide usability problems.

1. List every place where visual quality (spacing, alignment, type, colour, consistency) undermines trust, most severe first.
2. List any place where styling hurts usability (contrast, readability, unclear affordances).
3. Give a concrete fix for each (code changes if I shared code).
4. In one line, note what already works well.

UI to review:
{{UI_TO_REVIEW}}
```

## Sources

1. Kurosu, M., & Kashimura, K. (1995). Apparent usability vs. inherent usability: experimental analysis on the determinants of the apparent usability. *CHI '95 Conference Companion*, 292–293. https://dl.acm.org/doi/10.1145/223355.223680
2. Tractinsky, N., Katz, A. S., & Ikar, D. (2000). What is beautiful is usable. *Interacting with Computers*, 13(2), 127–145.
3. Moran, K. (2017). The Aesthetic-Usability Effect. Nielsen Norman Group. https://www.nngroup.com/articles/aesthetic-usability-effect/
4. Yablonski, J. Aesthetic-Usability Effect. *Laws of UX*. https://lawsofux.com/aesthetic-usability-effect/
