# Geometry 5 UX1 — Interaction QA

**Status: SOURCE AND LOCAL-HARNESS CHECKS PASS; BROWSER QA INCOMPLETE.** This record separates checks that could be run in the workspace from desktop/mobile/keyboard checks that require a browser view of the site. It does not claim full UX acceptance.

## Automated and synthetic checks completed

- `app.js` passes `node --check`.
- A synthetic `wire()` harness invoked the Unit E, M, and H event bindings while the Unit C mapper was absent. The previous unconditional mapper initialization threw before these controls could be wired. After the guard, each tested unit reached its input callback and saved state.
- Local math/SVG harness checked E at 30°, 60°, 90°, 109°, 120°, and 150°: vertex, opposite side, angle label, and acute/right/obtuse explanation agree.
- H ray endpoint and East/North components were checked at 000°, 045°, 090°, 180°, 270°, and 359°. Zero degrees is preserved across saved state rather than falling through to a default.
- M ray/circle construction and solution count were checked at b=4, 5.9, 6, 6.1, 8, 9.3, 6/sin(40°)≈9.334343, 9.4, and 11. Result counts: 1, 1, 1, 2, 2, 2, 1 tangent, 0, 0. Endpoint coordinates agree with the rendered ray and fixed radius a=6.
- The 30 canonical Practice Bank IDs, all 92 answer fields, and 88 unit references were checked. Stored answers are accepted and obvious incorrect answers rejected. `bank.js` is unchanged from R3 (SHA-256 `15de48cd0a0c8024a109a5754a34ed278965b4574407b2eefc457d6e48f86bfb`).
- Local SVG raster inspection was completed for the E angle states and I–N geometry outputs. This does not equal full browser inspection at target viewport widths.

## Interaction inventory

| Unit / control | Initial state | Action | Expected mathematical result | Expected visual result | Actual evidence | Desktop | Mobile | Keyboard | Result |
|---|---|---|---|---|---|---|---|---|---|
| Home / unit navigation | Home | Open a unit and return | Same lesson state is restored | Correct unit content renders; no interaction setup crash | Shared missing-mapper throw fixed in source; browser navigation not run | Not tested | Not tested | Not tested | Source verified |
| Language EN ↔ ID | Saved language | Switch language | Geometry state unchanged | Labels and explanations localize without losing control state | Not browser-tested | Not tested | Not tested | Not tested | Not tested |
| Teacher Pass | Off/on | Toggle and select exact question | Selected canonical item remains correct | Selector and practice view update | Bank and source audit only | Not tested | Not tested | Not tested | Not tested |
| A–S idea stepper | First idea or saved step | Next/previous | No math state altered | One concise idea shown; counter/buttons update; chosen step saves | Source handler inspected; no browser event run | Not tested | Not tested | Not tested | Source verified |
| Guided examples | Steps concealed | Reveal successive reasoning | Steps reveal in order | Explanation reveals incrementally | Source inspection only | Not tested | Not tested | Not tested | Not tested |
| B method explorer | Six valid scenarios | Select a scenario | Exposes appropriate method for that structure | Feedback identifies the route; exploration is explicitly not a single-answer quiz | Source and text inspected | Not tested | Not tested | Not tested | Source verified |
| C opposite-pair mapper | Pair a selected | Select a, b, or c | Correct opposite side-angle pair selected | Both side and opposite angle emphasized; other pairs dimmed | Existing R3 implementation retained; browser regression not run | Not tested | Not tested | Not tested | Not re-tested |
| D ambiguous SSA reveal | One configuration | Reveal second candidate | Supplementary candidate shares sine condition | Second admissible intersection/configuration appears | Existing R3 implementation retained; browser regression not run | Not tested | Not tested | Not tested | Not re-tested |
| E cosine slider | Saved angle (default 54°) | Move through acute/right/obtuse | c=√(7²+10²−140 cos C) | Vertex, angle arc/label, opposite side and readout move consistently | Synthetic math/SVG states 30°,60°,90°,109°,120°,150°; event guard tested | Not tested | Not tested | Not tested | Local harness pass |
| E SAS/SSS tabs | Saved use case | Choose SAS or SSS | Same rule, correct unknown role | Relevant compact use panel changes | Source inspected; browser not tested | Not tested | Not tested | Not tested | Source verified |
| H bearing slider | Saved bearing | Set tested values | E=distance·sin β; N=distance·cos β | Ray rotates clockwise from North; arc, endpoint and components agree | Synthetic endpoint/component checks at 000°,045°,090°,180°,270°,359° | Not tested | Not tested | Not tested | Local harness pass |
| J gateway stages | Saved stage | Advance 1→2→3 | No solved value inserted | First triangle → shared quantity → target triangle emphasis changes | Source/SVG inspection; no browser control run | Not tested | Not tested | Not tested | Source verified |
| M feasibility slider | Saved b | Move across critical values | Circle/ray intersections report exact 0/1/2 counts; tangency is one | Center and candidate triangles move; status matches intersections; slider uses local updates | Synthetic geometry tests listed above; no browser drag run | Not tested | Not tested | Not tested | Local harness pass |
| M tangency button | Current b | Select boundary | b=6/sin40° | Exact tangent point/right-angle marker and one-solution status | Synthetic event/math check | Not tested | Not tested | Not tested | Local harness pass |
| N route tabs | Saved route | Select cosine / bisect | Both yield same chord relation | Whole isosceles triangle changes to bisected right triangles | Source and SVG raster inspected; browser tab click not run | Not tested | Not tested | Not tested | Source/render verified |
| Practice level selector | Saved level | Change difficulty | Question remains within canonical bank | Prompt/control state refreshes | Bank content audit only | Not tested | Not tested | Not tested | Not tested |
| Check / hints / Final Support | Question active | Check; reveal hints/support | Validation and support remain tied to current question | Feedback/reveals update | Answer fields checked in harness; browser sequence not run | Not tested | Not tested | Not tested | Partial source/math |
| Change / Previous Problem | Question history | Navigate forward/back | Correct canonical IDs return | Prompt and answer draft restore as designed | Bank IDs audited; persistence not browser-tested | Not tested | Not tested | Not tested | Not tested |
| Answer drafts / workpad | Draft present | Navigate, rerender, revisit | Draft/workpad remain associated with state | Entered work remains available | Source not end-to-end browser-tested | Not tested | Not tested | Not tested | Not tested |
| Completion / progress | Unit incomplete | Complete and revisit | Completion state persists | Footer/progress reflects completion | Not browser-tested | Not tested | Not tested | Not tested | Not tested |

## Browser-only checks not completed

The available browser surface rejected workspace `file://` access. The permitted route here does not provide an approved browser-accessible preview, so no local HTTP server or indirect browser execution was used. Consequently, the following remain **NOT TESTED**: desktop at 1365 px, tablet at 768 px, mobile at 390 px; real pointer/touch dragging; keyboard-only operation and focus order; EN↔ID persistence; Teacher Pass interaction; practice history/drafts/workpad/hints/completion/local persistence; and full A–S browser-rendered diagram/text alignment.

Do not interpret source/harness results as browser-level PASS. Complete these checks in an approved browser preview before release acceptance.
