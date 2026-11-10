# Greek interconnected system (mainland and AC- or DC-linked islands) 400/150 kV grid winter peak 2026-01-21 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Greek interconnected system (mainland and AC- or DC-linked islands) 400/150 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-21T11:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over gr; local time EET (UTC+2)).
- Buses 450 (6 boundary points), branches 594 (lines 540, transformers 54), generators 2311.
- Buses by kV: 400 kV 40, 150 kV 382, 20 kV 28.
- Dispatch 9996.0 MW (plant in this system) + boundary imports 886.2 MW; demand 10748.3 MW (incl. boundary exports 1436.0 MW).
- Slack: 1 reference: Agios Nikolaos.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 450 | 140 (31.1%) | 0 (0.0%) | 282 (62.7%) | 28 (6.2%) |
| Branches | 594 | 0 (0.0%) | 55 (9.3%) | 539 (90.7%) | 0 (0.0%) |
| Generators | 2311 | 2062 (89.2%) | 0 (0.0%) | 249 (10.8%) | 0 (0.0%) |
| Demand points | 253 | 0 (0.0%) | 0 (0.0%) | 253 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 32 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 32 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of GR: 40 AC buses, 55 internal lines (17 underground / submarine in the model, given cable parameters), 0 transformers; 140 buses named from OSM.
- Systems: {'main': 422}; components 1 [422].
- Boundary points (cut ties, HVDC terminals, manual points): Albania ac x1; Bulgaria ac x2; Italy hvdc x1; North Macedonia ac x2; Turkey ac x1.
- 110-150 kV class layer: {'osm_line_ways': 941, 'interior_vertex_splits': 178, 'ways_without_hv_class': 0, 'segments': 1119, 'routes': 1028, 'routes_kept': 485, 'stub_routes_pruned': 63, 'ends_snapped_within_km': 0.5, 'ends_snapped': 40, 'hv_buses': 382, 'hv_buses_by_kv': {'150': 382}, 'tee_junctions': 135, 'couplings': 26, 'max_couplings_at_one_hv_bus': 1, 'uncoupled_components_left_out': {'buses': 29, 'routes': 22, 'km': 306.7}, 'uncoupled_components': [{'buses': 8, 'km': 133.5, 'names': [], 'nearest_ehv_km': 382.29, 'nearest_pair': 'osmhv:way/1373013842-150 -> way/85705637-400', 'nearest_kept_hv_km': 171.2, 'nearest_kept_pair': 'osmhv:way/1373013845-150 -> osmhv:way/255599054-150'}, {'buses': 8, 'km': 88.0, 'names': ['Y/S ILIOLOYSTI', 'Y/S KARYSTOS', 'Y/S LIVADI', 'Y/S MYRTIA', 'Y/S PARADEISI', 'Y/S POLYPOTAMOS'], 'nearest_ehv_km': 19.56, 'nearest_pair': 'osmhv:way/141710434-150 -> way/32357326-400', 'nearest_kept_hv_km': 21.14, 'nearest_kept_pair': 'osmhv:way/865784718-150 -> osmhv:way/86466243-150'}, {'buses': 4, 'km': 41.1, 'names': ['Ypostathmos DEI'], 'nearest_ehv_km': 59.14, 'nearest_pair': 'osmhv:way/93885376-150 -> way/85705637-400', 'nearest_kept_hv_km': 59.14, 'nearest_kept_pair': 'osmhv:way/93885376-150 -> osmhv:way/85705637-150'}, {'buses': 2, 'km': 22.3, 'names': ['Y/S PANORAMA', 'Ypostathmos Kithairona'], 'nearest_ehv_km': 11.53, 'nearest_pair': 'osmhv:way/232346869-150 -> virtual_way/251579391:1-400', 'nearest_kept_hv_km': 11.52, 'nearest_kept_pair': 'osmhv:way/232346869-150 -> osmhv:tee:38.27758,23.32584-150'}, {'buses': 2, 'km': 11.1, 'names': ['Y/S AMYGDALEA', 'Y/S PLATANISTOS'], 'nearest_ehv_km': 50.46, 'nearest_pair': 'osmhv:way/1001396029-150 -> way/85705637-400', 'nearest_kept_hv_km': 47.04, 'nearest_kept_pair': 'osmhv:way/1001396029-150 -> osmhv:way/86466243-150'}, {'buses': 2, 'km': 9.0, 'names': ['Y/S KATOYNA'], 'nearest_ehv_km': 29.82, 'nearest_pair': 'osmhv:way/1001663564-150 -> way/105184051-400', 'nearest_kept_hv_km': 7.78, 'nearest_kept_pair': 'osmhv:way/1001663564-150 -> osmhv:way/249115247-150'}, {'buses': 3, 'km': 1.8, 'names': [], 'nearest_ehv_km': 3.2, 'nearest_pair': 'osmhv:way/92421827-150 -> way/55099563-400', 'nearest_kept_hv_km': 1.96, 'nearest_kept_pair': 'osmhv:way/160692908-150 -> osmhv:way/92421826-150'}], 'gap_bridges': [{'name': 'Crete 150 kV west - central gap (Rethymno - Heraklion side)', 'from': 'osmhv:tee:35.36050,24.54913-150', 'to': 'osmhv:way/1489283728-150', 'km': 35.15}], 'route_km_kept': 7780.3}.
- Snapshot balance (energy-charts): generation by type 9996.0 MW, net import -1067.0 MW, pumping 0.0 MW -> demand 8929.0 MW (the source's own load series: 9025.0 MW).
- Plants left out (islands, outside the boxes): {'rows': 0, 'mw': 0.0, 'by_fuel': {}}.
- Country GR: demand 8929.0 MW, generation targets 9996.0 MW, net import (all neighbours) -1067.0 MW, external flows Albania -152.0, Bulgaria -487.0, Italy 369.0, North Macedonia -761.0, Turkey -36.0; source: energy-charts
- Boundary note: Ariadne HVDC (IPTO / Ariadne Interconnection: 2 x 500 MW, 500 kV DC, Koumoundouros (Attica) - Damasta (Crete), in operation since 2025-05-24 (trial operation); converter positions approximate [VERIFY]): area net deficit 681.3 - 164.1 MW = 517.2 MW, capped at 1000 MW -> 517.2 MW (balancing rule, estimated)
- GeoNames population in the modelled system by country: {'GR': 10303068.709141744}; places on unconnected islands left out: 0 (0 people).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 73.0 | 0.0 |
| biomass | 24.0 | 0.0 |
| coal | 1062.1 | 1009.0 |
| gas | 8239.3 | 4103.0 |
| hydro | 2621.3 | 1992.0 |
| interconnector | 1369.0 | 886.2 |
| oil | 1436.0 | 0.0 |
| pumped_storage | 1379.0 | 311.0 |
| solar | 12096.7 | 528.0 |
| wind_onshore | 6620.0 | 2053.0 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Albania | -152.0 | way/1256844098-400 (ac way/666594586-400, share 1.00 by rating) |
| Bulgaria | -243.5 | virtual_way/1024249021:0-400 (ac merged_way/1024246754-400+2, share 0.50 by rating) |
| Bulgaria | -243.5 | way/55099563-400 (ac merged_way/252077755-400+2, share 0.50 by rating) |
| Italy | 369.0 | way/140248148-400 (hvdc relation/8185664-400-DC, share 1.00 by rating) |
| North Macedonia | -380.5 | way/252077527-400 (ac way/252077524-400, share 0.50 by rating) |
| North Macedonia | -380.5 | way/55099563-400 (ac way/252077525-400, share 0.50 by rating) |
| Turkey | -36.0 | way/141220249-400 (ac Greece-Turkey 400 kV Nea Santa - Babaeski (not in PyPSA-Eur) [VERIFY]; nearest 400 kV bus, 5.6 km, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal line ratings: 523 overhead lines x 1.1034, 17 cables static (seasonal factor 1.1034 = JAO ratio winter 1.1034 / base 'summer' 1.0000 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- RfG thresholds used: type B 1 MW, type C 20 MW (IPTO (ADMIE) 'Integration of the Regulation EU 631-2016 into the Greek Regulatory Framework' (consultation 2020-09), Type B 1 MW <= Pmax < 20 MW, Type C 20 MW <= Pmax < 75 MW, Type D 75 MW or >= 110 kV [VERIFY the RAE approval]); synchronous units below type B at unity pf
- RfG Art. 5 voltage control: 225 converter units at or above type C (20 MW) are pv with +/- 0.33 MVAr per MW; smaller converters below at unity pf; idle converters never control voltage; embedded aggregates at unity pf
- converter plant (PV, wind, batteries) at fixed unity power factor, no voltage control: 1797 units pq at Q = 0 (batch 3 rule; estimated, [VERIFY] grid-code reactive mode)
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 1 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 28 lumped GSUs (13182 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value;. Offline units in the case: 20 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Agios Nikolaos at OSM way/253903008 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (7 passes of a Newton solve without reactive limits): 13 reactors 900 MVAr, 19 capacitors 1340 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 32 buses, 1340 MVAr capacitors and 900 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Agios Nikolaos takes the balance (losses and the losses-allowance error); synthetic
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
- r2: converter voltage control by RfG Art. 5 Table 1 (Continental Europe: type C from 50 MW controls voltage, smaller converters at unity pf, idle converters never). r1 had every converter as pv: its midday snapshot held every bus at 1.02 pu.
- r2: OSM bus names (Overpass, one query, 2026-11-01). EHV only: the first r2 attempt WITH the 150 kV layer (Geofabrik, 292 HV buses) did not solve - a radial OSM 150 kV chain to Chalkidiki sat at 0.7833 pu and -32.6 deg at 0.5 x snapshot (no second infeed in the OSM layer); the layer moves to r3.
- r3: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r3: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r3: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.
- r3: 150 kV layer from the Geofabrik Greece extract (Overpass timed out, HTTP 504): a build step writes the same files a build step osm_hv would; a build step --hv builds the layer (Crete joins if its 150 kV AC link to the Peloponnese is mapped in OSM).
- r3: reactive repair: a step is also accepted when it keeps the voltage extremes no worse (Canada's procedure rule; the first r2 attempt stopped at 0.6 x snapshot because every step was refused while Vmin was below 0.85 pu).
- r3: Crete: the Ariadne HVDC (Attica - Crete, 1,000 MW, in operation since 2025-05-24) is not in PyPSA-Eur; it is an injection pair carrying Crete's net deficit (balancing rule, estimated). The Peloponnese - Crete 150 kV AC cable is in the OSM layer.
- r3: a build step --hv: ways are split at interior vertices that are another way's end (OSM tees at towers; 177 in Greece, the build pipeline bug). The first r3 attempt lost the Stagira - Amfipoli tee into Thessaloniki - Filippoi, so the Chalkidiki 150 kV ring was radial. Routes kept 364 -> 460, HV buses 292 -> 364, km 6,694.2 -> 7,285.0.
- r4: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r4: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r4: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.
- r4: a build step now reads OSM substation RELATIONS (multipolygon yards) with their member-way bounds: Greece has only 4 (the r3 note's suspected cause); they add 2 EHV/150 kV couplings (23 -> 25) and 4 HV buses.
- r4: OSM ways built for 400 kV but OPERATED at 150 kV ('400000 (temp 150000)': KYT Lavrio - KYT Argyroupoli, KYT Argyroupoli - KYT Pallini, IPTO) leave the 400 kV layer (PyPSA-Eur read them as 400 kV) and join the 150 kV layer at their operating voltage (couplings 25 -> 26).
- r4: The uncoupled components left out were diagnosed one by one (topology_summary.json 'uncoupled_components'): they are OSM line gaps, not substation outlines: Crete centre / east (15 buses, 360.1 km; bridged, see below), the Dodecanese (8 buses, 133.5 km: Rhodes / Kos are autonomous island systems, correctly left out), South Evia (8 buses, 88.0 km, 21.1 km from the kept grid), and 5 small pockets (84.3 km).
- r4: Crete 150 kV gap bridge: one 150 kV circuit, straight line, between the west and centre parts of Crete's one 150 kV system, so the Ariadne converter side (Damasta) joins the case.

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
$ gridsim pf greece-spine-400-150-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.5 s)
Power flow - Greek interconnected system (mainland and AC- or DC-linked islands) 400/150 kV grid winter peak 2026-01-21 (UnvalidatedAtScale) (450 buses)
  converged in 8 iteration(s), mismatch 2.16E-011 pu   losses 166.815 MW / -3303.532 MVAr
  voltage range 0.9429 - 1.0450 pu
  lowest voltages:
      bus 347    0.9429 pu     -6.564 deg
      bus 301    0.9497 pu     -0.326 deg
      bus 49     0.9497 pu     -0.323 deg
      bus 207    0.9520 pu    -21.217 deg
      bus 303    0.9530 pu      4.909 deg
      bus 304    0.9535 pu      4.625 deg
      bus 47     0.9538 pu      5.023 deg
      bus 351    0.9540 pu      3.978 deg
      bus 45     0.9540 pu      3.984 deg
      bus 368    0.9550 pu      3.086 deg
      bus 46     0.9555 pu      4.691 deg
      bus 275    0.9565 pu      5.427 deg
(warm start baked into buses.json from that solve: flat start took 8 Newton iterations)
$ gridsim pf greece-spine-400-150-r4 (warm start)   (exit 0, 0.4 s)
Power flow - Greek interconnected system (mainland and AC- or DC-linked islands) 400/150 kV grid winter peak 2026-01-21 (UnvalidatedAtScale) (450 buses)
  converged in 6 iteration(s), mismatch 3.78E-011 pu   losses 166.815 MW / -3303.532 MVAr
  voltage range 0.9429 - 1.0450 pu
  lowest voltages:
      bus 347    0.9429 pu     -6.564 deg
      bus 301    0.9497 pu     -0.326 deg
      bus 49     0.9497 pu     -0.323 deg
      bus 207    0.9520 pu    -21.217 deg
      bus 303    0.9530 pu      4.909 deg
      bus 304    0.9535 pu      4.625 deg
      bus 47     0.9538 pu      5.023 deg
      bus 351    0.9540 pu      3.978 deg
      bus 45     0.9540 pu      3.984 deg
      bus 368    0.9550 pu      3.086 deg
      bus 46     0.9555 pu      4.691 deg
      bus 275    0.9565 pu      5.427 deg
$ gridsim physics-check greece-spine-400-150-r4   (exit 0, 0.4 s)
Physics-law audit  -  greece-spine-400-150-r4  (450 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 6.36E-010 | MW | independent dissipation 166.815174 MW (branch 166.8152 + shunt -0.0000) vs reported loss 166.815174 MW |
| 2 | Ohm's law | Holds | 1.53E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 6.34E-010 | MW | total network loss 166.815174 MW vs reported 166.815174 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 8.51E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 6.90E-009 | MVA | same residual as law 6, reactive component included at 340 PQ bus(es), by the bus types the solve ended with; 9 of them declared PV and solved as PQ (9 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
