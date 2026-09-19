# NUMER V12.9 QA Status

**Release candidate:** V12.9 Hostile QA Fix RC  
**Qualification date:** 2026-09-19  
**Artifact:** `qa/NUMER_V12_9_HOSTILE_QA_FIX_RC.html`  
**Status:** **HOLD — REGRESSION + PHYSICAL DEVICE SIGN-OFF REQUIRED**

## Green gates

- Core calculation arithmetic audit: PASS
- Interpretation coverage: PASS
- V12.6 typed-input DOM XSS: FIXED
- V12.8 accented Latin name handling defect: FIXED
- Archive persistence architecture: HARDENED
- Malformed vault recovery: FIXED
- Compare index-0 defect: FIXED
- Archive silent eviction: FIXED
- Duplicate archive save: FIXED
- Archive delete target / confirmation: FIXED
- Storage false-success reporting: FIXED
- Archive algorithm/Y-mode recomputation: FIXED
- Main form unsupported-script handling: FIXED
- Future DOB rejection: FIXED
- Mobile view scroll reset: FIXED
- V12.9 JavaScript syntax/static regression assertions: PASS

## Still pending before PUBLIC READY

- Independent hostile-QA regression run on V12.9
- Physical iPhone Safari
- Physical Android Chrome
- Desktop Firefox / Safari
- Windows Edge if in launch matrix
- Mobile gesture torture test
- Final accessibility pass
- Privacy Policy + Terms
- Production error monitoring
- Product analytics decision/implementation
- Open semantic/visual P2 items documented in `HOSTILE_QA_TRIAGE_V12_9.md`

## Production rule

Do not replace `index.html` until the exact V12.9-or-later candidate has zero open P0/P1 defects and the external device matrix is signed off.
