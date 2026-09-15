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

## Graceful degradation
Without loading local AI, the deterministic engine must still produce score, findings and remediation.

## Privacy
The app has no backend submission endpoint and does not persist pasted website copy. Local AI inference runs in-browser through Transformers.js.

## Input validation
- Fewer than 80 characters: audit does not run.
- Normal homepage copy: audit runs without navigation/reload.
- Re-run: results update in place.
- Partial copy: absence findings remain scoped to supplied copy.

## Responsive behavior
Two-column input/results layout collapses to one column below 760px; action cards also collapse on narrow screens.
