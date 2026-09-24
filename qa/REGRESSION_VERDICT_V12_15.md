# NUMER V12.15 Final Emulator Closure

**Candidate:** `NUMER_V12_15_PHONE_GATE_RC.html`  
**SHA256:** `da58ebf5d052df68d3e3d31ffde994ef8492002c704b894d07445638945d9878`  
**Status:** **CONDITIONAL PASS — READY FOR PHYSICAL PHONE / SCREEN-READER GATE**

## Scope

V12.15 is a surgical closure pass on V12.14.

It addresses three independently reproduced issues:

1. Archive long unbroken identity names were not contained.
2. Older <=760px CSS overrode V12.14 and reduced small-landscape dock labels to 7.5px.
3. Changing the interactive cosmograph from `role="img"` to `role="group"` exposed decorative SVG text to assistive technology.

Two adjacent zero-risk presentation items were also closed:

- Deep Reading's figure-bridge button is now a 44px mobile touch target.
- the duplicate `theme-color` meta element was removed.

The calculation engine and V12.7 touch-intent guard remain source-identical to V12.14.

---

# FINAL V12.15 VERDICT

## P0

None reproduced.

## P1

None reproduced.

## Closed P2 / accessibility findings

### Archive long-token containment — FIXED

An 80-character unbroken name was archived and rendered at:

- 320×568
- 360×800
- 390×844
- 412×915
- 768×1024
- 844×390
- 932×430

Measured page overflow:

**0px at all seven sizes.**

The Archive plate and name now explicitly use zero minimum width, full available width and `overflow-wrap:anywhere`.

The 844×390 screenshot confirms the long archived identity wraps inside the manuscript rather than widening the viewport or pushing Settings off the dock.

### Small-landscape dock typography — FIXED

Measured:

| Viewport | Dock font | Dock height | Desktop chapter row |
|---|---:|---:|---|
| 667×375 | 12px | 44px | hidden |
| 736×414 | 12px | 44px | hidden |
| 740×360 | 12px | 44px | hidden |
| 568×320 | 12px | 44px | hidden |
| 844×390 | 12px | 44px | hidden |
| 932×430 | 12px | 44px | hidden |

The V12.15 landscape rule explicitly wins over the older `@media(max-width:760px)` 7.5px rule.

### Interactive cosmograph accessibility noise — FIXED structurally

Chromium accessibility snapshot for a resolved plate now exposes:

- one group: “Numerological cosmograph for Maria Elena Garcia. Explore numerical sectors and identity layers.”
- exactly 12 buttons:
  - number 1 through number 9
  - Expression
  - Personality
  - Soul

No alphabet ring, Σ, VOWELS, CONSONANTS, identity footer, date, center labels or other decorative SVG text appears in the snapshot.

The decorative descendants of each interactive button are now `aria-hidden`, while the outer button keeps its explicit accessible name and pressed state.

Regression:

- SVG role: `group`
- interactive controls: 12
- no control has an `aria-hidden` ancestor
- Soul + Enter: `aria-pressed=true`
- Number 3 + Space: `aria-pressed=true`

Physical VoiceOver/NVDA verification is still required.

---

## Additional closure

### 320px Compare layout

The V12.14 global three-column rule had overridden the older mobile stack.

V12.15 restores:

`grid-template-columns: 1fr`

at widths <=600px.

At 320px:

- page overflow: 0px
- each identity heading receives the full 292px content width
- heading scroll width equals client width
- long realistic spaced identities wrap instead of collapsing into a near-zero-width side column

### Deep Reading figure bridge

At 390px portrait:

**44px measured height.**

### Theme color metadata

Exactly one `meta[name="theme-color"]` remains.

---

# Locked systems

Source comparison against V12.14:

- calculation-engine block: **identical**
- V12.7 touch-intent guard: **identical**
- `TOUCH_SLOP = 10`: unchanged

No arithmetic or gesture-policy changes were made in V12.15.

---

# Runtime regression

Targeted Chromium rendering produced:

- no application page exceptions
- no horizontal Archive overflow in the seven-size matrix
- correct 12-control cosmograph accessibility structure
- correct keyboard activation
- correct small-landscape navigation dimensions
- corrected 320px Compare composition

---

# Evidence

Included in the package:

- `V12_15_archive_844x390.png`
- `V12_15_compare_320.png`
- `V12_15_cosmograph_390.png`
- `numer_v1215_core_regression.json`
- `numer_v1215_final_regression.json`
- `numer_v1215_secondary_regression.json` where available

---

# Physical tests still required

V12.15 should now be frozen for hardware testing.

## iPhone Safari

Test hardest:

1. Natural 11–15px finger drift on ordinary taps.
2. Number sectors 3 and 7 without pinch zoom.
3. Pinch to 150–200%, pan, then use cosmograph and dock.
4. Validation error visibility with the software keyboard open.
5. VoiceOver traversal of the cosmograph.
6. Whether the live commentary announcement is useful rather than noisy.
7. First resolve announcement behavior.
8. Rotation while VoiceOver focus is inside the plate.
9. notch / Dynamic Island safe area.
10. browser chrome expansion/collapse.

## Android Chrome

Repeat:

- tap drift
- sector target comfort
- keyboard + validation
- zoom/pan
- rotation
- long names
- archive
- TalkBack if available

## Desktop assistive technology

- NVDA + Chrome/Firefox
- verify the group + 12-button structure
- verify commentary announcement
- verify no decorative SVG noise

---

# Known watch items intentionally not patched

These require real hardware or assistive-technology evidence before changing interaction behavior:

- 11–15px Chromium touch-slop dead band
- physical comfort of thin cosmograph number-sector hit areas
- validation toast visibility behind real software keyboards
- live-region announcement timing/churn
- focus behavior after commentary cue activation

Do not modify the touch guard solely from emulator evidence.

---

# Promotion recommendation

**READY FOR PHYSICAL PHONE GATE**

If physical iPhone Safari, Android Chrome, VoiceOver and NVDA produce no reproducible P0/P1 defects, mark mobile interaction/accessibility engineering as passed and stop changing core NUMER interaction code.