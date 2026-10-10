# Geometry 5 R4 — Unfrozen QA Record

**Status: NOT FROZEN.** This document records completed source, mathematical, and rendered-SVG checks for the R4 working candidate. It does not claim that R4 passed the requested full browser-level or responsive QA. The final frozen ZIP and `FINAL_REPAIR_QA.md` have therefore not been produced.

## Automated checks

- `app.js` and `bank.js` pass Node syntax checks.
- The canonical practice bank is unchanged from the R3 baseline: SHA-256 `15de48cd0a0c8024a109a5754a34ed278965b4574407b2eefc457d6e48f86bfb`.
- All 30 canonical question IDs remain distinct and referenced by unit banks. The original 30 IDs and question mathematics were not edited.
- All 92 canonical answer fields accept their stored answer under the app's actual `validateField` function; obvious incorrect responses are rejected.
- M feasibility geometry was checked at b=4, 5.9, 6, 6.1, 8, 9.3, 6/sin(40°)≈9.3343429612, 9.4, and 11. Counts were 1, 1, 1, 2, 2, 2, 1 tangent, 0, and 0 respectively. The valid endpoints were checked against the ray and radius; the tangent marker was checked in the local SVG updater.
- A simulated M slider event at b=9.4 confirmed the range handler updates the actual fractional state, circle center, candidate geometry, and 0/1/2 status locally; the exact tangency control also sets b=6/sin(40°) and updates the marker/status. The handler uses local SVG/state updates and does not invoke the global page renderer. The J stage controls and N route tabs likewise update their own visual regions. The practice bank file is byte-for-byte unchanged.

## Manual geometry / pedagogical visual checks completed

The updated I–N SVG helper output was rendered to raster images and inspected for mathematical structure, label placement, clipping, and the visual difference between staged/routes/states. This is a manual inspection of rendered SVG output, **not** a substitute for inspecting the complete app in a browser at viewport sizes.

- **I:** the cliff is vertical; the observer horizontal and ground are parallel; the sight line and the depression/elevation arcs sit at their respective horizontal-to-sight-line intersections. The 50 m height and horizontal-distance problem form the intended right triangle.
- **J:** the staged quadrilateral shows △ABC as the first solvable triangle, AC as the shared gateway side, and △ACD as the target. The diagonal and labels change emphasis by step without inserting a solved diagonal value.
- **K:** two triangles show equal 40° included angles; the premise explicitly states equal area. Side labels correspond to 8 and 12 in the first triangle and 6 and x in the second, supporting cancellation of the common sine factor.
- **L:** x+1 and x+3 are attached to the sides enclosing the 60° angle; 7 labels the opposite side. No solved root is present in the initial diagram.
- **M:** the drawing is constructed from a fixed 40° ray and a circle of radius a=6 centered at the end of b. Candidate triangles and intersection points track the tested solution count; at tangency the perpendicular marker is shown. The circle now fits within the SVG viewBox.
- **N:** the cosine route shows the whole isosceles triangle; the bisection route adds the perpendicular bisector, right-angle marker, half-chord labels, and θ/2. The SVG itself changes with the selected route.

## Repaired interactive visuals in the candidate

- **J gateway stages:** STEP 1 / STEP 2 / STEP 3 changes triangle, diagonal, labels, and explanatory note locally; the selected stage persists in app state.
- **M SSA feasibility explorer:** changing b locally moves the circle center and recomputes candidate intersections, triangles, radius labels, status, and note. A boundary button sets the exact tangency value. No full-page render is called by the slider handler.
- **N route comparison:** route tabs change the geometric construction as well as the formula panel and save the chosen route.

A–H interactions from R3 remain in the candidate and their source has not been intentionally replaced. R4 browser-level regression of those controls was not possible, so they are not marked as re-passed here.

## Required QA still blocked

The available browser surface rejected opening the workspace `file://` URL and only accepts HTTP/HTTPS. Its safety policy also prohibits serving the local project or using an indirect execution / CDP workaround. No compliant browser-accessible preview is available in this environment. Consequently, the following user-required checks remain outstanding:

- Full browser interaction testing for C, D, E, H, M, N, J, language switching, Teacher Pass, workpad/practice persistence, hints, completion, and local storage.
- Visual inspection of HOME and every unit A–S at 390 px, 768 px, and 1365 px, including sidebar, footer, wrapping, touch controls, and diagram legibility.
- Full-site integration inspection to confirm adjacent text and SVG state in every rendered lesson view.
- Browser-level validation of all practice flows, including Change Problem, Previous Problem, exact-question Teacher Pass selection, drafts, hints, and progress restoration.

The R4 changes are available as a **working candidate only**. Do not treat the candidate ZIP as the final frozen release until these checks pass in a permitted browser environment.
