# NUMER External Device Break Test

Test the public V12.7 QA page as if you are trying to make it fail. Do not coach the interface. Use it quickly and naturally.

## Tester record

| Field | Value |
|---|---|
| Tester | |
| Device | |
| OS + version | |
| Browser + version | |
| Screen/orientation | |
| Date | |
| Result | PASS / FAIL |

## 1. Cold-start journey

1. Open the QA page in a fresh tab.
2. Scroll from the top to the bottom before entering anything.
3. Enter a normal name and Resolve.
4. Tap rings/markers in the cosmograph.
5. Open Deep Reading.
6. Visit Figures.
7. Archive the plate.
8. Open Archive and return to the plate.
9. Open Name Lab and change both names.
10. Open Compare after at least two plates exist.
11. Change light/dark mode and return to Resolve.

**Fail if:** anything freezes, disappears, overlays incorrectly, becomes impossible to reach, or requires a refresh.

## 2. Scroll + touch torture test

This is the highest-priority mobile test.

Repeat **20 times**:

1. Flick vertically at normal fast-thumb speed.
2. Let the finger start or finish directly over an action button, chapter button, figure selector, or number selector.
3. Do not intentionally tap the control.

Expected: **0 accidental activations out of 20**.

Then repeat **20 deliberate taps** after scrolling has stopped.

Expected: **20/20 deliberate taps register**.

Also drag the horizontal number strip and Figures selector left/right while occasionally drifting diagonally.

Expected: the strip scrolls naturally and does not randomly select items.

## 3. Keyboard and form abuse

- Focus Name, scroll while the keyboard is open, then dismiss it.
- Enter a 1-character name.
- Enter an 80-character name.
- Try spaces, hyphens, apostrophes, accented characters, emoji, and pasted text.
- Open and close the date picker repeatedly.
- Tap Resolve quickly twice.
- Rotate the phone while a field is focused.

Expected: no zoom jump, trapped scroll, clipped submit control, duplicate state, or broken layout.

## 4. Persistence

1. Archive two plates.
2. Change appearance and Y-rule settings.
3. Hard reload the page.
4. Close the browser tab completely, reopen the QA URL, and inspect Archive/Settings.

Expected: saved local state returns on the same browser profile and no data from another browser/device appears.

## 5. Resize/orientation

Test portrait and landscape on phones. On desktop, resize from narrow phone-like width to full screen.

Expected:

- No horizontal page overflow.
- Bottom navigation remains reachable on phone.
- No content is permanently hidden behind the fixed navigation.
- No giant empty gaps or overlapping manuscript sections.

## 6. Break-it inputs

Developer/security check:

- Enter `<img src=x onerror="alert(1)">` as the name and Resolve.
- Enter `"><svg onload=alert(1)>` as the name and Resolve.

Expected: the characters may be displayed as text, but **no script runs, no alert appears, and the page remains intact**.

## 7. Report every defect like this

**Device / browser:**  
**Page/section:**  
**What I did:**  
**What happened:**  
**What I expected:**  
**Can I reproduce it:** Always / Sometimes / Once  
**Severity:** P0 crash/security, P1 blocks task, P2 annoying but usable, P3 cosmetic  
**Evidence:** screenshot or screen recording

## Launch sign-off

Minimum recommended external matrix:

- Physical iPhone + Safari
- Physical Android + Chrome
- Desktop Firefox or Safari
- Windows Edge if Windows desktop is a launch target

NUMER is release-ready only when the matrix has **zero open P0/P1 issues** and the touch torture test passes on both physical mobile platforms.
