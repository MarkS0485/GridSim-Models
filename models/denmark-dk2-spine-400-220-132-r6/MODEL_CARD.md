# Danish DK2 (Zealand, Nordic synchronous area) 400/220/150/132 kV grid winter peak 2026-01-12 (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Danish DK2 (Zealand, Nordic synchronous area) 400/220/150/132 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-12T16:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over dk; local time CET (UTC+1)).
- Buses 153 (3 boundary points), branches 237 (lines 217, transformers 20), generators 84.
- Buses by kV: 400 kV 10, 220 kV 5, 150 kV 1, 132 kV 129, 20 kV 8.
- Dispatch 1808.9 MW (plant in this system) + boundary imports 905.9 MW; demand 2675.1 MW (incl. boundary exports 52.6 MW).
- Slack: 1 reference: Avedore.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 153 | 82 (53.6%) | 0 (0.0%) | 63 (41.2%) | 8 (5.2%) |
| Branches | 237 | 0 (0.0%) | 10 (4.2%) | 227 (95.8%) | 0 (0.0%) |
| Generators | 84 | 82 (97.6%) | 0 (0.0%) | 2 (2.4%) | 0 (0.0%) |
| Demand points | 77 | 0 (0.0%) | 0 (0.0%) | 77 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 8 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 8 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of DK: 48 AC buses, 56 internal lines (135 underground / submarine in the model, given cable parameters), 4 transformers; 176 buses named from OSM.
- Systems: {'dk1': 161, 'dk2': 145}; components 2 [161, 145].
- Boundary points (cut ties, HVDC terminals, manual points): Germany ac x3; Germany hvdc x1; Netherlands hvdc x1; Norway hvdc x2; Sweden ac x2; Sweden hvdc x1; United Kingdom hvdc x1; internal hvdc x2.
- 110-150 kV class layer: {'osm_line_ways': 2254, 'ways_not_grid_frequency': {'frequency 0': 58}, 'traction_substations_dropped': 11, 'ways_without_hv_class': 672, 'segments': 2400, 't_junction_splits': 818, 'routes': 2269, 'routes_kept': 368, 'stub_routes_pruned': 13, 'ends_snapped_within_km': 0.5, 'ends_snapped': 15, 'foreign_hv_buses_dropped': 1, 'ends_snapped_to_tagged_substation': 8, 'tagged_snap_km': 2.0, 'tagged_snap_examples': ['way/32235977 150 kV Herning (0.37 km, 150 kV)', 'way/103575499 150 kV Sonderborg (0.70 km, 150 kV)', 'way/253817668 Estrupvej (0.57 km, 150 kV)', 'way/131443963 132kV Masnedo (0.49 km, 132 kV)', 'way/131339681 132/50 kV Teglstrupgard (0.80 km, 132 kV)', 'way/253817668 Estrupvej (0.58 km, 150 kV)', 'way/253817669 150kV Lykkegard (0.59 km, 150 kV)', 'way/198614550 132 kV Hedegard (0.34 km, 132 kV)'], 'pypsa_virtual_ehv_buses_sited': 1, 'virtual_site_examples': ['virtual_way/385384761:0-400 -> way/98212652 400 kV Vendsysselvaerket (1.47 km)'], 'hv_buses': 258, 'hv_buses_by_kv': {'132': 129, '150': 129}, 'tee_junctions': 88, 'couplings': 31, 'max_couplings_at_one_hv_bus': 2, 'uncoupled_components_left_out': {'buses': 6, 'routes': 5, 'km': 81.0}, 'route_km_kept': 3101.9}.
- Snapshot balance (energidataservice): generation by type 1809.2 MW, net import 853.3 MW, pumping 0.0 MW -> demand 2662.5 MW (the source's own load series: 2662.5 MW).
- Plants left out (islands, outside the boxes): {'rows': 7, 'mw': 90.1, 'by_fuel': {'battery': 39.1, 'biomass': 37.0, 'solar': 14.0}}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 38.8 | 0.0 |
| biomass | 1185.0 | 834.7 |
| gas | 38.0 | 0.0 |
| interconnector | 905.9 | 905.9 |
| oil | 196.0 | 0.0 |
| solar | 840.4 | 0.0 |
| wind_offshore | 1071.0 | 740.8 |
| wind_onshore | 234.0 | 233.4 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Sweden | -26.3 | way/131339683-400 (ac relation/5528438:b-400, share 0.50 by rating) |
| Sweden | -26.3 | way/131339683-400 (ac relation/5528440:b-400, share 0.50 by rating) |
| Germany | 435.7 | way/142321228-400 (hvdc relation/2505320-400-DC, share 1.00 by rating) |
| internal | 470.2 | way/160792651-400 (hvdc relation/5487095-400-DC, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 145 overhead lines (every one), 72 cables kept static; per line in ambient_ratings.json
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 56 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 8 lumped GSUs (1669 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; thermal 2/8 units. Offline units in the case: 6 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Avedore at Avedorevaerket Koblingsstation 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (3 passes of a Newton solve without reactive limits): 4 reactors 910 MVAr, 4 capacitors 230 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 8 buses, 230 MVAr capacitors and 910 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Avedore takes the balance (losses and the losses-allowance error); synthetic
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
- 110-150 kV class from OSM only (no impedances published): standard conductor per km; ONE estimated EHV/HV coupling (2 x 250 MVA) per EHV substation and HV class rule), so real transformer counts and HV substations near an EHV site that OSM does not join by a line are missing.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by NUTS 3 population (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- OpenStreetMap: names of the substations behind the PyPSA buses; 100-170 kV lines and substations (Overpass API, 2026-11-01) (OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31) (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- Energi Data Service: production, consumption and exchange per price area (DK1, DK2), 5-minute (snapshot hour) (Energinet), Energi Data Service terms (free reuse with source attribution)
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- GISCO NUTS 2024 regions ((c) EuroGeographics) and Natural Earth (public domain): geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf denmark-dk2-spine-400-220-132-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.5 s)
Power flow - Danish DK2 (Zealand, Nordic synchronous area) 400/220/150/132 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (153 buses)
  converged in 8 iteration(s), mismatch 3.00E-012 pu   losses 31.735 MW / -957.575 MVAr
  voltage range 1.0106 - 1.0326 pu
  lowest voltages:
      bus 115    1.0106 pu    -10.495 deg
      bus 102    1.0114 pu    -10.377 deg
      bus 150    1.0114 pu    -10.377 deg
      bus 62     1.0114 pu    -10.378 deg
      bus 63     1.0114 pu    -10.374 deg
      bus 103    1.0115 pu    -10.401 deg
      bus 61     1.0116 pu    -10.395 deg
      bus 135    1.0119 pu    -10.229 deg
      bus 139    1.0119 pu    -10.234 deg
      bus 99     1.0119 pu    -10.221 deg
      bus 132    1.0120 pu    -10.219 deg
      bus 131    1.0122 pu    -10.223 deg
(warm start baked into buses.json from that solve: flat start took 8 Newton iterations)
$ gridsim pf denmark-dk2-spine-400-220-132-r4 (warm start)   (exit 0, 0.4 s)
Power flow - Danish DK2 (Zealand, Nordic synchronous area) 400/220/150/132 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (153 buses)
  converged in 6 iteration(s), mismatch 3.36E-012 pu   losses 31.735 MW / -957.575 MVAr
  voltage range 1.0106 - 1.0326 pu
  lowest voltages:
      bus 115    1.0106 pu    -10.495 deg
      bus 102    1.0114 pu    -10.377 deg
      bus 150    1.0114 pu    -10.377 deg
      bus 62     1.0114 pu    -10.378 deg
      bus 63     1.0114 pu    -10.374 deg
      bus 103    1.0115 pu    -10.401 deg
      bus 61     1.0116 pu    -10.395 deg
      bus 135    1.0119 pu    -10.229 deg
      bus 139    1.0119 pu    -10.234 deg
      bus 99     1.0119 pu    -10.221 deg
      bus 132    1.0120 pu    -10.219 deg
      bus 131    1.0122 pu    -10.223 deg
$ gridsim physics-check denmark-dk2-spine-400-220-132-r4   (exit 0, 0.4 s)
Physics-law audit  -  denmark-dk2-spine-400-220-132-r4  (153 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.15E-010 | MW | independent dissipation 31.734571 MW (branch 31.7346 + shunt -0.0000) vs reported loss 31.734571 MW |
| 2 | Ohm's law | Holds | 9.16E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.16E-010 | MW | total network loss 31.734571 MW vs reported 31.734571 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.17E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.87E-010 | MVA | same residual as law 6, reactive component included at 141 PQ bus(es), by the bus types the solve ended with; 4 of them declared PV and solved as PQ (4 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## Inference round denmark-dk2-spine-400-220-132-r6 (base denmark-dk2-spine-400-220-132-r4, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 0 (0 circuits / units, 0 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), with no new overload, no existing overload made worse by more than 1 point, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 7 sites, 200 MVAr capacitive / 890 MVAr inductive, replacing the generic repair (8 shunts, 230 / 910 MVAr).
- Taps: 2 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- Units at a reactive limit: base round 4; held because generic repair shunts on generator terminal buses were moved to their public substation: 1 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 8 | 9 |
| iterations_warm | 6 | 8 |
| loss_mw | 31.735 | 31.692 |
| vmin_pu | 1.011 | 1.008 |
| vmax_pu | 1.033 | 1.035 |
| angle_spread_deg | 10.150 | 10.117 |
| over_100 | 1 | 1 |
| over_120 | 1 | 1 |
| over_140 | 0 | 0 |
| auto_cap_mvar | 230.000 | 0 |
| auto_reactor_mvar | 910.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 1090.000 |
| units_held_at_q_limit | 4 | 5 |
| cpf_lambda | 1.607 | 1.602 |
| physics_pass | True | True |

Worst after: 137.1 % hv:way/727496028 (Avedorevaerket Koblingsstation 132kV - Amager koblingsstation 132kV); 69.8 % hv:way/134265138+1 (132kV Radsted 132kV - OSM way/516107851 132kV); 67.4 % gsu:way/301369285-400 (OSM way/301369285 400kV gen bus - OSM way/301369285 400kV)

Inferred feeds:

- none

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: -430 MVAr at Avedorevaerket Koblingsstation 400kV
- inferred compensation 2: -310 MVAr at KFA 220kV
- inferred compensation 3: +170 MVAr at Amagervaerkets Koblingsstation 132kV
- inferred compensation 4: -110 MVAr at 400kV Asnaesvaerket 400kV
- inferred compensation 5: -40 MVAr at 132 kV Vestlolland 132kV
- inferred compensation 6: +20 MVAr at 132kV Torslunde 132kV
- inferred compensation 7: +10 MVAr at 132/50 kV Naestved 132kV
