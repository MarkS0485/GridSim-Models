# MODEL CARD: Poland transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Poland study results. A solvable rough map of the Poland 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, PSE) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r5 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 23982.0 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 375 (10 cross-border boundary buses, 135 generator / embedded buses), branches 610 (lines 435, transformers 175), generators 2965.
- Buses by kV: 400 kV 113, 220 kV 127, 110 kV 116, 21 kV 19.
- Dispatch 22445.6 MW (Poland plant) + boundary imports 2900.0 MW; demand 24864.8 MW (incl. boundary exports 1307.0 MW and storage charging).
- Slack: 1 reference: Belchatow Phase.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 375 | 0 (0.0%) | 0 (0.0%) | 230 (61.3%) | 145 (38.7%) |
| Branches | 610 | 262 (43.0%) | 2 (0.3%) | 346 (56.7%) | 0 (0.0%) |
| Generators | 2965 | 0 (0.0%) | 0 (0.0%) | 2965 (100.0%) | 0 (0.0%) |
| Demand points | 122 | 0 (0.0%) | 0 (0.0%) | 122 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 25 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 25 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, PSE: 222 internal line rows (by class {'220': 135, 'hv': 87}), 15 tie-line rows used, 26 JAO transformers placed.
- Positions: {'osm_whole_word': 146, 'jao_map': 4, 'pypsa_osm': 80, 'neighbour_mean': 0, 'boundary': 10} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 196 circuits, 89 OSM-only stations, 23 chain duplicates of JAO lines skipped; per km (HV) R 0.0281 ohm, X 0.3199 ohm, B 3.594 uS, Imax 2000 A (medians of 87 JAO lines); 220 kV R 0.0564, X 0.4151, B 2.770, Imax 848 A.
- Synthetic couplings (median JAO unit {'mva': 500.0, 'x_pct_own': 12.04, 'x_over_r': 91.5, 'how': 'median of 26 JAO Poland 400(380)/220 kV units'}): ['bydgoszcz zachod', 'grudziadz', 'jasiniec', 'kromolice', 'morzyczyn', 'olsztyn matki', 'osm virtual_way/146491141:1', 'ostrowiec', 'pelplin', 'pila krzewina', 'plewiska', 'skawina', 'zydowo kierzkowo']; near-site ['joachimow / t joa-lag (0.23 km)'].
- JAO transformers not modelled: ['PST GRUDZIADZ-A3: phase shifter 400/220 kV, not modelled', 'PST JOACHIMOW-TD1: phase shifter 220/220 kV, not modelled', 'PST JOACHIMOW-TD2: phase shifter 220/220 kV, not modelled', 'PST MIKULOWA-PF1: phase shifter 400/400 kV, not modelled', 'PST MIKULOWA-PF2: phase shifter 400/400 kV, not modelled', 'PST MIKULOWA-PF3: phase shifter 400/400 kV, not modelled', 'PSTMIKULOWA-PF4: phase shifter 400/400 kV, not modelled', 'PST MIKULOWA-TD1: phase shifter 220/220 kV, not modelled', 'PST MIKULOWA-TD2: phase shifter 220/220 kV, not modelled', 'TR OLSZTYN-MATK-A3: no station with both voltage classes named in it', 'TR RZESZOW-A3: no station with both voltage classes named in it', 'TR RZESZOW-A4: no station with both voltage classes named in it'].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [240]).
- Shape check (crow-fly vs published length): 4 outliers [{'line': 'BIERUN-KOMOROWICE', 'crow_km': 26.2, 'len_km': 84.5}, {'line': 'MORY-PRAGA', 'crow_km': 11.8, 'len_km': 32.0}, {'line': 'HALEMBA-T HAL-BYC', 'crow_km': 0.2, 'len_km': 20.4}, {'line': 'T HAL-BYC-BYCZYNA', 'crow_km': 32.3, 'len_km': 16.6}].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 235.8 | 0.0 |
| biomass | 703.0 | 379.2 |
| coal | 16809.5 | 8220.8 |
| gas | 5074.0 | 3496.2 |
| hydro_ps | 1875.0 | 641.1 |
| hydro_res | 165.5 | 139.5 |
| hydro_ror | 222.4 | 139.1 |
| interconnector | 2900.0 | 2900.0 |
| lignite | 6949.0 | 4851.8 |
| oil | 277.4 | 221.9 |
| other | 899.4 | 719.5 |
| solar | 9324.5 | 0.0 |
| waste | 16.0 | 0.0 |
| wind_onshore | 9470.5 | 3636.5 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| CZ | -253.7 | PL:detmarovice [CZ]:hv (AC boundary bus, share 0.389 of the CZ border by tie rating) |
| CZ | -145.8 | PL:liskowiec [CZ]:220 (AC boundary bus, share 0.224 of the CZ border by tie rating) |
| CZ | -252.5 | PL:nosovice [CZ]:hv (AC boundary bus, share 0.387 of the CZ border by tie rating) |
| DE | 1104.5 | PL:vierraden [DE]:hv (AC boundary bus, share 0.500 of the DE border by tie rating) |
| DE | 1104.5 | PL:hagenwerder [DE]:hv (AC boundary bus, share 0.500 of the DE border by tie rating) |
| LT | 137.0 | PL:alytus [LT]:hv (AC boundary bus, share 1.000 of the LT border by tie rating) |
| SK | -439.0 | PL:lemesany [SK]:hv (AC boundary bus, share 1.000 of the SK border by tie rating) |
| SE | 554.0 | PL:starno [SE]:hv (AC boundary bus, share 1.000 of the SE border by tie rating) |
| UA | -162.9 | PL:khmelnytskyi [UA]:hv (AC boundary bus, share 0.754 of the UA border by tie rating) |
| UA | -53.1 | PL:dobrotwor [UA]:220 (AC boundary bus, share 0.246 of the UA border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 19 lumped GSUs (29552 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 116 embedded buses behind lumped supply equivalents (26726 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.2 MW, type C 10 MW, type D 75 MW; PSE 'Progi mocowe jednostek wytworczych' (PSE presentation 2017-11-30; table reproduced in DSO connection information) [VERIFY the URE approval decision]): 44 synchronous units (2509.9 MW) of type B+ and 232 running converter units (9470.5 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 2391 smaller units (9560.3 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 7/35 units (5534 MW offline); lignite 2/3 units (474 MW offline); gas 11/23 units (612 MW offline); oil 116/116 units (0 MW offline); biomass 4/8 units (185 MW offline); waste 0/1 units (16 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): oil register 0.0 MW vs energy-charts 221.9 MW; 277.4 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 0.0 MW vs energy-charts 719.5 MW; 899.4 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Belchatow Phase at Rogowiec 400kV gen bus, reactive band +/-31765 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (3 passes of a Newton solve without reactive limits): 20 reactors 585 MVAr, 5 capacitors 90 MVAr (synthetic; JAO publishes no reactive compensation): Khmelnytskyi [UA] 400kV -115, Alytus [LT] 400kV -50, Elk Bis 400kV -40, Czarna 400kV embedded bus -40, Lomza Systemowa 400kV -30, Narew 400kV embedded bus -30, Elk Bis 400kV embedded bus -30, Osm Virtual_Way/166838340:0 400kV -20, Osm Virtual_Way/1447360698:1 400kV -20, Osm Virtual_Way/1447360690:1 400kV -20, Osm Virtual_Way/1447360686:1 400kV -20, Osm Virtual_Way/1447360682:0 400kV -20, Osm Virtual_Way/1447360670:1 400kV -20, Olsztyn-Matki 400kV -20, Osm Virtual_Way/1446962835:1 400kV -20, Osm Virtual_Way/1446962824:1 400kV -20, Osm Virtual_Way/1446962823:1 400kV -20, Osm Virtual_Way/845649424:1 400kV -20, Ostroleka 400kV -20, Mikulowa 220kV embedded bus -10, Nysa 220kV embedded bus +10, Boguchwala 220kV embedded bus +10, Klikowa 220kV embedded bus +10, Groszowice 220kV embedded bus +20, Zamosc 220kV embedded bus +40

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: first build (build-first batch); reactive repair by fixed bus shunts only.
- r5: Kozienice (r4: 400/220 kV AT-2 139.7 %): the powerplantmatching row of units 1-10 (2,919 MW) sat on the 400 kV bus. OSM maps 8 generator transformers at 220 kV and 3 at 400 kV in the Kozienice station (Overpass 2026-11-01, the source record): the row is split into 1,120 MW at 400 kV (units 9, 10 at 560 MW [VERIFY]) and 1,799 MW at 220 kV (units 1-8); unit 11 (1,075 MW, its own row) stays at 400 kV. Placement only; the JAO transformer (one 500 MVA unit, as OSM's AT-2) is unchanged. Repair: weak-bus cap.

## Known gaps

- JAO lists only the elements relevant to flow-based capacity calculation; missing corridors were added from PyPSA-Eur OSM with median JAO per-km parameters (estimated), and some stations may still be missing.
- No reactive compensation from JAO; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per station and voltage class. Phase shifters are not modelled.
- Neighbouring grids are fixed boundary injections (energy-charts physical flows at the snapshot): no foreign network and no fault infeed from abroad.
- Generator fleet from powerplantmatching (merged registers): duplicates and retired capacity are possible; where the register is short of the snapshot output a register-gap aggregate is added (listed in the repairs).
- Demand is allocated by population only (no industrial load map).
- Snapshot: one common Core-region quarter-hour (2025-11-19 16:30 UTC) for the whole batch, not this country's own peak; an hourly energy-charts series uses the 16:00-17:00 UTC hour.
- IEC 60909 fault sweep not run in round 1 (build-first); refinement runs it.

## Sources

- Core Static Grid Model, 9th release (2026-03): PSE lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (PSE for Poland)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Poland (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Poland units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Poland 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Poland, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries POL ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf poland-spine-400-220-r5   (flat start: vm 1, vaDeg 0; exit 0, 1.0 s)
Power flow - Poland transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (375 buses)
  converged in 8 iteration(s), mismatch 3.66E-012 pu   losses 388.013 MW / -2631.012 MVAr
  voltage range 0.9564 - 1.0467 pu
  lowest voltages:
      bus 119    0.9564 pu    -38.179 deg
      bus 365    0.9586 pu    -18.681 deg
      bus 232    0.9590 pu    -24.882 deg
      bus 366    0.9590 pu    -24.882 deg
      bus 159    0.9677 pu    -23.306 deg
      bus 321    0.9689 pu    -20.695 deg
      bus 128    0.9774 pu    -35.480 deg
      bus 146    0.9785 pu    -25.577 deg
      bus 171    0.9785 pu    -25.578 deg
      bus 187    0.9786 pu    -25.579 deg
      bus 162    0.9790 pu    -31.934 deg
      bus 207    0.9791 pu    -24.247 deg
(warm start baked into buses.json: flat start took 8 Newton iterations)
(the build pipeline reading of the pf result) angle spread 49.097 deg; branches over 100 %: 4, over 80 %: 13; highest: jao:19T000000003959P:23 (Wielopole 400kV - Wielopole 220kV) 109.7 %; jao:19T110000006627A:21 (Rogowiec 400kV - Rogowiec 220kV) 106.8 %; jao:19T110000006626C:20 (Rogowiec 400kV - Rogowiec 220kV) 103.8 %; jao:SWIEBODZICE-ZABKOWICE:138 (Swiebodzice 220kV - Zabkowice 220kV) 100.5 %; synth:coupling:plewiska~plewiska (Plewiska 400kV - Plewiska 220kV) 99.2 %
$ gridsim pf poland-spine-400-220-r5 (warm start)   (exit 0, 0.5 s)
Power flow - Poland transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (375 buses)
  converged in 5 iteration(s), mismatch 1.87E-012 pu   losses 388.013 MW / -2631.012 MVAr
  voltage range 0.9564 - 1.0467 pu
  lowest voltages:
      bus 119    0.9564 pu    -38.179 deg
      bus 365    0.9586 pu    -18.681 deg
      bus 232    0.9590 pu    -24.882 deg
      bus 366    0.9590 pu    -24.882 deg
      bus 159    0.9677 pu    -23.306 deg
      bus 321    0.9689 pu    -20.695 deg
      bus 128    0.9774 pu    -35.480 deg
      bus 146    0.9785 pu    -25.577 deg
      bus 171    0.9785 pu    -25.578 deg
      bus 187    0.9786 pu    -25.579 deg
      bus 162    0.9790 pu    -31.934 deg
      bus 207    0.9791 pu    -24.247 deg
$ gridsim physics-check poland-spine-400-220-r5   (exit 0, 0.6 s)
Physics-law audit  -  poland-spine-400-220-r5  (375 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.81E-011 | MW | independent dissipation 388.013333 MW (branch 388.0133 + shunt -0.0000) vs reported loss 388.013333 MW |
| 2 | Ohm's law | Holds | 7.54E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 3.18E-011 | MW | total network loss 388.013333 MW vs reported 388.013333 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.57E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 5.35E-010 | MVA | same residual as law 6, reactive component included at 292 PQ bus(es), by the bus types the solve ended with; 6 of them declared PV and solved as PQ (6 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
