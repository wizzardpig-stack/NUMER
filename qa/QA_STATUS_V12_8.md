# NUMER V12.8 QA Status

**Release candidate:** V12.8 Calculation Audit RC  
**Qualification date:** 2026-09-19  
**Artifact:** `qa/NUMER_V12_8_CALCULATION_AUDIT_RC.html`  
**Status:** **HOLD — EXTERNAL DEVICE + LAUNCH INFRASTRUCTURE REQUIRED**

## Gate board

| Gate | Status |
|---|---|
| Core calculation correctness | **PASS** |
| Interpretation coverage | **PASS** |
| V12.6 DOM XSS blocker | **FIXED / RETESTED** |
| Mobile touch-intent mitigation | **IMPLEMENTED / PHYSICAL TEST PENDING** |
| 44 px mobile navigation targets | **PASS** |
| Previously unlabeled controls | **PASS** |
| Physical iPhone Safari | PENDING |
| Physical Android Chrome | PENDING |
| Desktop Firefox / Safari | PENDING |
| Windows Edge | PENDING |
| Privacy Policy / Terms | PENDING |
| Production error monitoring | PENDING |
| Product analytics | PENDING |
| Final accessibility audit | PENDING |
| PWA packaging | DEFERRED — not required for ordinary web launch |

## Calculation evidence

V12.8 passes 17/17 automated calculation and interpretation gates.

Key evidence:
- 73,414 valid birth dates checked against an independent Life Path oracle.
- 20,000 deterministic name calculations checked across forced-Y modes.
- Published reference examples pass.
- Adaptive-Y published examples pass after NUMER-CALC-001 repair.
- Every reachable core number has complete interpretation content.

See `CALCULATION_INTERPRETATION_AUDIT_V12_8.md`.

## Promotion rule

Do not replace production `index.html` until:

1. iPhone Safari and Android Chrome both pass the external-device protocol.
2. Mobile gesture torture test records zero accidental activations.
3. No open P0 or P1 defects remain.
4. Privacy / Terms are linked.
5. Production error monitoring is live.
6. Required analytics events are live or deliberately waived in the release record.
7. Final accessibility gate is complete.

Only then may this exact release candidate, or a byte-identical promoted copy, become PUBLIC READY.
