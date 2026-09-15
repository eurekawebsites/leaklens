# LeakLens — Judging Evidence Map

The AI Builders Hackathon evaluates projects on Innovation & Creativity (20%), Technical Implementation (25%), Problem Solving & Impact (25%), User Experience & Design (15%), and Presentation & Demo (15%).

## Innovation & Creativity — 20%
LeakLens is not an LLM prompt wrapper. Observable facts are handled by deterministic evidence rules; ambiguous language is handled by a browser-local zero-shot classifier; semantic findings affect the audit only above explicit confidence thresholds.

## Technical Implementation — 25%
- Static browser application with no required backend.
- MobileBERT MNLI inference locally through Transformers.js.
- Rules engine for CTA, booking, lead capture, pricing, currency, trust and differentiation.
- Fusion layer keeps deterministic evidence inspectable.
- Graceful rules-only fallback.
- Reproducible acceptance tests in `TESTING.md`.

## Problem Solving & Impact — 25%
LeakLens targets companies buying traffic before fixing conversion friction. Every finding includes severity, evidence, commercial risk and P1/P2/P3 remediation. The sample demonstrates phone-only booking, local-market currency mismatch and weak trust proof.

## User Experience & Design — 15%
- One-screen workflow: paste → audit → ranked leak map → action plan.
- Built-in sample for immediate judging.
- Responsive desktop/mobile layouts.
- Evidence-backed findings rather than black-box scoring.
- Local AI optional and clearly labeled.
- No account or API key required.

## Presentation & Demo — 15%
- Working public product: https://eurekawebsites.github.io/leaklens/
- Public source: https://github.com/eurekawebsites/leaklens
- Deck: https://eurekawebsites.github.io/leaklens/deck.html
- Reproducible judge path and responsible-AI disclosure.

## Fastest evaluation path
Open the live app, click **Load sample**, then **Analyze conversion leaks**. Local AI can then be loaded separately to verify browser-side semantic inference.
