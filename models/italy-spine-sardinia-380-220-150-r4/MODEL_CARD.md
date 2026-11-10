# Italy Sardinian 380/220 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official Italian study results. A solvable rough map of the Sardinian 380/220 kV transmission grid (DC-linked to the mainland by SAPEI and SACOI) for one summer peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur), register-based generation (powerplantmatching), Terna's published peak, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Round: r1. System: sardinia.
- Snapshot: 2026-06-29 12:00-13:00 UTC (14:00-15:00 CEST), Terna June 2026 peak; Terna national demand 57434 MW.
- Buses 168 (2 boundary points on Italian buses), branches 219 (lines 190, transformers 29), generators 104.
- Buses by kV: 380 kV 8, 220 kV 10, 150 kV 133, 20 kV 17.
- Dispatch 1429.1 MW (plant in this system) + boundary imports 77.4 MW; demand 1506.6 MW (incl. boundary exports 0.0 MW).
- Slack: 1 reference: Fiume Santo.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 168 | 125 (74.4%) | 0 (0.0%) | 26 (15.5%) | 17 (10.1%) |
| Branches | 219 | 0 (0.0%) | 23 (10.5%) | 196 (89.5%) | 0 (0.0%) |
| Generators | 104 | 72 (69.2%) | 0 (0.0%) | 32 (30.8%) | 0 (0.0%) |
| Demand points | 15 | 0 (0.0%) | 0 (0.0%) | 15 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 10 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 10 (100.0%) |

Buses are 'attested' when OSM names the substation; lines 'derived' (OSM length x PyPSA standard type), cables 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, Italian rows: 590 AC buses, 802 internal lines (214 underground / submarine, given cable parameters), 66 transformers; 3328 buses named from OSM.
- Systems: {'mainland': 4625, 'sardinia': 151} (mainland includes Sicily through the Messina 380 kV link); islands 2 [4625, 151].
- Boundary points (cut ties and HVDC terminals): Austria ac x2; France ac x4; France hvdc x3; Greece hvdc x1; Italy hvdc x2; Malta ac x1; Montenegro hvdc x1; Slovenia ac x2; Switzerland ac x8.
- HV layer (150/132 kV): {'osm_line_ways': 11615, 'ways_without_hv_class': 0, 'segments': 11615, 'routes': 10779, 'routes_kept': 5211, 'stub_routes_pruned': 379, 'ends_snapped_within_km': 0.5, 'ends_snapped': 264, 'hv_buses': 4186, 'hv_buses_by_kv': {'132': 2668, '150': 1518}, 'tee_junctions': 1022, 'couplings': 400, 'uncoupled_components_left_out': {'buses': 119, 'routes': 92, 'km': 341.0}, 'route_km_kept': 39228.1}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 593.0 | 0.0 |
| biomass | 25.5 | 24.2 |
| coal | 1230.0 | 362.5 |
| gas | 636.0 | 0.0 |
| hydro_lake | 194.6 | 0.0 |
| hydro_ror | 20.0 | 7.2 |
| interconnector | 77.4 | 77.4 |
| oil | 457.0 | 0.0 |
| pumped_storage | 240.0 | 0.0 |
| solar | 1582.0 | 786.4 |
| wind_onshore | 1216.0 | 248.8 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| SAPEI (to mainland) | 59.6 | way/409439916-380 (hvdc relation/8185711-500-DC: Sardinian net export share) |
| SACOI (to mainland) | 17.9 | way/1156702013-380 (hvdc relation/3391794-200-DC: Sardinian net export share) |

## Repairs (every change made so the case solves)

