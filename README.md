# LeakLens

Privacy-first AI conversion auditor for service-business websites, built for the AI Builders Hackathon 2026.

## Live product
- App: https://eurekawebsites.github.io/leaklens/
- Deck: https://eurekawebsites.github.io/leaklens/deck.html
- QA: [TESTING.md](TESTING.md)
- Judging evidence: [JUDGING.md](JUDGING.md)
- Devpost copy: [SUBMISSION.md](SUBMISSION.md)

## What it does
Paste visible homepage copy and receive a conversion-health score, ranked conversion-risk map, evidence for every finding, and concrete P1/P2/P3 fixes.

LeakLens uses a hybrid architecture:
1. deterministic evidence rules for observable signals such as CTAs, booking paths, lead capture, pricing/currency, trust and differentiation;
2. optional browser-local MobileBERT MNLI zero-shot classification through Transformers.js for semantic ambiguity;
3. confidence-gated fusion so AI adds risk signals without replacing observable evidence.

No API key is required. The supplied business copy is not sent to a hosted LLM provider, and the app remains fully useful in rules-only mode.

## Verified regression behavior
The built-in sample scores **45/100 (High-friction)** with phone-only booking, potential Mexico/USD mismatch and thin trust proof. A complete-copy Eureka Tech regression recognizes CTA, lead capture, price/quote, trust proof and differentiation, preventing the original false-positive vocabulary bug from returning.

## Input guardrail
LeakLens scores **the supplied copy**, not facts it cannot observe. Absence findings are deliberately phrased as “not detected in supplied copy.”

## Tech
HTML, CSS, JavaScript, Transformers.js 4.2, MobileBERT MNLI ONNX, browser-side inference and GitHub Pages.

## Roadmap
Consent-based URL ingestion, screenshot/visual-hierarchy analysis, accessibility/mobile checks, analytics integrations, vertical-specific scoring and before/after audit history.

Built by Aster Volta / Eureka Websites Tech.
