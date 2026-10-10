# Geometry 5 — Repair R2 checkpoint

## Scope and baseline

R2 continues from `Geometry5_Trigonometric_Geometry_Repair_R1.zip`. It revises the academic explanation for Units I–O and Synthesis (S). R1's Units A–H remain intact. The Practice Bank engine and question data are preserved.

## Explanations expanded

- **I — Elevation & depression:** defined line of sight and observer horizontal; distinguished elevation/depression from vertical angles; explained the parallel-line angle transfer; connected the justified right triangle to the correct trigonometric ratio and contextual target.
- **J — Multi-triangle geometry:** defined a gateway quantity; made the target ← missing information ← supplying triangle dependency explicit; explained why the target cannot be solved directly before the transfer; staged the shared-diagonal example.
- **K — Reverse reasoning:** contrasted forward and reverse question structures; derived equal-area equations; explained when and why a common non-zero sine factor cancels without numerical evaluation; identified when cancellation is invalid.
- **L — Algebra + trigonometric geometry:** separated equation solving from geometric validation; established a candidate-validation sequence covering positive lengths, angle domain, triangle inequality, and the original condition; strengthened the parameter example's reasoning.
- **M — Feasibility & constraints:** connected the geometric explanation back to Unit D's inverse-sine ambiguity; derived `h = b sin A` as the perpendicular distance from a circle centre to a ray; explained zero, one (tangent), and two intersections and their boundary conditions.
- **N — Cumulative geometry:** explained both chord routes: cosine rule in the whole isosceles triangle, and symmetry/bisection followed by right-triangle trigonometry; compared their steps and the structures each reveals.
- **O — Advanced synthesis:** replaced labels alone with representative mini-cases for hidden methods, parameters, constraints, gateway quantities, and route comparison, within the existing course tools.
- **S — Synthesis:** replaced the short summary with a flexible nine-question pathway from target identification through geometric validation, plus a consolidated tool map and common checks.

## Continuity across A–S

The new I introduction explicitly carries the right-triangle retrieval and method-choice habits from A–H into contextual line-of-sight geometry. J develops the multi-triangle dependency. K and L reverse and parameterise that dependency. M returns to the SSA ambiguity first introduced in D. N compares two valid representations using previously learned tools. O develops those structures into advanced chains, and S consolidates the complete progression. The pathway is a guide for judgment, not a rigid algorithm.

## Preserved systems

State and persistence, navigation and section IDs, bilingual switching, Teacher Pass, completion behavior, Practice Bank IDs and mathematics, difficulty levels, Change Problem, Previous Problem, hints, Final Support, workpad, and history remain in place. `bank.js` and every R1 project file other than `app.js` are unchanged.

## Verification

- JavaScript syntax check (`node --check app.js`) passed.
- R1 ZIP archive integrity passed.
- R1-to-R2 file comparison: only `app.js` changed before adding this checkpoint and the R2 QA report.
- `bank.js` is byte-for-byte identical to R1.
- Numerical checks passed for the gateway-diagonal example (`AC≈9.848858`, `CD≈5.970407`), equal-area recovery (`x=16`), parameter roots (only `x=-2+√43` gives valid side lengths), SSA 0/1/2 boundaries, and equality of both chord formulas.
- English and Indonesian paired explanatory content is present in all revised sections.
- Browser-based visual and interaction QA was not performed in this repair phase.

## Deferred to R3/R4

The existing geometry visuals were not comprehensively rebuilt or re-audited. In particular, the SSA feasibility diagram still needs a dedicated visual pass to show the perpendicular foot and right-angle marker accurately, and the elevation/bearing/circle diagrams need full placement, label, and responsive review. Existing interactions were preserved; their teaching value and visual behavior still require browser-level testing. These are intentionally deferred to the planned geometry visual and interaction phases.

**R2 complete. Stop here; do not revise Units I–S further until the next phase is requested.**
