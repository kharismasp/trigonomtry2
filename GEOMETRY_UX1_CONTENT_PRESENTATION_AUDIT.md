# Geometry 5 UX1 — Content and Presentation Audit

**Scope:** progressive lesson presentation and interaction runtime across Units A–S. This is the UX1 working candidate, not a final freeze.

## Presentation changes

- Replaced the opening multi-card theory dumps with a saved, one-idea-at-a-time stepper. Each lesson starts with one concise explanation; the learner can move forward/back and return to the saved idea.
- Kept foundational meanings in the visible lesson flow. Additional derivations and longer reasoning remain available inside an explicit “Why does this work? · Formal reasoning” disclosure, rather than being deleted.
- Unit E now follows a web lesson rhythm: pose a prediction question, manipulate the triangle, observe acute/right/obtuse behavior, state the cosine rule, compare SAS and SSS use cases, then work a guided example and practice.
- Unit B now identifies its method buttons as valid scenarios for exploration, not a one-answer quiz. The selection feedback classifies the information structure.
- Existing staged or comparative lessons retain their interactions: C pair mapper, D supplementary SSA reveal, J gateway sequence, M feasibility explorer, and N route comparison.
- Lessons A–S continue the R1–R4 mathematical sequence: right-triangle retrieval and classification; sine/cosine/area; bearings and contextual geometry; linked triangles; reverse reasoning; algebraic candidates; feasibility; cumulative comparison; advanced synthesis; and a flexible consolidation pathway.
- Practice Bank `bank.js` is unchanged. No canonical Practice Bank IDs were restructured.

## Runtime repair

`wire()` initialized the Unit C opposite-pair mapper unconditionally. On Home and every non-C unit, the mapper element did not exist, so initialization threw before later controls—including sliders—were wired. The mapper setup is now guarded both in its helper and at the call site. E, H, and M controls then bind locally and update their own SVG/readout without invoking the full-page renderer.

Additional state/geometry repairs:

- Unit E updates the moving vertex, opposite side, included angle label, readout, explanatory acute/right/obtuse state, and persisted slider value together.
- Unit H preserves a valid 000° bearing and updates the clockwise-from-North ray, endpoint, arc, East component, and North component.
- Unit M uses the same baseline coordinates for the ray and constructed circle intersections; the slider preserves fractional values and updates geometry/status locally. A tangency control selects the exact boundary.

## Audit limitations

The source and synthetic checks pass as recorded in `GEOMETRY_UX1_INTERACTION_QA.md`. Browser rendering and interaction inspection at 390/768/1365 px could not be completed in this environment. In particular, responsive text rhythm, tactile control sizing, keyboard focus behavior, persistent state after real language/Teacher Pass changes, and actual page-level text/SVG adjacency still need browser verification. No complete UX acceptance or final release freeze is claimed.
