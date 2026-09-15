# LeakLens QA & Acceptance Tests

Live app: https://eurekawebsites.github.io/leaklens/

## Core acceptance test
1. Open the live app.
2. Click **Load sample**.
3. Click **Analyze conversion leaks**.
4. Confirm a conversion-health score, ranked evidence-backed findings, and prioritized action plan appear.

### Verified sample result
- **Score:** 45/100
- **Grade:** High-friction
- **High:** Booking depends on a phone call
- **High:** Potential currency mismatch
- **Medium:** Trust proof is thin
- **P1:** Add asynchronous booking
- **P1:** Verify currency end-to-end
- **P2:** Move proof near the CTA

A live pre-submission browser acceptance run on 2026-09-15 passed this exact result and confirmed the recognized positive chips are CTA, Lead capture, Price/quote and Differentiation.

## Real-world false-positive regression
Eureka Tech exposed false positives in the first deterministic vocabulary pass. The regression case must recognize:
- CTA: “Get a quote”, “Let’s talk”, “Explore products”, “Send us a message”
- Lead capture: “Send us a message”, “Email us”, “WhatsApp”
- Differentiation: “custom”, “built around your real workflow”, “not a generic template”

Absence findings must be phrased as **not detected in supplied copy**, not as proof that the live website lacks the feature.

## Local AI acceptance
1. Refresh.
2. Click **Load local AI**.
3. Wait for **Local AI ready** / **AI loaded**.
4. Load the sample and rerun.
5. Confirm mode becomes **Local AI + rules**.
6. If a semantic risk crosses threshold, confirm local zero-shot confidence appears as evidence.
7. Confirm the summary distinguishes among: AI added semantic risks, AI evaluated but added no extra risks, and AI inference unavailable.

A focused live browser load test on 2026-09-15 reached **Local AI ready / AI loaded** successfully. A post-fix end-to-end AI acceptance run then loaded the model, analyzed the sample in **Local AI + rules** mode, returned the expected **45/100 High-friction** deterministic result, and correctly stated: **“Local AI evaluated the copy and added no extra risk signals.”**

Because first-load model delivery depends on external CDN/model hosting, the audited release also includes a 90-second UI fallback that restores rules-ready state and exposes **Retry local AI** instead of leaving the product indefinitely stuck in a loading state.

## Graceful degradation
Without loading local AI, the deterministic engine must still produce score, findings and remediation. The optional AI layer must never be required for the core audit.

## Privacy / architecture
The app has no backend submission endpoint and does not persist pasted website copy. Local AI inference runs in-browser through Transformers.js after the browser obtains the model assets. Source review found no Firebase integration, localStorage persistence, XMLHttpRequest or WebSocket application path.

## Input validation
- Fewer than 80 characters: audit does not run and a visible message explains that at least 80 characters are required.
- A rejected short input must not replace a previous valid score with a bogus result.
- Normal homepage copy: audit runs without navigation/reload.
- Re-run: results update in place.
- Partial copy: absence findings remain scoped to supplied copy.

The 2026-09-15 live pre-submission acceptance run verified the visible short-input message and preservation of the previous valid result.

## UI integrity
- The earlier **Business type** selector was removed before submission because it was inert and did not affect scoring; the product no longer presents a control that implies unsupported segmentation.
- Desktop live acceptance found no obvious overlaps, broken controls or missing sections.
- The local-AI mode label remains visible in the narrow-screen CSS; only the header download-status text is hidden below 760px.

## Responsive behavior
Two-column input/results layout collapses to one column below 760px; action cards also collapse on narrow screens. Score-ring sizing is reduced for narrow screens. Automated mobile viewport emulation was unavailable in the connected browser QA runner, so this CSS behavior is source-reviewed rather than claimed as a separate live-device acceptance test.

## Pre-submission release hardening
The audited release added:
- visible short-input validation;
- removal of the inert Business type control;
- 90-second local-AI load recovery;
- evidence-accurate AI summary wording;
- mobile visibility for the audit mode label;
- cache-busted audited JS/CSS asset references.

Rules-only live acceptance passed 4/4 checks. Optional local-AI load + inference acceptance also passed. No product/backend blocker remains for submission.
