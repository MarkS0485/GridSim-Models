# MODEL CARD: Swedish 400/220 kV transmission grid winter peak 2026-01-12 (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Swedish 400/220 kV transmission grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-12T08:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over se; local time CET (UTC+1)).
- Buses 320 (14 boundary points), branches 390 (lines 255, transformers 135), generators 808.
- Buses by kV: 400 kV 110, 220 kV 99, 20 kV 111.
- Dispatch 23352.8 MW (plant in this system) + boundary imports 2551.7 MW; demand 25519.9 MW (incl. boundary exports 1927.3 MW).
- Slack: 1 reference: Oskarshamn 3.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 320 | 128 (40.0%) | 0 (0.0%) | 81 (25.3%) | 111 (34.7%) |
| Branches | 390 | 0 (0.0%) | 252 (64.6%) | 133 (34.1%) | 5 (1.3%) |
| Generators | 808 | 666 (82.4%) | 0 (0.0%) | 142 (17.6%) | 0 (0.0%) |
| Demand points | 209 | 0 (0.0%) | 0 (0.0%) | 209 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 79 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 79 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of SE: 211 AC buses, 255 internal lines (3 underground / submarine in the model, given cable parameters), 24 transformers; 128 buses named from OSM.
- Systems: {'main': 209, 'island1': 1, 'island2': 1}; components 3 [209, 1, 1].
- Boundary points (cut ties, HVDC terminals, manual points): Denmark ac x2; Denmark hvdc x1; Finland ac x4; Finland hvdc x2; Germany hvdc x1; Lithuania hvdc x1; Norway ac x5; Poland hvdc x1; internal hvdc x3.
- 110-150 kV class layer: not in this round.
- Snapshot balance (esett+svk): generation by type 23352.9 MW, net import 624.5 MW, pumping 0.0 MW -> demand 23951.9 MW (the source's own load series: 24964.0 MW).
- Plants left out (islands, outside the boxes): {'rows': 5, 'mw': 222.39999999999998, 'by_fuel': {'oil': 126.0, 'wind_onshore': 96.4}}.
- Not modelled: internal HVDC relation/8184633-300-DC at way/1265541078-400 (main -> main): no flow published for it in the snapshot sources; not modelled (0 MW) [VERIFY]
- Not modelled: internal HVDC relation/8184633-300-DC at way/1265541077-400 (main -> main): no flow published for it in the snapshot sources; not modelled (0 MW) [VERIFY]

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 764.5 | 4.7 |
| biomass | 3637.7 | 766.2 |
| gas | 798.0 | 15.8 |
| hydro | 15232.0 | 11794.6 |
| interconnector | 2551.7 | 2551.7 |
| nuclear | 7184.0 | 6926.5 |
| oil | 2663.0 | 874.6 |
| other | 12.3 | 11.7 |
| pumped_storage | 91.0 | 76.9 |
| solar | 682.1 | 7.9 |
| wind_offshore | 188.0 | 35.5 |
| wind_onshore | 18372.4 | 2838.3 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Norway | 105.2 | way/299750661-220 (ac merged_way/150486182-220+3, share 0.06 by rating) |
| Norway | 401.8 | relation/11097406-420 (ac merged_way/232662155-420+2, share 0.24 by rating) |
| Norway | 401.8 | virtual_way/287684721:1-420 (ac way/287684721-420, share 0.24 by rating) |
| Norway | 382.6 | way/292593503-400 (ac way/292593505-400, share 0.23 by rating) |
| Norway | 401.8 | virtual_way/585198893:1-420 (ac way/585198893-420, share 0.24 by rating) |
| Denmark | 275.1 | way/101320612-400 (ac relation/5528438:b-400, share 0.42 by rating) |
| Denmark | 275.1 | way/101320612-400 (ac relation/5528440:b-400, share 0.42 by rating) |
| Denmark | 104.6 | way/1451345383-400 (hvdc relation/8184629-300-DC, share 0.16 by rating) |
| Finland | -211.8 | way/1025530508-400 (ac merged_way/1025530506-400+1, share 0.37 by rating) |
| Finland | -211.8 | way/400471060-400 (ac merged_way/71375664-400+1, share 0.37 by rating) |
| Finland | -94.8 | way/41906390-400 (hvdc relation/3391954-500-DC, share 0.16 by rating) |
| Finland | -59.3 | way/80702333-400 (hvdc relation/8184631-400-DC, share 0.10 by rating) |
| Lithuania | -732.5 | relation/10629005-400 (hvdc relation/8185455-300-DC, share 1.00 by rating) |
| Poland | -617.1 | relation/14939275-400 (hvdc relation/3392010-450-DC, share 1.00 by rating) |
| Germany | 203.8 | way/28390455-400 (hvdc relation/3918230-450-DC, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 252 overhead lines (every one), 3 cables kept static; per line in ambient_ratings.json
- components not joined to a modelled system left out: 2 buses in 2 components (largest 1 buses; e.g. ['virtual_way/1348774144:0-400', 'way/217032425-400'])
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 108 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- RfG rule (Regulation (EU) 2016/631 Art. 5, Nordic limits: type B 1.5 MW, type C 10 MW): 34 running units (98.1 MW) below their voltage-control threshold set pq at unity power factor (documented rule; national thresholds [VERIFY])
- synchronous plant moved behind 111 lumped GSUs (31248 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; hydro 152/188 units; thermal 5/66 units; nuclear 6/6 units. Offline units in the case: 104 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Oskarshamn 3 at Ekhyddan 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- reactive repair staged by load scaling: shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage from the previous stage's shunts (estimated)
- bus shunts placed where the snapshot needs reactive support (41 passes of a Newton solve without reactive limits): 11 reactors 590 MVAr, 68 capacitors 6150 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 79 buses, 6150 MVAr capacitors and 590 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Oskarshamn 3 takes the balance (losses and the losses-allowance error); synthetic
- No demand is moved: the India radial-chain relief is not used in this batch.

Assumed (typical values or documented rules, not fitted; tagged estimated with [VERIFY]):

- losses allowance 1.5 % of the balance demand (the slack takes the rest)
- EHV transformers 2 x 400 MVA, x 12 %; EHV/HV couplings 2 x 250 MVA, x 12 % (one per EHV site and HV class); X/R 40
- HV lines single ACSR about 585 mm2: R 0.060, X 0.400 ohm/km, C 9 nF/km, 870 A; cables X 0.12-0.13 ohm/km, C 0.20-0.25 uF/km
- GSU x 14.5 % own rating, X/R 40; generator Q range -0.30 to +0.62 x MW; converter +/-0.33 x MW; load power factor 0.97
- unit commitment largest first to 0.8 loading (nuclear 0.95); listed fleet short -> embedded remainder by population
- plants >= 250 MW on the top EHV class; above one HV circuit (870 A, 0.85 pf) on EHV; < 100 MW on HV
- boundary flows split over a neighbour's tie points by tie rating
- HV layer (when built): OSM ways split at T-junctions; a dangling line end, or a PyPSA virtual EHV line end, within 2.0 km (TAGGED_SNAP_KM, assumed) of a substation whose OSM voltage tag carries that class ends there (mapping gap rule)
- HV layer (when built): EHV substations whose own OSM voltage tag lists a level below 100 kV take demand (attested supply to unmodelled distribution); plant under 100 MW on an HV bus only up to the bus's connected circuit capacity (rating x circuits of its lines and couplings), else the next HV bus within 40 km, else the nearest EHV bus (grid-access rule; RD 1183/2020 for Spain [VERIFY])
- load buses take the demand of the NUTS 3 region whose polygon contains them; r1: nearest label point)
- RfG rule (when rfg_area is set): Regulation (EU) 2016/631 Art. 5 Table 1 limits (CE type B 1 MW / C 50 MW; Nordic 1.5 / 10 MW): converters below type C and synchronous units below type B run pq at unity pf; the synchronous ones sit on the grid bus, not behind a GSU; national thresholds may be lower [VERIFY]
- reactive repair never on generator terminal buses (shunts belong on the grid bus)

## Known gaps

- No TSO impedances: EHV line R/X/B come from PyPSA-Eur's standard overhead types (400 / 380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; real conductors differ; cables use typical XLPE values.
- EHV transformers: 2 x 400 MVA, x 12 % at every 400/220 kV site PyPSA marks; real unit counts unknown.
- 110-150 kV class not modelled in this round: demand and small plant sit on EHV buses.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by NUTS 3 population (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31) (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- GISCO NUTS 2024 regions ((c) EuroGeographics) and Natural Earth (public domain): geography.json.

Licence: pending a licence check (see ATTRIBUTION.txt and LICENSING.md).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf sweden-spine-400-220-r5   (flat start: vm 1, vaDeg 0; exit 0, 0.6 s)
Power flow - Swedish 400/220 kV transmission grid winter peak 2026-01-12 (UnvalidatedAtScale) (320 buses)
  converged in 9 iteration(s), mismatch 2.14E-010 pu   losses 1235.319 MW / -2416.413 MVAr
  voltage range 0.9521 - 1.0325 pu
  lowest voltages:
      bus 187    0.9521 pu     -8.007 deg
      bus 115    0.9522 pu     -8.033 deg
      bus 146    0.9527 pu     -7.932 deg
      bus 287    0.9527 pu     -7.932 deg
      bus 123    0.9532 pu     -7.841 deg
      bus 141    0.9539 pu    -18.515 deg
      bus 181    0.9540 pu    -18.330 deg
      bus 209    0.9540 pu    -18.717 deg
      bus 163    0.9545 pu     -7.341 deg
      bus 171    0.9548 pu     -7.572 deg
      bus 186    0.9551 pu    -19.209 deg
      bus 206    0.9551 pu    -18.620 deg
(warm start baked into buses.json from that solve: flat start took 9 Newton iterations)
$ gridsim pf sweden-spine-400-220-r5 (warm start)   (exit 0, 0.4 s)
Power flow - Swedish 400/220 kV transmission grid winter peak 2026-01-12 (UnvalidatedAtScale) (320 buses)
  converged in 5 iteration(s), mismatch 2.14E-010 pu   losses 1235.319 MW / -2416.413 MVAr
  voltage range 0.9521 - 1.0325 pu
  lowest voltages:
      bus 187    0.9521 pu     -8.007 deg
      bus 115    0.9522 pu     -8.033 deg
      bus 146    0.9527 pu     -7.932 deg
      bus 287    0.9527 pu     -7.932 deg
      bus 123    0.9532 pu     -7.841 deg
      bus 141    0.9539 pu    -18.515 deg
      bus 181    0.9540 pu    -18.330 deg
      bus 209    0.9540 pu    -18.717 deg
      bus 163    0.9545 pu     -7.341 deg
      bus 171    0.9548 pu     -7.572 deg
      bus 186    0.9551 pu    -19.209 deg
      bus 206    0.9551 pu    -18.620 deg
$ gridsim physics-check sweden-spine-400-220-r5   (exit 0, 0.5 s)
Physics-law audit  -  sweden-spine-400-220-r5  (320 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.09E-010 | MW | independent dissipation 1235.318819 MW (branch 1235.3188 + shunt 0.0000) vs reported loss 1235.318819 MW |
| 2 | Ohm's law | Holds | 2.23E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.05E-010 | MW | total network loss 1235.318819 MW vs reported 1235.318819 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.74E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.14E-008 | MVA | same residual as law 6, reactive component included at 161 PQ bus(es), by the bus types the solve ended with; 12 of them declared PV and solved as PQ (12 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## Inference round sweden-spine-400-220-r8 (base sweden-spine-400-220-r5, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 0 (0 circuits / units, 0 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), with no new overload, no existing overload made worse by more than 1 point, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 57 sites, 5640 MVAr capacitive / 30 MVAr inductive, replacing the generic repair (79 shunts, 6150 / 590 MVAr).
- Taps: 11 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- Units at a reactive limit: base round 12; held because generic repair shunts on generator terminal buses were moved to their public substation: 20 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 9 | 13 |
| iterations_warm | 5 | 10 |
| loss_mw | 1235.319 | 1235.518 |
| vmin_pu | 0.952 | 0.954 |
| vmax_pu | 1.033 | 1.033 |
| angle_spread_deg | 93.633 | 93.715 |
| over_100 | 1 | 1 |
| over_120 | 1 | 1 |
| over_140 | 0 | 0 |
| auto_cap_mvar | 6150.000 | 0 |
| auto_reactor_mvar | 590.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 5670.000 |
| units_held_at_q_limit | 12 | 29 |
| cpf_lambda | 1.109 | 1.107 |
| physics_pass | True | True |

Worst after: 132.1 % gsu:way/279842937-400 (Ekhyddan 400kV gen bus - Ekhyddan 400kV); 97.4 % way/38105008-400-220 (Kolbotten 400kV - Kolbotten 220kV); 85.9 % way/261447466-400-220 (Ekudden 400kV - Ekudden 220kV)

Inferred feeds:

- none

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: +530 MVAr at Vittersjo 400kV
- inferred compensation 2: +320 MVAr at FT6 Barseback 400kV
- inferred compensation 3: +310 MVAr at Kilanda 400kV
- inferred compensation 4: +280 MVAr at Kolstad 400kV
- inferred compensation 5: +260 MVAr at Kruseberg Substation 400kV
- inferred compensation 6: +250 MVAr at Stackbo 220kV
- inferred compensation 7: +200 MVAr at Soderasen 400kV
- inferred compensation 8: +180 MVAr at Hjalta 400kV
- inferred compensation 9: +180 MVAr at OSM way/469037951 220kV
- inferred compensation 10: +180 MVAr at Haradsbo 400kV
- inferred compensation 11: +180 MVAr at Stallverk Hurva 400kV
- inferred compensation 12: +180 MVAr at Hatuna 220kV
- inferred compensation 13: +150 MVAr at Djurmo 400kV
- inferred compensation 14: +140 MVAr at Ostansjo 400kV
- inferred compensation 15: +140 MVAr at Malsta 220kV
