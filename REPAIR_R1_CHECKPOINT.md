# Geometry 5 — Repair R1 checkpoint

## Scope

R1 reconstructs the academic exposition and learning sequence for **Units A–H only**. It preserves the Phase 4 project as its implementation baseline. Units I–S, the Practice Bank engine, and the full geometry-visual rebuild are outside this phase.

## Units revised

- **A — Right-triangle retrieval:** clarified when a right angle must be established, what opposite/adjacent/hypotenuse mean relative to a reference angle, what sin/cos/tan compare, when Pythagoras is simpler, and how to sanity-check results.
- **B — Choosing a method:** introduced SAS, SSS, ASA/AAS, SSA, and included angle before relying on them; separated preliminary geometry from method selection, substitution, algebra, and validation; added gateway quantities as a deliberate step.
- **C — Sine rule:** established standard opposite-side/opposite-angle pairing, both equivalent forms, when a complete pair makes the rule available, the area-based justification, and side-angle plausibility checks.
- **D — Ambiguous sine-rule case:** connected supplementary angles to two actual SSA configurations; distinguished inverse-sine candidates from valid triangles and added the remaining-angle and geometry checks.
- **E — Cosine rule:** treated SAS and SSS separately, explained the role of the included angle, showed the rearrangement for an angle, and connected the 90° case to Pythagoras.
- **F — Strategic consolidation:** rebuilt the unit as a post-sine/post-cosine checkpoint covering angle sum, Pythagoras, similarity, gateway quantities, method choice, and final validation.
- **G — Trigonometric area:** derived the formula from perpendicular height with consistent (a=BC, b=CA, c=AB) notation; clarified included-angle pairing and reverse-area ambiguity. Corrected the diagram labels to match that notation.
- **H — Bearings:** introduced three-figure clockwise-from-North convention first; explained back bearings and conversion to internal angles; derived east/north components from the bearing reference and added directional checks.

All new explanation blocks have matched English and Indonesian content at the same mathematical depth.

## Preserved systems

Section IDs and navigation, Teacher Pass, completion and persistence architecture, all existing lessons outside A–H, the centralized Practice Bank and its IDs/mathematics, difficulty levels, structural Change Problem, Previous Problem, hints, Final Support, workpad, and language switching are retained. `bank.js` is byte-identical to the Phase 4 baseline.

## Verification

- `node --check app.js` passes.
- `bank.js` byte comparison against the supplied baseline passes.
- Static scope review confirms the academic bridge was added to A–H; no lesson function I–S was edited.
- Mathematical review checked opposite-pair notation, sine-rule area derivation, SSA candidate validity conditions, cosine-rule side/angle correspondence, area formula notation and height derivation, reverse-area bounds, bearing component orientation, and the two-leg bearing example's internal angle.
- Full interactive browser rendering was not available in this workspace, so runtime visual claims are limited to the static source and packaging checks.

## Intentionally deferred to R3

- Full geometry-diagram and SVG rebuild, including precise vertex/side placement, angle arcs, altitude feet, bearing compass layouts, and responsive visual alignment.
- Interaction redesign or extension of visual controls.
- Whole-site visual polish and comprehensive browser-based visual QA.

R1 makes the explanations self-contained without claiming that the existing diagrams have been fully repaired. Proceed to the planned visual phase separately.
