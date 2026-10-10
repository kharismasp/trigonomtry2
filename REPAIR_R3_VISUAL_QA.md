# Geometry 5 — Repair R3 Visual QA

## Scope and baseline

R3 uses `Geometry5_Trigonometric_Geometry_Repair_R2.zip` as its source baseline and repairs the visual and interaction layer in Units A–H only. Unit text, question-bank content, IDs, and units I–S were not intentionally changed. `bank.js` matches the extracted R2 baseline byte for byte.

## Repairs and visual audit

| Unit | Audit result and repair |
|---|---|
| A | Kept the right-triangle diagnostic but corrected its drawing to a proportional 5:12 leg ratio and centered the narrow triangle in its viewBox. The perpendicular marker belongs at A; labels 5 and 12 mark the perpendicular legs and `?` marks the hypotenuse. |
| B | Recast the method buttons as explicit structure explorations. Each option supplies a complete scenario and a suitable method explanation. The controls no longer act like a quiz in which every click is reported as correct. |
| C | Replaced the generic triangle with a fixed △ABC and conventional side placement: a=BC, b=CA, c=AB. Pair controls emphasize the selected side, its opposite angle arc, and its labels; other pairs are dimmed but remain legible. Angle text uses ∠A/∠B/∠C to distinguish it from the vertex names. The selected pair persists. |
| D | Rebuilt the SSA construction around a fixed-radius circle centered at C and an admissible ray from A. The initial view shows the given angle, baseline, first intersection, and fixed side construction. Revealing the second candidate shows the same circle intersecting the ray again at B₂, the extended ray, and the second triangle. The reveal state persists. The two drawn radii are both 125 units, and both points lie on the same 35° ray. |
| E | Rebuilt the explorer in conventional notation: a=7 and b=10 meet at included angle C, and the opposite side is c=x. Slider changes update the existing polygon, edges, moving vertex B, vertex label, angle arc, angle label, and side-label positions locally. The numerical readout and state use the same cosine-rule calculation. |
| F | Audited the strategy toolkit. It is a static classification/reference section rather than a geometry diagram or control, and it contains no pseudo-interactive diagram to retain. |
| G | Rebuilt the area visual with B and C at the base, a=BC, b=CA, and included angle C between a and b. The altitude from A to BC is shown as a dashed helper with foot D and a right-angle marker. The former duplicate/contradictory angle label is removed. |
| H | Rebuilt the compass drawing so the ray and endpoint follow bearing β clockwise from North. The arc and three-figure β label update with the ray; the east and north readouts use E=18 sin β and N=18 cos β. The major arc is selected for bearings above 180° so 270°–359° do not reverse direction. |

## Interaction and numerical checks

- E was checked at 25°, 54°, 90°, and 130°. The visible angle label matched each selected value. The calculated and drawn opposite side lengths agreed (approximately 4.70, 8.17, 12.21, and 15.46 units), and B moved to a different coordinate at every setting.
- H was checked at 000°, 045°, 090°, 180°, 270°, and 359°. The endpoint matched `(150 + 100 sin β, 150 − 100 cos β)` at each value. The bearing label was zero-padded and the arc used its major sweep for 270° and 359°. Component readouts follow the corresponding east/north sine and cosine values.
- C selection logic applies the chosen key to both side and opposite-angle elements, de-emphasizes the remaining pairs, updates the explanation and `aria-pressed` state, and saves the selection.
- D reveal toggles construction visibility and explanatory state without rendering the page again. E and H slider handlers mutate only their SVG nodes and nearby readouts; they do not call the global `render()` function. Each control saves its current value.
- B remains an exploration: selected states and explanations identify the chosen scenario without claiming correctness.

## Responsive and visual inspection

The inline SVGs use `width:100%`, `height:auto`, `max-width:560px`, and their own viewBoxes. SVGs were rasterized and visually inspected at 350 px, 520 px, and 560 px output widths. These represent the drawing area available in a roughly 390 px phone layout and the capped diagram width at tablet/desktop sizes. The labeled shapes remained within their viewBoxes, and the 350 px exports remained readable without shrinking the SVG to an icon.

A full browser session was not available in this environment: no browser executable was installed, so the complete page could not be manually exercised at exact 390 px, 768 px, and 1365 px viewport widths. The raster checks cover the SVG drawing itself, not every responsive page layout or browser-specific interaction rendering. This limitation is recorded rather than claiming a browser viewport pass.

## State and regression checks

- `node --check app.js` passes.
- The E/H SVG update helpers were exercised with numeric test doubles; angle labels, endpoints, arc direction, and opposite-side length were checked against the formulas.
- `bank.js` SHA-256 matches the extracted R2 baseline: `15de48cd0a0c8024a109a5754a34ed278965b4574407b2eefc457d6e48f86bfb`.
- Existing bilingual state, completion, hints, workpad, difficulty, practice history, Teacher Pass, and practice-bank systems remain in the R2 files and event wiring. Canonical practice IDs were not restructured.

## Deferred to R4

The full visual rebuild and broader page-level layout/interaction QA are deferred. In particular, full-page responsive inspection at exact viewport sizes and browser-specific animation/focus behavior require a browser runtime. No work beyond Unit H is included in R3.
