# LeakLens — 3-minute hackathon demo script

Use the canonical app: https://eurekawebsites.github.io/leaklens/

Target length: 3:00–3:40. Devpost allows up to 5 minutes.

## 0:00–0:25 — Problem

**Screen:** LeakLens landing page.

**Narration:**
“Small businesses often pay for traffic before fixing the last few steps between a website visit and revenue. A site can look polished while still hiding expensive friction: weak calls to action, phone-only booking, unclear pricing, currency mismatches, or missing trust proof. LeakLens turns visible homepage copy into an explainable conversion audit.”

## 0:25–0:50 — Product and privacy

**Screen:** Point to the paste area and the chips: No API key, Runs in your browser, Explainable scoring, AI optional.

**Narration:**
“The workflow is intentionally simple. Paste the visible homepage copy and choose the business type. The deterministic audit runs entirely in the browser. There is no backend submission endpoint and no hosted LLM API. For semantic ambiguity, users can optionally load a browser-local MobileBERT zero-shot model through Transformers.js.”

## 0:50–1:35 — Live rules-only audit

**Screen:** Click **Load sample**, then **Analyze conversion leaks**.

**Narration:**
“This sample is a physical-therapy business in Mexico City. It asks visitors to call to reserve, displays a USD price in a Mexico context, and gives little concrete trust proof. LeakLens scores the supplied copy 45 out of 100, High-friction.”

**Screen:** Show the three findings.

**Narration:**
“Every finding is evidence-backed rather than a black-box diagnosis. Here it detects booking dependence on a phone call, a potential currency mismatch, and thin trust proof. Importantly, absence findings are scoped to the copy supplied. LeakLens does not claim a live website lacks something merely because the pasted extraction was incomplete.”

## 1:35–2:00 — Prioritized remediation

**Screen:** Scroll to the action plan.

**Narration:**
“The audit is designed to produce work, not just a score. Findings map directly to a prioritized remediation plan. In this example, asynchronous booking and currency verification are P1 actions, while moving proof near the call to action is P2.”

## 2:00–2:40 — Local AI layer

**Screen:** Return to the top and click **Load local AI**. Wait until the status says **Local AI ready** and mode shows **Local AI + rules**. Rerun the sample.

**Narration:**
“The optional AI layer runs locally in the browser. MobileBERT evaluates semantic risks such as booking friction, credibility, CTA strength, and differentiation. AI is additive: it only contributes a finding when confidence crosses an explicit threshold. Deterministic evidence remains responsible for facts that should not depend on a model.”

If model loading is slow during recording, record the rules-only demo first and cut to a second take after **Local AI ready** appears. Do not spend the demo waiting on a download spinner.

## 2:40–3:10 — Why it is different

**Screen:** Show the score/findings, then briefly show the deck architecture slide if useful.

**Narration:**
“LeakLens is deliberately not a prompt wrapper. Rules handle observable conversion signals, local AI handles semantic ambiguity, and the fusion layer keeps the result explainable. It also degrades gracefully: if the model cannot load, the core product still works.”

## 3:10–3:30 — Close

**Screen:** Return to the LeakLens hero.

**Narration:**
“The goal is simple: help service businesses find conversion friction before spending more money on traffic. LeakLens is live, open source, privacy-first, and usable today.”

## Recording checklist

- Record at 1080p if possible.
- Keep browser zoom at 100% unless text is hard to read.
- Close unrelated tabs and notifications.
- Do not show private accounts, email, API keys, or credentials.
- Keep the final video under 5 minutes.
- Upload to a public or unlisted video URL that Devpost judges can access without requesting permission.
- Use only the standalone LeakLens URLs in the description.

## Submission links

- Live app: https://eurekawebsites.github.io/leaklens/
- Source: https://github.com/eurekawebsites/leaklens
- Deck: https://eurekawebsites.github.io/leaklens/deck.html
- QA: https://github.com/eurekawebsites/leaklens/blob/main/TESTING.md
- Judging evidence: https://github.com/eurekawebsites/leaklens/blob/main/JUDGING.md
