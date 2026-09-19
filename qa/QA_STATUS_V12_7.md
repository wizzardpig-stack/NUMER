# NUMER V12.7 QA Status

**Release candidate:** V12.7 QA FIX RC  
**Qualification date:** 2026-09-19  
**QA artifact:** `qa/NUMER_V12_7_QA_FIX_RC.html`  
**Status:** **HOLD — EXTERNAL DEVICE SIGN-OFF REQUIRED**

## What V12.7 fixes

- Escapes the user-controlled name in the result caption, closing the V12.6 DOM XSS release blocker.
- Associates the two Name Lab inputs with labels.
- Adds accessible names to both Compare selectors.
- Raises the mobile chapter dock from 43 px to a 44 px minimum target.
- Adds mobile gesture-intent protection: a moved touch gesture is treated as scrolling/flicking and the immediately following accidental click is suppressed.
- Preserves native vertical scrolling, pinch zoom, and horizontal strip interaction.

## Verified on the exact remote QA artifact

The repository copy was re-fetched after commit and passed source assertions for:

- V12.7 version marker present.
- Escaped result-caption name present.
- Raw vulnerable result-caption interpolation absent.
- Touch-intent guard present.
- 44 px mobile navigation target present.
- All four previously unlabeled controls repaired.

GitHub Pages deployment for commit `1ef28700a30945ce8c8710b5cb53bf0f659e8494` completed successfully.

## Still required before PUBLIC READY

1. Physical iPhone Safari test.
2. Physical Android Chrome test.
3. Desktop test in at least one non-Chromium browser, preferably Firefox or Safari.
4. Edge test on Windows if Windows is a launch target.
5. Archive persistence after hard reload on the deployed HTTPS origin.
6. Mobile gesture torture test from `EXTERNAL_DEVICE_TEST.md`.
7. No open P0 or P1 defects after those runs.

## Mobile release gate

For each physical touch device:

- 20 rapid vertical flicks that start or end over buttons/navigation: **0 accidental activations**.
- 20 deliberate taps immediately after normal scrolling has stopped: **20/20 register**.
- Horizontal figure/number strips remain scrollable without accidental selection.
- No horizontal page overflow.
- Keyboard opening, closing, and form scrolling do not trap the page.
- Orientation change does not strand content or hide navigation.

## Packaging note

Manifest/service-worker work remains a separate PWA packaging milestone. It is not required for an ordinary web launch, but NUMER should not be described as installable/offline-ready until that work is completed.

## Promotion rule

Do **not** replace the live `index.html` with V12.7 until the external-device matrix is signed off. After sign-off, promote this exact artifact or an identical byte-for-byte build and record the production commit SHA.