- synchronous plant moved behind 17 lumped GSUs (3295 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 covers the fuel's snapshot value; gas 23/109 units; coal 1/2 units; oil 1/11 units; biomass 16/16 units; hydro_lake 2/142 units. Offline units in the case: 15 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Fiume Santo at Fiumesanto Carbo 380 380kV gen bus, reactive band +/-20000 MVAr (synthetic)
- reactive repair staged by load scaling: shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage from the previous stage's shunts (estimated)
- bus shunts placed where the snapshot needs reactive support (20 passes of a Newton solve without reactive limits): 3 reactors 90 MVAr, 7 capacitors 280 MVAr (synthetic; no open source lists Terna's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Known gaps

- No TSO impedances: line R/X/B come from PyPSA-Eur's two standard overhead types (380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; Terna's real conductors (e.g. 3 x 585 mm2 at 380 kV) differ; cables use typical XLPE values. Terna publishes no grid model; the JAO Core SGM holds only foreign TSOs' halves of the AT / SI / FR ties (no Terna rows), and no Italy North static grid model is published.
- Transformers: 2 x 400 MVA, x 12 % at every 380/220 kV site OSM marks; real unit counts unknown.
- 150/132 kV from OSM only (no impedances published): standard conductor per km, couplings estimated.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (energy-charts cbpf per border, split by tie rating): no foreign network and no fault infeed from abroad. SAPEI / SACOI carry Sardinia's estimated net balance.
- Demand by province population (no Terna regional load map at the peak hour); embedded PV by population, though Italian PV is skewed to the south and to Lombardy / Veneto / Emilia [VERIFY].
- Unit commitment by size, not Terna's real schedule (MSD / MGP not used).

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): Italian buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- OpenStreetMap: names of the substations behind the PyPSA buses; 120-160 kV lines and substations (Overpass API, 2026-10-31) (OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31), Italian rows (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- energy-charts public net generation by type and cross-border physical flows, Italy, 2026-06-29 12:00-13:00 UTC (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
- Rapporto Mensile sul Sistema Elettrico, Giugno 2026: peak 57,434 MW on 29 June 2026 14:00-15:00, thermal 23,907 MW at the peak (Terna S.p.A.), Terna publication, facts reused with attribution
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- openpolis geojson-italy regions (ISTAT), CC BY 4.0, and Natural Earth (public domain): geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf italy-spine-sardinia-380-220-150-r1   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Italy Sardinian 380/220 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale) (168 buses)
  converged in 9 iteration(s), mismatch 7.42E-012 pu   losses 11.210 MW / -546.145 MVAr
  voltage range 1.0077 - 1.0281 pu
  lowest voltages:
      bus 95     1.0077 pu    -10.236 deg
      bus 100    1.0102 pu    -10.412 deg
      bus 166    1.0102 pu    -10.412 deg
      bus 51     1.0102 pu     -9.668 deg
      bus 94     1.0106 pu    -10.070 deg
      bus 128    1.0106 pu    -10.492 deg
      bus 143    1.0109 pu    -10.463 deg
      bus 92     1.0119 pu     -9.936 deg
      bus 50     1.0126 pu     -9.703 deg
      bus 25     1.0135 pu     -9.051 deg
      bus 63     1.0160 pu     -9.492 deg
      bus 60     1.0186 pu     -9.594 deg
(warm start baked into buses.json from that solve: flat start took 9 Newton iterations)
$ gridsim pf italy-spine-sardinia-380-220-150-r1 (warm start)   (exit 0, 0.6 s)
Power flow - Italy Sardinian 380/220 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale) (168 buses)
  converged in 6 iteration(s), mismatch 7.42E-012 pu   losses 11.210 MW / -546.145 MVAr
  voltage range 1.0077 - 1.0281 pu
  lowest voltages:
      bus 95     1.0077 pu    -10.236 deg
      bus 100    1.0102 pu    -10.412 deg
      bus 166    1.0102 pu    -10.412 deg
      bus 51     1.0102 pu     -9.668 deg
      bus 94     1.0106 pu    -10.070 deg
      bus 128    1.0106 pu    -10.492 deg
      bus 143    1.0109 pu    -10.463 deg
      bus 92     1.0119 pu     -9.936 deg
      bus 50     1.0126 pu     -9.703 deg
      bus 25     1.0135 pu     -9.051 deg
      bus 63     1.0160 pu     -9.492 deg
      bus 60     1.0186 pu     -9.594 deg
$ gridsim physics-check italy-spine-sardinia-380-220-150-r1   (exit 0, 0.6 s)
Physics-law audit  -  italy-spine-sardinia-380-220-150-r1  (168 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.50E-009 | MW | independent dissipation 11.210401 MW (branch 11.2104 + shunt -0.0000) vs reported loss 11.210401 MW |
| 2 | Ohm's law | Holds | 4.59E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.50E-009 | MW | total network loss 11.210401 MW vs reported 11.210401 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 1.06E-011 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.50E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.33E-009 | MVA | same residual as law 6, reactive component included at 130 PQ bus(es), by the bus types the solve ended with; 5 of them declared PV and solved as PQ (5 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## Inference round italy-spine-sardinia-380-220-150-r4 (base italy-spine-sardinia-380-220-150-r1, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 0 (0 circuits / units, 0 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), with no new overload, no existing overload made worse by more than 1 point, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 7 sites, 220 MVAr capacitive / 80 MVAr inductive, replacing the generic repair (10 shunts, 280 / 90 MVAr).
- Taps: 7 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- Units at a reactive limit: base round 5; held because generic repair shunts on generator terminal buses were moved to their public substation: 2 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 9 | 8 |
| iterations_warm | 6 | 6 |
| loss_mw | 11.210 | 11.265 |
| vmin_pu | 1.008 | 1.008 |
| vmax_pu | 1.028 | 1.031 |
| angle_spread_deg | 8.148 | 8.155 |
| over_100 | 1 | 1 |
| over_120 | 0 | 0 |
| over_140 | 0 | 0 |
| auto_cap_mvar | 280.000 | 0 |
| auto_reactor_mvar | 90.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 300.000 |
| units_held_at_q_limit | 5 | 5 |
| cpf_lambda | 1.723 | 1.699 |
| physics_pass | True | True |

Worst after: 104.8 % hv:way/136762728 (Tula 150kV - Codrongianos 150kV); 80.8 % gsu:osmhv:way/303915533-150 (Rumianca 150kV gen bus - Rumianca 150kV); 50.4 % gsu:way/409439916-380 (Fiumesanto Carbo 380 380kV gen bus - Fiumesanto Carbo 380 380kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 104.8 % hv:way/136762728 (Tula 150kV - Codrongianos 150kV)

Inferred feeds:

- none

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: +140 MVAr at Tula 150kV
- inferred compensation 2: -40 MVAr at Codrongianos 150kV
- inferred compensation 3: -40 MVAr at Fiumesanto Carbone 150kV
- inferred compensation 4: +30 MVAr at Nuoro 2 150kV
- inferred compensation 5: +20 MVAr at Sottostazione Villasor FS 150kV
- inferred compensation 6: +20 MVAr at Quartu Sant'Elena 150kV
- inferred compensation 7: +10 MVAr at Nurri 150kV
