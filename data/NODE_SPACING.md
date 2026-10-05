# Conservative customer relocation

Only preview fixture `three_affected_local_candidate_16.json` is updated. Original is preserved in `node_spacing_original.json`. Official `presentation_scenario.json` is unchanged.

Moved customer IDs 9, 10, 24 to real OSM nodes reachable from and back to depot. Kept all other customer coordinates, event definition, roles, solver options, demands, time windows, and vehicle capacity unchanged. No runtime code changed.

Approximate straight-line separation in meters:

| Pair | Before | After |
|---|---:|---:|
| 9–15 | 3.8 | 90.6 |
| 1–9 | 7.3 | 79.8 |
| 7–10 | 73.5 | 86.9 |
| 7–24 | 41.9 | 75.3 |
| 10–24 | 80.2 | 113.2 |

Existing real three-vehicle validator ran all three role pairs. Detector remains V2 at 31069 ms. V4/V5/V6 receive updates avoiding the incident. All customers complete and positions remain continuous. Detailed evidence: `node_spacing_conservative_validation.json`.

The pre-existing strict visual acceptance failures remain: `detours_not_distinct`, `vehicle_6_weak_visible_change`. This is not a fully accepted new presentation scenario; it preserves the current scenario behavior while modestly improving two remote customer clusters.

Larger relocations were rejected because the detector was not on the incident edge at the fixed injection time. An earlier proposal also contained an unreachable directed-road node and was replaced with candidates filtered by depot connectivity. Central corridor nodes were not relocated.

## Further spacing (2026-10-05)

Customers 10 and 24 moved farther on valid OSM nodes. Latest pair distances: 7–10 158.5 m; 10–24 232.4 m; 7–24 135.9 m. Three real pairwise simulation validations preserve detector V2 at 31069 ms, V4/V5/V6 avoidance and fleet completion. Existing strict visual limitations remain unchanged. Evidence: `node_spacing_expanded_validation.json`; immediate prior fixture: `node_spacing_before_expansion.json`.
