# Geometry 5 — Phase 3 Targeted QA

## Scope
Phase 3 verification only. Full visual/responsive/localization acceptance remains Phase 4.

## Passed checks
- JavaScript syntax: `bank.js` and `app.js` pass `node --check`.
- Canonical bank count: 30 questions.
- Difficulty distribution: CORE 10, CHALLENGE 10, ADVANCED 10.
- Bank coverage: every canonical question ID C1–C10, H1–H10, A1–A10 is present in the centralized bank.
- Synthesis Practice Bank exposes all 30 questions through Teacher Pass exact-question selection.
- Canonical answer values pass the shared field validator for all stored answer fields.
- Structural `Change Problem` preserves the active difficulty band and prioritizes a different problem family when available.
- `Previous Problem` history stores real question IDs and therefore preserves each problem's original level/family.
- EN/ID generated practice controls were checked through the shared rendering function.
- Per-question hints, attempts, workpad state, solution support, and per-level solved tracking use centralized question IDs.
- Teacher Pass problem-family and exact-question controls use the same central bank as inline practice.
- Supplied mascot assets remain untouched: 18 PNG files present.
- Phase 2 A–O lesson functions and existing reasoning interactions remain in the build.

## Targeted logic test output
```text
COUNT 30 {"core":10,"challenge":10,"advanced":10}
VALID true
S_OPTIONS 30
CHANGE C1 C2 core core method sine-side
HISTORY ["C1","C2"]
ID true true
LEVEL_STAY core true
LEVEL_STAY challenge true
LEVEL_STAY advanced true
```

## Visual / browser note
The current execution environment blocks local `file:`, `data:`, and loopback HTTP navigation in Chromium by organization policy. Therefore no new browser screenshot is claimed for Phase 3. Full browser-level visual QA is intentionally reserved for Phase 4; Phase 3 was verified through syntax checks, bank/data checks, and Node execution of the shared practice logic.

## Known issues
- Some highly focused inline subtopics have only one canonical question at a given level. In those cases `Change Problem` is disabled with a clear message rather than silently changing difficulty or inventing a numeric clone. The Synthesis bank has all 10 questions per level for full structural rotation.
- No Paper 1/2/3 mode is added because the canonical source does not provide those tags.
