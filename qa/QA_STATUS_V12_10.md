# NUMER V12.10 Mobile-First QA Status

**Release candidate:** V12.10 Mobile-First RC  
**Qualification date:** 2026-09-19  
**Artifact:** `qa/NUMER_V12_10_MOBILE_FIRST_RC.html`  
**Status:** **CONDITIONAL HOLD — REAL PHONE SIGN-OFF + LAUNCH INFRASTRUCTURE REQUIRED**

## Independent mobile QA incorporated

The V12.10 candidate incorporates the externally tested V12.9 mobile patch set and additional repairs for remaining launch-relevant findings.

### External QA evidence reported against V12.9

- 280 fast mobile flicks produced zero stray taps.
- 30 rapid section changes produced zero wrong-view activations.
- No crashes or wrong-control taps were reported.
- Chromium mobile emulation still identified pinch/pan, Name Lab validation, archive recovery, landscape navigation, archive performance, and several smaller interaction defects.

## V12.10 repairs

- Pinch/pan interaction no longer uses a vertical-only touch-action constraint.
- A new deliberate touch clears stale suppression from the previous drag.
- Landscape phones receive a persistent one-row navigation dock.
- Mobile toasts sit above the dock and stay within viewport width.
- Compare selections use stable plate IDs rather than array indexes.
- Compare defaults to the two newest plates and preserves deliberate selections.
- New inscription clears prior name and birth date fields.
- Name Lab now validates empty and unsupported-script input instead of silently falling back or producing zero calculations.
- Digits and other ASCII non-letter characters are allowed but explicitly disclosed as ignored by the A-Z calculation.
- Archive loading no longer silently rewrites malformed, over-capacity, or partially invalid stored data.
- Archive repair creates a local raw backup before any later cleaned state can replace the original.
- Archive thumbnails use lightweight SVGs instead of redrawing the full cosmograph for every plate.
- Duplicate archive actions report that one copy was kept.
- Remove is a separate 44px-class action rather than an overlay beside the plate hit target.
- Responsive/orientation rerenders preserve the current scroll position.
- The exact committed artifact passes JavaScript syntax validation and static regression assertions.

## Known open product/QA items

These are not known P0/P1 blockers from the external Chromium run, but they remain open until adjudicated or tested:

- Physical iPhone Safari touch, pinch, keyboard and validation behavior.
- Physical Android Chrome touch, pinch, keyboard and validation behavior.
- 3·4·5 figure geometry correction.
- Still-mode audit for every ambient animation.
- Keyboard accessibility for interactive cosmograph elements.
- ARIA selected/current state semantics and focus announcements.
- Browser history/back behavior.
- Final accessibility audit.
- Privacy Policy and Terms.
- Production error monitoring.
- Analytics implementation or explicit release waiver.
- PWA/installability work if NUMER is marketed as installable/offline.

## Public promotion rule

Do not replace production `index.html` until:

1. Physical iPhone Safari sign-off passes.
2. Physical Android Chrome sign-off passes.
3. No P0/P1 defects are open.
4. Legal pages are linked.
5. Production error monitoring is active.
6. Analytics has either been implemented or explicitly waived for web V1.
7. Final accessibility blockers are resolved.

At that point, promote the exact signed-off candidate and record its production commit SHA.
