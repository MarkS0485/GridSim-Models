# MODEL CARD: Swiss 380/220/150/132/110 kV transmission grid winter peak 2026-01-06 (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Swiss 380/220/150/132/110 kV transmission grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-06T15:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over ch; local time CET (UTC+1)).
- Buses 737 (22 boundary points), branches 1038 (lines 788, transformers 250), generators 1070.
- Buses by kV: 380 kV 44, 220 kV 141, 150 kV 34, 132 kV 163, 110 kV 213, 20 kV 142.
- Dispatch 11981.4 MW (plant in this system) + boundary imports 3391.5 MW; demand 15216.4 MW (incl. boundary exports 5411.5 MW).
- Slack: 1 reference: Leibstadt.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 737 | 246 (33.4%) | 0 (0.0%) | 349 (47.4%) | 142 (19.3%) |
| Branches | 1038 | 0 (0.0%) | 219 (21.1%) | 813 (78.3%) | 6 (0.6%) |
| Generators | 1070 | 618 (57.8%) | 222 (20.7%) | 230 (21.5%) | 0 (0.0%) |
| Demand points | 238 | 0 (0.0%) | 0 (0.0%) | 238 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 96 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 96 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of CH: 185 AC buses, 224 internal lines (68 underground / submarine in the model, given cable parameters), 33 transformers; 246 buses named from OSM.
- Systems: {'main': 595}; components 1 [595].
- Boundary points (cut ties, HVDC terminals, manual points): Austria ac x2; France ac x9; Germany ac x10; Italy ac x8.
- 110-150 kV class layer: {'osm_line_ways': 3526, 'ways_not_grid_frequency': {'frequency 16.7': 538}, 'traction_substations_dropped': 65, 'coupling_units_osm': [], 'ways_without_hv_class': 1776, 'segments': 2107, 't_junction_splits': 357, 'routes': 1731, 'routes_kept': 564, 'stub_routes_pruned': 189, 'ends_snapped_within_km': 0.5, 'ends_snapped': 87, 'foreign_hv_buses_dropped': 0, 'ends_snapped_to_tagged_substation': 43, 'tagged_snap_km': 2.0, 'tagged_snap_examples': ['way/166389287  (1.93 km, 132 kV)', 'way/431346670 Unterwerk Bassersdorf (1.25 km, 110 kV)', 'node/6564909212 Unterwerk Jona (0.69 km, 110 kV)', 'way/197059163  (0.70 km, 110 kV)', 'way/147557677 Umspannwerk Wangen (1.04 km, 132 kV)', 'way/147557677 Umspannwerk Wangen (1.79 km, 132 kV)', 'way/31318082 EKZ-EWH Unterwerk (0.86 km, 110 kV)', 'way/31318082 EKZ-EWH Unterwerk (0.90 km, 110 kV)'], 'pypsa_virtual_ehv_buses_sited': 7, 'virtual_site_examples': ['virtual_relation/11762422:b:1-400 -> way/111162936 Poste electrique de Romanel-sur-Lausanne (0.00 km)', 'virtual_relation/5318397:a:0-400 -> way/177392130 Poste electrique de Verbois (0.00 km)', 'virtual_relation/5552942:1-225 -> way/55698557 St-Triphon (0.00 km)', 'virtual_relation/5610122:1-220 -> way/281815404 Magadino (1.56 km)', 'virtual_way/194683262:1-220 -> way/44496892 Banlieue Ouest (1.89 km)', 'virtual_way/81247299:b:1-220 -> way/239937062 Foretaille (1.77 km)', 'virtual_way/93377768:1-220 -> way/89977424 Unterwerk Spreitenbach (1.99 km)'], 'hv_buses': 410, 'hv_buses_by_kv': {'110': 213, '132': 163, '150': 34}, 'tee_junctions': 214, 'couplings': 75, 'max_couplings_at_one_hv_bus': 3, 'uncoupled_components_left_out': {'buses': 23, 'routes': 25, 'km': 29.4}, 'route_km_kept': 1809.3}.
- Snapshot balance (energy-charts+swissgrid): generation by type 11981.4 MW, net import -2020.1 MW, pumping 0.0 MW -> demand 9954.2 MW (the source's own load series: 10801.6 MW).
- Plants left out (islands, outside the boxes): {'rows': 1, 'mw': 28.0, 'by_fuel': {'biomass': 28.0}}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 73.5 | 0.0 |
| biomass | 271.5 | 0.0 |
| gas | 55.0 | 0.0 |
| hydro | 13824.1 | 5993.7 |
| interconnector | 3391.5 | 3391.5 |
| nuclear | 3095.0 | 1956.5 |
| other | 2005.1 | 1904.9 |
| pumped_storage | 4274.6 | 2066.2 |
| solar | 96.7 | 44.3 |
| wind_onshore | 55.0 | 15.8 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Austria | -367.3 | way/455120191-220 (ac merged_way/105623757-220+2, share 0.22 by rating) |
| Austria | -1269.0 | relation/7933294-380 (ac relation/3948320:a-380, share 0.78 by rating) |
| Germany | -229.7 | way/50319857-380 (ac merged_relation/3916226:c-380+3, share 0.09 by rating) |
| Germany | -66.5 | way/98648381-220 (ac merged_way/195538144-220+4, share 0.02 by rating) |
| Germany | -229.7 | way/98648381-380 (ac merged_way/195538144-380+6, share 0.09 by rating) |
| Germany | -66.5 | way/50319857-220 (ac merged_way/26660205-220+4, share 0.02 by rating) |
| Germany | -133.0 | way/50319857-220 (ac merged_way/27854188-220+1, share 0.05 by rating) |
| Germany | -133.0 | way/50319857-220 (ac merged_way/50306784-220+1, share 0.05 by rating) |
| Germany | -459.4 | way/50319857-380 (ac merged_way/50306784-380+1, share 0.17 by rating) |
| Germany | -459.4 | way/50319857-380 (ac merged_way/62332171-380+3, share 0.17 by rating) |
| Germany | -229.7 | way/397960460-380 (ac relation/3916522:a-380, share 0.09 by rating) |
| Germany | -689.2 | way/50319857-380 (ac way/104906905-380, share 0.26 by rating) |
| France | -169.9 | virtual_relation/11762422:b:1-400 (ac merged_relation/11762422:a-400+1, share 0.16 by rating) |
| France | -169.9 | virtual_relation/5318397:a:0-400 (ac merged_relation/5318397:b-400+1, share 0.16 by rating) |
| France | -46.7 | way/803903329-220 (ac relation/12643745-220, share 0.04 by rating) |
| France | -169.9 | virtual_relation/3717716:b:1-400 (ac relation/3717716:b-400, share 0.16 by rating) |
| France | -161.4 | way/127004407-380 (ac relation/3989161-380, share 0.15 by rating) |
| France | -47.8 | virtual_relation/5552942:1-225 (ac relation/5552942-225, share 0.04 by rating) |
| France | -47.8 | virtual_relation/5552944:1-225 (ac relation/5552944-225, share 0.04 by rating) |
| France | -169.9 | virtual_relation/6668144:1-400 (ac relation/6668144-400, share 0.16 by rating) |
| France | -95.6 | virtual_way/176700313:0-225 (ac way/176700313-225, share 0.09 by rating) |
| Italy | 550.8 | virtual_relation/5609696:d:1-380 (ac merged_relation/5609696:a-380+3, share 0.16 by rating) |
| Italy | 159.4 | way/391576135-220 (ac merged_way/332890452-220+3, share 0.05 by rating) |
| Italy | 550.8 | way/281804158-380 (ac merged_way/339184905-380+1, share 0.16 by rating) |
| Italy | 1101.5 | way/207991759-380 (ac relation/2798852-380, share 0.32 by rating) |
| Italy | 159.4 | way/802058337-220 (ac relation/5552941-220, share 0.05 by rating) |
| Italy | 159.4 | way/802058337-220 (ac relation/5552945-220, share 0.05 by rating) |
| Italy | 550.8 | way/207991759-380 (ac relation/5563323-380, share 0.16 by rating) |
| Italy | 159.4 | virtual_way/104450944:1-220 (ac way/104450944-220, share 0.05 by rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 720 overhead lines (every one), 68 cables kept static; per line in ambient_ratings.json
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 6 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- RfG rule (Regulation (EU) 2016/631 Art. 5, CE limits: type B 1 MW, type C 50 MW): 247 running units (264.3 MW) below their voltage-control threshold set pq at unity power factor (documented rule; national thresholds [VERIFY])
- synchronous plant moved behind 142 lumped GSUs (24255 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; nuclear 2/4 units; hydro 28/523 units; pumped_storage 3/18 units. Offline units in the case: 527 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Leibstadt at Leibstadt 380kV gen bus, reactive band +/-20000 MVAr (synthetic)
- production not in the ENTSO-E by-type series: 1417.4 MW at 222 buses ('other', embedded pq), = Swissgrid control-block production minus energy-charts production by type (derived); placed by Swissgrid's per-canton production (estimated); fuel unknown [VERIFY]
- reactive repair staged by load scaling: shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage from the previous stage's shunts (estimated)
- bus shunts placed where the snapshot needs reactive support (25 passes of a Newton solve without reactive limits): 0 reactors 0 MVAr, 92 capacitors 1300 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 96 buses, 1300 MVAr capacitors and 0 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Leibstadt takes the balance (losses and the losses-allowance error); synthetic
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
- energy-charts public net generation by type and cross-border physical flows (snapshot hour) (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
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
$ gridsim pf switzerland-spine-380-220-hv-r6   (flat start: vm 1, vaDeg 0; exit 0, 0.6 s)
Power flow - Swiss 380/220/150/132/110 kV transmission grid winter peak 2026-01-06 (UnvalidatedAtScale) (737 buses)
  converged in 5 iteration(s), mismatch 1.12E-010 pu   losses 340.441 MW / -68.831 MVAr
  voltage range 0.9512 - 1.0267 pu
  lowest voltages:
      bus 515    0.9512 pu    -11.775 deg
      bus 719    0.9512 pu    -11.775 deg
      bus 225    0.9512 pu    -10.884 deg
      bus 386    0.9513 pu    -11.761 deg
      bus 371    0.9515 pu    -10.449 deg
      bus 699    0.9515 pu    -10.449 deg
      bus 281    0.9516 pu    -11.119 deg
      bus 312    0.9516 pu    -11.260 deg
      bus 278    0.9518 pu    -10.317 deg
      bus 345    0.9518 pu    -10.297 deg
      bus 589    0.9518 pu    -12.488 deg
      bus 279    0.9518 pu    -10.290 deg
(warm start baked into buses.json from that solve: flat start took 5 Newton iterations)
$ gridsim pf switzerland-spine-380-220-hv-r6 (warm start)   (exit 0, 0.5 s)
Power flow - Swiss 380/220/150/132/110 kV transmission grid winter peak 2026-01-06 (UnvalidatedAtScale) (737 buses)
  converged in 1 iteration(s), mismatch 1.73E-010 pu   losses 340.441 MW / -68.831 MVAr
  voltage range 0.9512 - 1.0267 pu
  lowest voltages:
      bus 515    0.9512 pu    -11.775 deg
      bus 719    0.9512 pu    -11.775 deg
      bus 225    0.9512 pu    -10.884 deg
      bus 386    0.9513 pu    -11.761 deg
      bus 371    0.9515 pu    -10.449 deg
      bus 699    0.9515 pu    -10.449 deg
      bus 281    0.9516 pu    -11.119 deg
      bus 312    0.9516 pu    -11.260 deg
      bus 278    0.9518 pu    -10.317 deg
      bus 345    0.9518 pu    -10.297 deg
      bus 589    0.9518 pu    -12.488 deg
      bus 279    0.9518 pu    -10.290 deg
$ gridsim physics-check switzerland-spine-380-220-hv-r6   (exit 0, 0.5 s)
Physics-law audit  -  switzerland-spine-380-220-hv-r6  (737 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.08E-009 | MW | independent dissipation 340.440618 MW (branch 340.4406 + shunt 0.0000) vs reported loss 340.440618 MW |
| 2 | Ohm's law | Holds | 2.74E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 4.08E-009 | MW | total network loss 340.440618 MW vs reported 340.440618 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 3.15E-011 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 4.49E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 7.50E-009 | MVA | same residual as law 6, reactive component included at 708 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
