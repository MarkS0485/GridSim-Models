# MODEL CARD: Bulgarian 400/220 kV grid winter peak 2026-01-21 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Bulgarian 400/220 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-21T10:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over bg; local time EET (UTC+2)).
- Buses 185 (8 boundary points), branches 272 (lines 227, transformers 45), generators 577.
- Buses by kV: 400 kV 93, 220 kV 60, 20 kV 32.
- Dispatch 6100.2 MW (plant in this system) + boundary imports 1101.0 MW; demand 7093.2 MW (incl. boundary exports 0.0 MW).
- Slack: 1 reference: Maritsa Iztok #2.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 185 | 44 (23.8%) | 0 (0.0%) | 109 (58.9%) | 32 (17.3%) |
| Branches | 272 | 0 (0.0%) | 227 (83.5%) | 45 (16.5%) | 0 (0.0%) |
| Generators | 577 | 417 (72.3%) | 0 (0.0%) | 160 (27.7%) | 0 (0.0%) |
| Demand points | 152 | 0 (0.0%) | 0 (0.0%) | 152 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 10 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 10 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of BG: 153 AC buses, 227 internal lines (0 underground / submarine in the model, given cable parameters), 13 transformers; 44 buses named from OSM.
- Systems: {'main': 153}; components 1 [153].
- Boundary points (cut ties, HVDC terminals, manual points): Greece ac x2; North Macedonia ac x1; Romania ac x3; Serbia ac x1; Turkey ac x1.
- 110-150 kV class layer: not in this round.
- Snapshot balance (energy-charts): generation by type 6100.2 MW, net import 1101.0 MW, pumping 0.0 MW -> demand 7201.2 MW (the source's own load series: 7790.9 MW).
- Plants left out (islands, outside the boxes): {'rows': 0, 'mw': 0.0, 'by_fuel': {}}.
- Country BG: demand 7201.2 MW, generation targets 6100.2 MW, net import (all neighbours) 1101.0 MW, external flows Greece 478.0, North Macedonia 168.0, Romania 118.0, Serbia 109.0, Turkey 228.0; source: energy-charts
- GeoNames population in the modelled system by country: {'BG': 6905806.354725121}; places on unconnected islands left out: 0 (0 people).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 1397.7 | 0.0 |
| biomass | 15.9 | 15.1 |
| coal | 6571.0 | 2441.9 |
| gas | 761.0 | 317.7 |
| hydro | 2038.7 | 608.6 |
| interconnector | 1101.0 | 1101.0 |
| nuclear | 2080.0 | 1814.1 |
| pumped_storage | 864.0 | 0.0 |
| solar | 3921.0 | 812.1 |
| wind_onshore | 608.0 | 90.7 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Greece | 239.0 | way/1287693974-400 (ac merged_way/1024246754-400+2, share 0.50 by rating) |
| Greece | 239.0 | way/235044638-400 (ac merged_way/252077755-400+2, share 0.50 by rating) |
| North Macedonia | 168.0 | way/176656979-400 (ac merged_relation/3517149-400+1, share 1.00 by rating) |
| Romania | 29.5 | virtual_way/261379799:0-400 (ac merged_way/144787755-400+1, share 0.25 by rating) |
| Romania | 59.0 | virtual_way/114515157:1-400 (ac merged_way/192459174-400+1, share 0.50 by rating) |
| Romania | 29.5 | way/200516868-400 (ac merged_way/200521429-400+1, share 0.25 by rating) |
| Serbia | 109.0 | way/37028932-400 (ac merged_way/237583897-400+1, share 1.00 by rating) |
| Turkey | 228.0 | way/253244460-400 (ac Bulgaria-Turkey 400 kV Maritsa East - Hamitabat (not in PyPSA-Eur) [VERIFY]; nearest 400 kV bus, 1.1 km, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal line ratings: 227 overhead lines x 1.1034, 0 cables static (seasonal factor 1.1034 = JAO ratio winter 1.1034 / base 'summer' 1.0000 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- RfG thresholds used: type B 1 MW, type C 50 MW (national values not found (ESO / EWRC): EU Table 1 Continental Europe upper limits 1 / 50 / 75 MW [VERIFY]); synchronous units below type B at unity pf
- RfG Art. 5 voltage control: 20 converter units at or above type C (50 MW) are pv with +/- 0.33 MVAr per MW; smaller converters below at unity pf; idle converters never control voltage; embedded aggregates at unity pf
- converter plant (PV, wind, batteries) at fixed unity power factor, no voltage control: 337 units pq at Q = 0 (batch 3 rule; estimated, [VERIFY] grid-code reactive mode)
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 11 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 32 lumped GSUs (13241 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value;. Offline units in the case: 40 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Maritsa Iztok #2 at OSM way/253597954 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 2 reactors 180 MVAr, 8 capacitors 640 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 10 buses, 640 MVAr capacitors and 180 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Maritsa Iztok #2 takes the balance (losses and the losses-allowance error); synthetic
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
- r2: OSM bus names (Overpass, one query, 2026-11-01; r1 had OSM ids only because Overpass was down). No network, dispatch or demand value changed.
- r3: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r3: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r3: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.

## Known gaps

- No TSO impedances: EHV line R/X/B come from PyPSA-Eur's standard overhead types (400 / 380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; real conductors differ; cables use typical XLPE values.
- EHV transformers: 2 x 400 MVA, x 12 % at every 400/220 kV site PyPSA marks; real unit counts unknown.
- 110-150 kV class not modelled in this round: demand and small plant sit on EHV buses.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by GeoNames population of populated places, per country (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
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
$ gridsim pf bulgaria-spine-400-220-r3   (flat start: vm 1, vaDeg 0; exit 0, 0.4 s)
Power flow - Bulgarian 400/220 kV grid winter peak 2026-01-21 (UnvalidatedAtScale) (185 buses)
  converged in 4 iteration(s), mismatch 1.14E-011 pu   losses 118.701 MW / -1487.073 MVAr
  voltage range 0.9628 - 1.0358 pu
  lowest voltages:
      bus 127    0.9628 pu    -23.068 deg
      bus 177    0.9628 pu    -23.068 deg
      bus 143    0.9639 pu    -22.928 deg
      bus 181    0.9639 pu    -22.928 deg
      bus 115    0.9647 pu    -22.826 deg
      bus 128    0.9726 pu    -20.973 deg
      bus 178    0.9726 pu    -20.973 deg
      bus 123    0.9738 pu    -20.823 deg
      bus 108    0.9792 pu    -20.159 deg
      bus 148    0.9811 pu    -20.391 deg
      bus 116    0.9833 pu    -20.563 deg
      bus 149    0.9850 pu    -20.231 deg
(warm start baked into buses.json from that solve: flat start took 4 Newton iterations)
$ gridsim pf bulgaria-spine-400-220-r3 (warm start)   (exit 0, 0.4 s)
Power flow - Bulgarian 400/220 kV grid winter peak 2026-01-21 (UnvalidatedAtScale) (185 buses)
  converged in 1 iteration(s), mismatch 6.09E-012 pu   losses 118.701 MW / -1487.073 MVAr
  voltage range 0.9628 - 1.0358 pu
  lowest voltages:
      bus 127    0.9628 pu    -23.068 deg
      bus 177    0.9628 pu    -23.068 deg
      bus 143    0.9639 pu    -22.928 deg
      bus 181    0.9639 pu    -22.928 deg
      bus 115    0.9647 pu    -22.826 deg
      bus 128    0.9726 pu    -20.973 deg
      bus 178    0.9726 pu    -20.973 deg
      bus 123    0.9738 pu    -20.823 deg
      bus 108    0.9792 pu    -20.159 deg
      bus 148    0.9811 pu    -20.391 deg
      bus 116    0.9833 pu    -20.563 deg
      bus 149    0.9850 pu    -20.231 deg
$ gridsim physics-check bulgaria-spine-400-220-r3   (exit 0, 0.4 s)
Physics-law audit  -  bulgaria-spine-400-220-r3  (185 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.10E-011 | MW | independent dissipation 118.701243 MW (branch 118.7012 + shunt -0.0000) vs reported loss 118.701243 MW |
| 2 | Ohm's law | Holds | 9.17E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.10E-011 | MW | total network loss 118.701243 MW vs reported 118.701243 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.32E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 7.67E-010 | MVA | same residual as law 6, reactive component included at 163 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
