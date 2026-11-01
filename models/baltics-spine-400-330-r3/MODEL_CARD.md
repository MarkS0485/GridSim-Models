# MODEL CARD: Baltic states (Estonia, Latvia, Lithuania; Continental Europe synchronous area since 9 February 2025) 400/330/220 kV grid winter peak 2026-01-30 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Baltic states (Estonia, Latvia, Lithuania; Continental Europe synchronous area since 9 February 2025) 400/330/220 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-30T08:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over ee, lv, lt; local time EET (UTC+2)).
- Buses 87 (4 boundary points), branches 109 (lines 89, transformers 20), generators 542.
- Buses by kV: 400 kV 1, 330 kV 66, 220 kV 2, 20 kV 18.
- Dispatch 4639.1 MW (plant in this system) + boundary imports 881.2 MW; demand 5439.7 MW (incl. boundary exports 146.8 MW).
- Slack: 1 reference: Riga #2.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 87 | 54 (62.1%) | 0 (0.0%) | 15 (17.2%) | 18 (20.7%) |
| Branches | 109 | 0 (0.0%) | 85 (78.0%) | 24 (22.0%) | 0 (0.0%) |
| Generators | 542 | 411 (75.8%) | 0 (0.0%) | 131 (24.2%) | 0 (0.0%) |
| Demand points | 69 | 0 (0.0%) | 0 (0.0%) | 69 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 23 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 23 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of EE, LV, LT: 69 AC buses, 89 internal lines (4 underground / submarine in the model, given cable parameters), 2 transformers; 54 buses named from OSM.
- Systems: {'main': 69}; components 1 [69].
- Boundary points (cut ties, HVDC terminals, manual points): Finland hvdc x2; Poland ac x1; Sweden hvdc x1.
- 110-150 kV class layer: not in this round.
- Snapshot balance (energy-charts): generation by type 4639.1 MW, net import 734.5 MW, pumping 0.0 MW -> demand 5373.6 MW (the source's own load series: 5393.3 MW).
- Plants left out (islands, outside the boxes): {'rows': 0, 'mw': 0.0, 'by_fuel': {}}.
- Country EE: demand 1528.6 MW, generation targets 972.3 MW, net import (all neighbours) 556.3 MW, external flows Finland -146.8; source: energy-charts
- Country LV: demand 1289.5 MW, generation targets 1450.0 MW, net import (all neighbours) -160.5 MW, external flows none; source: energy-charts
- Country LT: demand 2555.5 MW, generation targets 2216.7 MW, net import (all neighbours) 338.8 MW, external flows Poland 149.2, Sweden 732.0; source: energy-charts
- GeoNames population in the modelled system by country: {'EE': 1316867.6431335649, 'LT': 2818075.8408455863, 'LV': 1892575.2783178897}; places on unconnected islands left out: 0 (0 people).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 472.7 | 0.0 |
| biomass | 297.8 | 250.9 |
| gas | 2442.0 | 1420.8 |
| hydro | 1637.8 | 533.5 |
| interconnector | 881.2 | 881.2 |
| oil | 692.3 | 670.3 |
| other | 114.1 | 108.4 |
| pumped_storage | 900.0 | 0.0 |
| solar | 3096.5 | 273.6 |
| wind_onshore | 3638.8 | 1381.6 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Finland | -95.4 | relation/18986190-330 (hvdc relation/6886400-450-DC, share 0.65 by rating) |
| Finland | -51.4 | way/34968224-330 (hvdc relation/8184630-150-DC, share 0.35 by rating) |
| Poland | 149.2 | way/256339597-400 (ac merged_way/352126763-400+1, share 1.00 by rating) |
| Sweden | 732.0 | way/90098783-330 (hvdc relation/8185455-300-DC, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal line ratings: 85 overhead lines x 1.1034, 4 cables static (seasonal factor 1.1034 = JAO ratio winter 1.1034 / base 'summer' 1.0000 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- RfG thresholds used: type B 0.5 MW, type C 10 MW (national values not found (Elering, AST, Litgrid): RfG Table 1 Baltic synchronous-area upper limits 0.5 / 10 / 15 MW, under which the thresholds were set in 2018 (the states joined Continental Europe on 2025-02-09) [VERIFY]); synchronous units below type B at unity pf
- RfG Art. 5 voltage control: 103 converter units at or above type C (10 MW) are pv with +/- 0.33 MVAr per MW; smaller converters below at unity pf; idle converters never control voltage; embedded aggregates at unity pf
- converter plant (PV, wind, batteries) at fixed unity power factor, no voltage control: 279 units pq at Q = 0 (batch 3 rule; estimated, [VERIFY] grid-code reactive mode)
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 8 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 18 lumped GSUs (6444 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value;. Offline units in the case: 5 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Riga #2 at Rigas TEC-2 330kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (3 passes of a Newton solve without reactive limits): 17 reactors 750 MVAr, 6 capacitors 370 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 23 buses, 370 MVAr capacitors and 750 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Riga #2 takes the balance (losses and the losses-allowance error); synthetic
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
$ gridsim pf baltics-spine-400-330-r3   (flat start: vm 1, vaDeg 0; exit 0, 0.4 s)
Power flow - Baltic states (Estonia, Latvia, Lithuania; Continental Europe synchronous area since 9 February 2025) 400/330/220 kV grid winter peak 2026-01-30 (UnvalidatedAtScale) (87 buses)
  converged in 8 iteration(s), mismatch 2.07E-012 pu   losses 50.144 MW / -1730.654 MVAr
  voltage range 1.0188 - 1.0258 pu
  lowest voltages:
      bus 69     1.0188 pu    -16.671 deg
      bus 30     1.0194 pu     -5.024 deg
      bus 63     1.0195 pu     -4.956 deg
      bus 18     1.0196 pu     -5.248 deg
      bus 10     1.0197 pu     -5.235 deg
      bus 39     1.0198 pu    -16.325 deg
      bus 51     1.0199 pu    -10.819 deg
      bus 17     1.0200 pu      1.825 deg
      bus 15     1.0200 pu    -16.207 deg
      bus 1      1.0200 pu     -4.802 deg
      bus 2      1.0200 pu     -9.261 deg
      bus 3      1.0200 pu     -4.898 deg
(warm start baked into buses.json from that solve: flat start took 8 Newton iterations)
$ gridsim pf baltics-spine-400-330-r3 (warm start)   (exit 0, 0.4 s)
Power flow - Baltic states (Estonia, Latvia, Lithuania; Continental Europe synchronous area since 9 February 2025) 400/330/220 kV grid winter peak 2026-01-30 (UnvalidatedAtScale) (87 buses)
  converged in 6 iteration(s), mismatch 1.94E-012 pu   losses 50.144 MW / -1730.654 MVAr
  voltage range 1.0188 - 1.0258 pu
  lowest voltages:
      bus 69     1.0188 pu    -16.671 deg
      bus 30     1.0194 pu     -5.024 deg
      bus 63     1.0195 pu     -4.956 deg
      bus 18     1.0196 pu     -5.248 deg
      bus 10     1.0197 pu     -5.235 deg
      bus 39     1.0198 pu    -16.325 deg
      bus 51     1.0199 pu    -10.819 deg
      bus 17     1.0200 pu      1.825 deg
      bus 15     1.0200 pu    -16.207 deg
      bus 1      1.0200 pu     -4.802 deg
      bus 2      1.0200 pu     -9.261 deg
      bus 3      1.0200 pu     -4.898 deg
$ gridsim physics-check baltics-spine-400-330-r3   (exit 0, 0.4 s)
Physics-law audit  -  baltics-spine-400-330-r3  (87 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.42E-011 | MW | independent dissipation 50.144467 MW (branch 50.1445 + shunt 0.0000) vs reported loss 50.144467 MW |
| 2 | Ohm's law | Holds | 5.77E-012 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 4.50E-011 | MW | total network loss 50.144467 MW vs reported 50.144467 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 6.44E-011 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.03E-010 | MVA | same residual as law 6, reactive component included at 33 PQ bus(es), by the bus types the solve ended with; 7 of them declared PV and solved as PQ (7 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
