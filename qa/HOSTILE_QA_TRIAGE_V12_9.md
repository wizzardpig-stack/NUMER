# NUMER V12.9 Independent Hostile QA Triage

**Date:** 2026-09-19  
**Source candidate reviewed:** V12.8 Calculation Audit RC  
**Repair candidate:** `qa/NUMER_V12_9_HOSTILE_QA_FIX_RC.html`  
**Overall status:** **HOLD — major hostile-QA blockers repaired; regression + physical-device sign-off still required**

## Confirmed and repaired in V12.9

| Finding | V12.8 status | V12.9 action |
|---|---|---|
| Accented Latin letters dropped | Confirmed | Added Latin diacritic normalization plus explicit mappings for Æ/Œ/Ø/Ł/Đ/Ð/Þ. |
| Apostrophe splits O'Brien | Confirmed | Apostrophes no longer create a name-part boundary. |
| Mixed/non-Latin input silently partially resolves | Confirmed | Core Resolve now rejects unsupported non-ASCII remnants with a clear Latin-script message. |
| Persistent XSS through tampered computed archive records | Confirmed threat under localStorage tampering | Archive no longer persists computed result objects. It stores only inputs + Y mode and recomputes validated results on load. Letter SVG title is escaped as defense-in-depth. |
| Malformed vault breaks Archive | Confirmed | Vault must be an array; each record is validated/hydrated independently; invalid records are dropped instead of bricking startup. |
| Compare cannot select index 0 on right | Confirmed | Removed the `|| 1` zero-index bug and preserved valid selections. |
| Compare resets on every open | Confirmed | Previous valid select values are preserved. |
| Archive silently evicts after 30 | Confirmed | Archive now refuses the 31st save with a visible message. No silent data loss. |
| Duplicate rapid archive saves | Confirmed | Exact duplicate plates are rejected. |
| Archive remove target too small / keyboard inaccessible | Confirmed | Remove is now a separate 44×44 minimum button with an accessible label. |
| One-tap permanent delete | Confirmed | Removal now requires confirmation. |
| Storage write failure still reports success | Confirmed | Storage writes return success/failure; failed archive/clear actions report failure and roll back UI state. |
| Archived values frozen across algorithm fixes | Confirmed | Minimal inputs are persisted and recomputed on load under the archived Y mode. |
| Ryan adaptive-Y inconsistency | Confirmed | Ryan is added to the known exception set. UI now explicitly labels Adaptive as a heuristic. |
| Mobile view switch retains deep scroll position | Confirmed | Switching views resets to the top. |
| Name Lab pathological paste | Confirmed risk | Both lab inputs now have the same 80-character cap as the main form. |
| Future birth dates accepted | Confirmed | Resolve rejects invalid/future dates. |

## Revalidated on the committed V12.9 artifact

- JavaScript parses successfully.
- Accented examples normalize correctly:
  - José → JOSE
  - Chloé → CHLOE
  - Björk → BJORK
  - Renée Smith → RENEE SMITH
  - Müller → MULLER
  - François → FRANCOIS
  - Søren → SOREN
  - Łukasz → LUKASZ
- O'Brien is treated as OBRIEN rather than two independent name parts.
- Pure non-Latin and mixed Latin/non-Latin inputs are detected rather than silently partially calculated.
- Raw computed archive-object persistence is absent.
- Compare's index-0 fallback defect is absent.
- 30-plate capacity warning, duplicate protection, 44px delete control, delete confirmation, and honest storage-failure messages are present.

## Open findings intentionally not hidden by this repair pass

These remain for later QA/design adjudication:

1. Karmic-debt semantics need one documented rule. This is an interpretive-domain policy issue, not a JavaScript arithmetic failure.
2. Adaptive Y remains inherently phonetic and therefore heuristic for arbitrary names. Forced vowel/consonant modes remain the authoritative override.
3. The 3·4·5 visual geometry requires a dedicated figure correction pass.
4. Still mode must be checked against every ambient animation.
5. Cosmograph inspection needs keyboard/focus semantics.
6. Selected navigation/settings states need `aria-current` / `aria-pressed` and view-change focus/announcement behavior.
7. Browser Back/history behavior is still not app-like; scroll-reset is fixed but URL routing/history is not implemented.
8. Pinch-zoom + horizontal pan still requires a real-device check.
9. Trace/figure truncation copy should disclose visual limits.
10. PWA, analytics, monitoring, legal pages, and store packaging remain separate launch gates.

## Promotion rule

V12.9 is not production yet.

Before promotion:
- rerun the hostile QA suite against V12.9;
- run physical iPhone Safari and Android Chrome touch torture tests;
- resolve any remaining P0/P1 regressions;
- complete legal, monitoring, analytics and final accessibility gates required for the chosen web launch scope.
