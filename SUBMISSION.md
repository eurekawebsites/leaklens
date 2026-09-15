# LeakLens — Devpost Submission Copy

## Tagline
Private, explainable local AI that finds the leaks between website traffic and revenue.

## Inspiration
Small businesses often spend money on traffic before fixing the last part of the funnel. We kept seeing technically small but commercially expensive problems: phone-only booking, unclear next steps, mismatched currency labels, weak trust proof and generic positioning.

## What it does
Users paste visible homepage copy. LeakLens returns a 0–100 conversion-health score, ranked findings with severity and evidence, and a P1/P2/P3 action plan. An optional browser-side zero-shot model detects semantic risks that keyword rules can miss.

## How we built it
1. Deterministic evidence engine for observable conversion signals.
2. MobileBERT MNLI running locally through Transformers.js.
3. Fusion layer that adds semantic findings only above confidence thresholds.
4. Remediation layer mapping findings to prioritized fixes.

This is intentionally not a prompt wrapper. Rules handle facts that should be deterministic; AI handles semantic ambiguity.

## Responsible AI and privacy
Business copy is not sent to an LLM provider. No API key is required. AI confidence is presented as a risk signal rather than factual diagnosis. The product remains useful in rules-only mode if the browser model cannot load.

## Verified behavior
The sample scores **45/100 (High-friction)** and surfaces phone-only booking, a potential Mexico/USD currency mismatch and thin trust proof, then maps them to two P1 fixes and one P2 fix. A complete-copy Eureka Tech regression recognizes CTA, lead capture, price/quote, trust proof and differentiation, preventing the original false-positive vocabulary bug from returning.

## Built with
JavaScript, HTML, CSS, Transformers.js, MobileBERT, ONNX, Hugging Face, GitHub Pages.

## Development assistance disclosure
ChatGPT was used during the hackathon for ideation, implementation support, QA planning, copy editing and submission preparation. LeakLens does not depend on ChatGPT or a hosted LLM API at runtime.

## Links
Live demo: https://eurekawebsites.github.io/leaklens/

Public source: https://github.com/eurekawebsites/leaklens

Presentation deck: https://eurekawebsites.github.io/leaklens/deck.html

QA: https://github.com/eurekawebsites/leaklens/blob/main/TESTING.md

Judging evidence: https://github.com/eurekawebsites/leaklens/blob/main/JUDGING.md

## Suggested prize/category
Best SaaS Product
