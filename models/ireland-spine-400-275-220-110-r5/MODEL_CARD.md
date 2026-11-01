# MODEL CARD: Irish all-island (Ireland + Northern Ireland) 400/275/220/110 kV grid winter peak 2026-01-05 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Irish all-island (Ireland + Northern Ireland) 400/275/220/110 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-05T18:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over ie; local time WET (UTC+0)).
- Buses 513 (1 boundary points), branches 728 (lines 649, transformers 79), generators 582.
- Buses by kV: 400 kV 4, 275 kV 10, 220 kV 51, 110 kV 415, 20 kV 33.
- Dispatch 7079.5 MW (plant in this system) + boundary imports 1043.0 MW; demand 8000.7 MW (incl. boundary exports 0.0 MW).
- Slack: 1 reference: Kilroot.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 513 | 343 (66.9%) | 0 (0.0%) | 137 (26.7%) | 33 (6.4%) |
| Branches | 728 | 0 (0.0%) | 71 (9.8%) | 657 (90.2%) | 0 (0.0%) |
| Generators | 582 | 327 (56.2%) | 0 (0.0%) | 255 (43.8%) | 0 (0.0%) |
| Demand points | 297 | 0 (0.0%) | 0 (0.0%) | 297 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 50 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 50 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of IE, GB: 65 AC buses, 84 internal lines (146 underground / submarine in the model, given cable parameters), 5 transformers; 343 buses named from OSM.
- Systems: {'main': 480}; components 1 [480].
- Boundary points (cut ties, HVDC terminals, manual points): United Kingdom hvdc x2.
- 110-150 kV class layer: {'osm_line_ways': 1945, 'interior_vertex_splits': 787, 'ways_without_hv_class': 0, 'segments': 2732, 'routes': 2496, 'routes_kept': 565, 'stub_routes_pruned': 35, 'ends_snapped_within_km': 0.5, 'ends_snapped': 34, 'hv_buses': 415, 'hv_buses_by_kv': {'110': 415}, 'tee_junctions': 114, 'couplings': 41, 'max_couplings_at_one_hv_bus': 1, 'uncoupled_components_left_out': {'buses': 2, 'routes': 1, 'km': 0.1}, 'uncoupled_components': [{'buses': 2, 'km': 0.1, 'names': ['Meenbog 110 kV Substation', '_________ 110 kV Substation'], 'nearest_ehv_km': 55.42, 'nearest_pair': 'osmhv:way/871784938-110 -> way/402783212-275', 'nearest_kept_hv_km': 1.34, 'nearest_kept_pair': 'osmhv:way/871784938-110 -> osmhv:tee:54.73455,-7.93769-110'}], 'gap_bridges': [], 'route_km_kept': 5938.4}.
- Snapshot balance (energy-charts): generation by type 7079.5 MW, net import 1043.0 MW, pumping 0.0 MW -> demand 8122.5 MW (the source's own load series: 5847.2 MW).
- Plants left out (islands, outside the boxes): {'rows': 2486, 'mw': 115562.349335, 'by_fuel': {'battery': 7143.01, 'biomass': 6312.95, 'gas': 34878.0, 'geothermal': 2.0, 'hydro': 1601.9, 'nuclear': 9974.0, 'oil': 556.8, 'pumped_storage': 3160.0, 'solar': 13533.497835, 'wind_offshore': 22742.4, 'wind_onshore': 15657.7915}}.
- Country IE: demand 5847.2 MW, generation targets 4804.2 MW, net import (all neighbours) 1043.0 MW, external flows United Kingdom 1043.0; source: energy-charts; balance_rule: demand = energy-charts Load 5847.2 MW; gap 1584.6 MW added to gas (ENTSO-E per-type generation for Ireland incomplete; Load series kept as the demand [VERIFY])
- Country GB: demand 2275.2 MW, generation targets 2275.2 MW, net import (all neighbours) 0.0 MW, external flows none; source: missing-country rule (population x covered demand per head; covered load factors); rule detail {"population": 1908828.662741154, "covered_population": 4905581.456675784, "covered_demand_mw": 5847.25, "load_factors": {"hydro": 0.5030769230769231, "coal": 0.5411111111111112, "pumped_storage": 0.700513698630137, "gas": 0.6093778397043678, "wind_onshore": 0.19468772280810037, "oil": 0.2538179062718583, "other": 0.0}}
- GeoNames population in the modelled system by country: {'GB': 1908828.662741154, 'IE': 4905581.456675784}; places on unconnected islands left out: 0 (0 people).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 1040.5 | 0.0 |
| biomass | 139.2 | 15.8 |
| coal | 135.0 | 73.1 |
| gas | 6909.1 | 4972.0 |
| hydro | 260.0 | 130.8 |
| interconnector | 1043.0 | 1043.0 |
| oil | 1775.6 | 495.4 |
| other | 29.4 | 28.0 |
| pumped_storage | 292.0 | 204.6 |
| solar | 1750.0 | 0.0 |
| wind_onshore | 5958.2 | 1160.0 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| United Kingdom | 1043.0 | way/254158424-400 (hvdc relation/8184641-200-DC, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal line ratings: 503 overhead lines x 1.1034, 146 cables static (seasonal factor 1.1034 = JAO ratio winter 1.1034 / base 'summer' 1.0000 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- RfG thresholds used: type B 0.1 MW, type C 5 MW (EirGrid / SONI 'Proposal for RfG Banding Thresholds - Final Position' (Ireland and Northern Ireland: B 0.1 MW, C 5 MW, D 10 MW), equal to the Table 1 limits); synchronous units below type B at unity pf
- RfG Art. 5 voltage control: 188 converter units at or above type C (5 MW) are pv with +/- 0.33 MVAr per MW; smaller converters below at unity pf; idle converters never control voltage; embedded aggregates at unity pf
- converter plant (PV, wind, batteries) at fixed unity power factor, no voltage control: 28 units pq at Q = 0 (batch 3 rule; estimated, [VERIFY] grid-code reactive mode)
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 71 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 33 lumped GSUs (10575 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value;. Offline units in the case: 20 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Kilroot at Kilroot 275kV Substation 275kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (5 passes of a Newton solve without reactive limits): 4 reactors 90 MVAr, 46 capacitors 1300 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 50 buses, 1300 MVAr capacitors and 90 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Kilroot takes the balance (losses and the losses-allowance error); synthetic
- No demand is moved: the India radial-chain relief is not used in this batch.

Assumed (typical values or documented rules, not fitted; tagged estimated with [VERIFY]):

- converter plant (PV, wind, batteries) at fixed unity power factor (pq, Q = 0); only synchronous units regulate voltage [VERIFY]
- losses allowance 1.5 % of the balance demand (the slack takes the rest)
- EHV transformers 2 x 400 MVA, x 12 %; EHV/HV couplings 2 x 250 MVA, x 12 % (one per EHV site and HV class); X/R 40
- HV lines single ACSR about 585 mm2: R 0.060, X 0.400 ohm/km, C 9 nF/km, 870 A; cables X 0.12-0.13 ohm/km, C 0.20-0.25 uF/km
- GSU x 14.5 % own rating, X/R 40; generator Q range -0.30 to +0.62 x MW; converter +/-0.33 x MW; load power factor 0.97
- unit commitment largest first to 0.8 loading (nuclear 0.95); listed fleet short -> embedded remainder by population
- plants >= 250 MW on the top EHV class; above one HV circuit (870 A, 0.85 pf) on EHV; < 100 MW on HV
- boundary flows split over a neighbour's tie points by tie rating

## Round history

- r1: first build (build-first batch).
- r2: converter voltage control by RfG Art. 5 Table 1 (Ireland and Northern Ireland: type C from 5 MW controls voltage, smaller converters at unity pf, idle converters never); r1 had every converter as pv.
- r2: OSM bus names (Overpass, one query, 2026-11-01).
- r2: 110 kV layer from the Geofabrik ireland-and-northern-ireland extract (Overpass timed out, HTTP 504; the GB part is written empty because the extract covers Northern Ireland): a build step --hv.
- r3: city sections (JAO batch rule): a GeoNames city of 100,000 or more whose PPLX sections within 15 km cover half its population is replaced by them, scaled to the city total (r2: Dublin as one point on one 110 kV bus, Francis Street - Harolds Cross 651.5 %).
- r4: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r4: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r4: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.
- r5: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r5: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r5: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.
- r5: EHV transformer sizes from OSM power=transformer elements: units within 0.6 km of the PyPSA site whose voltage:primary / secondary match its classes, rating tags summed (untagged = 400 MVA typical). Woodland 400/220 kV: 3 OSM units (EirGrid, 400000/220000) -> 1,200 MVA (was the 2 x 400 MVA rule; r4 loading 230.5 %); Moneypoint 2 x 500 MVA tagged -> 1,000 MVA; Oldstreet 1 unit -> 400 MVA; a 275/220 kV site 1 unit tagged 600 MVA. Dunstown 2 units unchanged. Applied to every site by the same rule.

## Known gaps

- No TSO impedances: EHV line R/X/B come from PyPSA-Eur's standard overhead types (400 / 380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; real conductors differ; cables use typical XLPE values.
- EHV transformers: 2 x 400 MVA, x 12 % at every 400/220 kV site PyPSA marks; real unit counts unknown.
- 110-150 kV class from OSM only (no impedances published): standard conductor per km; ONE estimated EHV/HV coupling (2 x 250 MVA) per EHV substation and HV class rule), so real transformer counts and HV substations near an EHV site that OSM does not join by a line are missing.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by GeoNames population of populated places, per country (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- OpenStreetMap: names of the substations behind the PyPSA buses; 100-170 kV lines and substations (Overpass API, 2026-11-01) (OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31) (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- energy-charts public net generation by type and cross-border physical flows (snapshot hour) (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
- GeoNames per-country dumps: populated places with population and position (demand shares) (GeoNames), CC BY 4.0
- GHSL GHS-POP R2023A epoch 2020, 30 arc-second population grid (demand shares, from the round with pop_grid) (European Commission, Joint Research Centre (Schiavina et al. 2023, doi:10.2905/2FF68A52-5B5B-4A22-8F40-C41DA8332CFE)), CC BY 4.0
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries gbOpen ADM1 (CC BY 4.0) and Natural Earth (public domain): geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf ireland-spine-400-275-220-110-r5   (flat start: vm 1, vaDeg 0; exit 0, 1.5 s)
Power flow - Irish all-island (Ireland + Northern Ireland) 400/275/220/110 kV grid winter peak 2026-01-05 (UnvalidatedAtScale) (513 buses)
  converged in 7 iteration(s), mismatch 5.49E-009 pu   losses 162.826 MW / -987.681 MVAr
  voltage range 0.9520 - 1.0282 pu
  lowest voltages:
      bus 239    0.9520 pu    -18.865 deg
      bus 236    0.9544 pu    -19.590 deg
      bus 238    0.9546 pu    -18.468 deg
      bus 199    0.9570 pu    -20.209 deg
      bus 407    0.9574 pu    -11.899 deg
      bus 187    0.9595 pu    -17.667 deg
      bus 312    0.9606 pu    -18.142 deg
      bus 415    0.9611 pu    -11.609 deg
      bus 359    0.9618 pu    -18.058 deg
      bus 237    0.9626 pu    -16.854 deg
      bus 162    0.9631 pu    -16.830 deg
      bus 403    0.9632 pu    -13.490 deg
(warm start baked into buses.json from that solve: flat start took 7 Newton iterations)
$ gridsim pf ireland-spine-400-275-220-110-r5 (warm start)   (exit 0, 0.5 s)
Power flow - Irish all-island (Ireland + Northern Ireland) 400/275/220/110 kV grid winter peak 2026-01-05 (UnvalidatedAtScale) (513 buses)
  converged in 4 iteration(s), mismatch 5.49E-009 pu   losses 162.826 MW / -987.681 MVAr
  voltage range 0.9520 - 1.0282 pu
  lowest voltages:
      bus 239    0.9520 pu    -18.865 deg
      bus 236    0.9544 pu    -19.590 deg
      bus 238    0.9546 pu    -18.468 deg
      bus 199    0.9570 pu    -20.209 deg
      bus 407    0.9574 pu    -11.899 deg
      bus 187    0.9595 pu    -17.667 deg
      bus 312    0.9606 pu    -18.142 deg
      bus 415    0.9611 pu    -11.609 deg
      bus 359    0.9618 pu    -18.058 deg
      bus 237    0.9626 pu    -16.854 deg
      bus 162    0.9631 pu    -16.830 deg
      bus 403    0.9632 pu    -13.490 deg
$ gridsim physics-check ireland-spine-400-275-220-110-r5   (exit 0, 1.0 s)
Physics-law audit  -  ireland-spine-400-275-220-110-r5  (513 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 7.05E-010 | MW | independent dissipation 162.825698 MW (branch 162.8257 + shunt 0.0000) vs reported loss 162.825698 MW |
| 2 | Ohm's law | Holds | 2.74E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 7.02E-010 | MW | total network loss 162.825698 MW vs reported 162.825698 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 3.09E-011 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 5.09E-008 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 5.49E-007 | MVA | same residual as law 6, reactive component included at 410 PQ bus(es), by the bus types the solve ended with; 21 of them declared PV and solved as PQ (21 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
