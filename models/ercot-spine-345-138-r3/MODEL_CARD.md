# MODEL CARD: ERCOT transmission 345/138 kV 2025 peak hour 2025-08-18 17:00 CDT (UnvalidatedAtScale, r3)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against ERCOT study results (which are CEII and were not used). A solvable rough map of the ERCOT (Texas Interconnection, 60 Hz) 345/138 kV transmission grid for one snapshot: OpenStreetMap topology, estimated conductor parameters, EIA-860M fleet dispatched to the EIA-930 fuel mix of the 2025 peak hour, EIA-930 weather-zone demand allocated by county population. Use it to learn, compare and explore, not to plan or operate.

Round: r3. Frequency: 60 Hz.

## What it is

- Snapshot: 08/18/2025 10:00:00 PM UTC (08/18/2025 5:00:00 PM CDT, hour ending).
- Buses 5771 (246 generator terminal buses), branches 7835 (lines 7390, transformers 445), generators 1052.
- Buses by kV: 345 kV 874, 138 kV 4651, 22 kV 246.
- Dispatch 83794.0 MW (ERCOT plant) + DC-tie imports 1.0 MW; demand 80806.4 MW (incl. DC-tie exports 35.0 MW and battery charging 223.0 MW).
- Slack: 1 reference: South Texas Project [nuclear].

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 5771 | 0 (0.0%) | 0 (0.0%) | 5525 (95.7%) | 246 (4.3%) |
| Branches | 7835 | 0 (0.0%) | 0 (0.0%) | 7798 (99.5%) | 37 (0.5%) |
| Generators | 1052 | 0 (0.0%) | 0 (0.0%) | 1052 (100.0%) | 0 (0.0%) |
| Demand points | 403 | 0 (0.0%) | 0 (0.0%) | 229 (56.8%) | 174 (43.2%) |
| Shunts (repairs) | 156 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 156 (100.0%) |

Generator rows are 'estimated' because their BUS and dispatch are inferred; their capacity and position are EIA-860M's (attested, evidence_detail). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OSM Texas extract (Geofabrik texas-261030), built into buses and circuits by the shared adapter a build step; kept layers 345 / 138 kV; ERCOT island 5525 buses (345 kV 874, 138 kV 4651; 1677 tee points), 7390 line branches, 199 345/138 kV transformer sites; route km 345 kV 17981.9, 138 kV 36451.9; circuit km 345 kV 21851.1, 138 kV 38789.8.
- DC-tie converter sites removed as AC buses (OSM joins ERCOT to SPP through them): sw165665526_345, sw165669465_345, sw512936551_138.
- Neighbouring-grid groups cut out (>= 5 connected buses whose EIA-860M BA vote is not ERCO): 132 buses {'MISO': 132} near 30.496, -94.284; 93 buses {'SWPP': 93} near 32.793, -94.559; 17 buses {'SWPP': 17} near 35.915, -101.757; 11 buses {'SWPP': 11} near 33.634, -101.899; 8 buses {'MISO': 8} near 29.81, -94.215; 29 boundary lines cut ([VERIFY]: normally-open points or OSM errors).
- Footprint check (majority BA of the 5 nearest EIA-860M plants): kept island votes {'ERCO': 5515, 'SWPP': 5, 'MISO': 5}; other islands 29 buses (20 with an ERCO vote) not modelled.
- Per-km parameters (derived from catalogue conductor data, [VERIFY]): 345 kV Twin Rail 954 kcmil 45/7 ACSR: R 0.0364, X 0.3713 ohm/km, B 4.361 uS/km, 1183 MVA; 138 kV Drake 795 kcmil 26/7 ACSR: R 0.0864, X 0.4647 ohm/km, B 3.523 uS/km, 217 MVA.
- Generator placement snap distance: median 1.52 km, 90th percentile 10.8 km, max 118.45 km.
- ERCOT counties (EIA-860M BA vote ERCO) 211 of 254; left out: Bailey, Bowie, Cass, Cochran, Crosby, Dallam, El Paso, Gaines, Gregg, Hale, Hansford, Hardin, Harrison, Hartley, Hemphill, Hockley, Hudspeth, Hutchinson, Jasper, Jefferson, Lamb, Lipscomb, Lubbock, Marion, Moore, Morris, Newton, Ochiltree, Orange, Parmer, Polk, Potter, Randall, Roberts, Sabine, San Augustine, San Jacinto, Sherman, Terry, Tyler, Upshur, Wheeler, Yoakum.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch | EIA-930 at the snapshot hour |
|---|---:|---:|---:|
| battery | 18999.6 | 0.0 | -223 |
| biomass | 137.0 | 52.0 | other: 52 |
| coal | 13378.9 | 10000.0 | 10000 |
| gas | 68448.1 | 36506.0 | 36506 |
| hydro | 555.1 | 1.0 | 1 |
| nuclear | 5138.6 | 4951.0 | 4951 |
| oil | 822.1 | 0.0 | 0 |
| other | 237.4 | 0.0 | other: 52 |
| solar | 33778.3 | 20204.0 | 20204 |
| wind | 40552.3 | 12080.0 | 12080 |

## Demand by weather zone (MW)

| Zone | EIA-930 | In case |
|---|---:|---:|
| COAS | 22315.0 | 22224.8 |
| EAST | 2805.0 | 2793.7 |
| FWES | 6731.0 | 6703.8 |
| NCEN | 26879.0 | 26770.4 |
| NRTH | 2190.0 | 2181.1 |
| SCEN | 14455.0 | 14396.6 |
| SOUT | 6398.0 | 6372.1 |
| WEST | 2104.0 | 2095.5 |

## DC ties (MW, + export from ERCOT)

| Tie | Neighbour | Rating (recalled, [VERIFY]) | Flow | ERCOT-side bus |
|---|---|---:|---:|---|
| East DC tie | SWPP | 600 | +25.6 | OSM site Monticello (171859709) |
| North DC tie | SWPP | 220 | +9.4 | OSM site Oklaunion South (165665543) |
| Railroad DC tie | CEN | 300 | -1.0 | nearest 138 kV bus to the OSM converter site (2.37 km) |
| Laredo VFT | CEN | 100 | +0.0 | OSM site Laredo VFT North Yard (426016267) |
| Eagle Pass DC tie | CEN | 36 | +0.0 | OSM site Eagle Pass (21108292) |

## Values adjusted to fit the solve (synthetic; NO-FITTING rule)

Each item below was chosen because an earlier build did not solve, without a cited source; the elements it touches are tagged synthetic in provenance and evidence_tags.json.

- Demand aggregated to the 138 kV bus of the nearest 345/138 kV coupling station (3178 demand rows moved; GSP-style convention, chosen because the spread allocation over every 138 kV bus had no AC solution): moved demand rows are synthetic.
- Autotransformer units raised to the demand each station serves (served MVA / (0.7 x 600 MVA), at least 2): 37 sites, units 398 -> 468: those transformers are synthetic.
- All gas plants committed and dispatched pro rata (instead of largest-first commitment), spreading gas output over the state incl. the Houston industrial CHP; argued from the peak hour but chosen after a failed solve.
- Plants of 100-500 MW placed at a 345 kV bus when one lies within 15 km (placement rule changed after a failed solve).

## Repairs (every change made so the case solves)

- seasonal line ratings: all 7390 overhead lines x 0.9439 (seasonal factor 0.9439 = JAO ratio summer 1.0000 / base 'interseason' 1.0594 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- committed synchronous plant moved behind 246 lumped GSUs (92421 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: per synchronous fuel, EIA-860M plants committed largest first until committed net summer capacity x 0.85 covers the EIA-930 figure; coal 7/10 plants (749 MW offline); gas 279/279 plants (0 MW offline); nuclear 2/2 plants (0 MW offline); other 1/17 plants (258 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed); wind / solar at one capacity factor each: hydro 0.0018, solar 0.5981, wind 0.2979
- converter voltage control by ERCOT Nodal Protocols 3.15 (VSS): wind / solar plants over 20 MVA at >= 10 % of nameplate pv with +/- 0.3287 MVAr per MW of nameplate; other converters and batteries pq at Q = 0
- converter plant outside the VSS rule (wind / solar at or below 20 MVA or under 10 % output, all batteries) runs at Q = 0 (pq)
- slack: largest dispatched synchronous plant South Texas Project [nuclear] at South Texas Project Switchyard 345 kV gen bus, reactive band +/-15933 MVAr (synthetic)
- loss accounting: EIA-930 demand includes transmission losses; demand rows 83538.0 MW scaled by 0.964213 (L = 2989.597 MW, the previous round's gridsim pf loss; estimated)
- reactive repair stopped early at some stage(s): pass 16: no damped step solves; 20 buses still outside
- bus shunts placed where the snapshot needs reactive support (16 passes of a Newton solve without reactive limits): 8 reactors 110 MVAr, 148 capacitors 25385 MVAr (synthetic; no open ERCOT reactive-compensation list); largest: Tri-Corner Substation 345 kV +2025, West Denton Substation 345 kV +1735, Gilleland Creek Substation 345 kV +1535, Substation 1162878332 345 kV +1110, Gibbons Creek Station 345 kV +1035, Substation 1462376316 345 kV +720, Substation 15318503 345 kV +680, Substation 43705092 345 kV +680, Substation 43705092 345 kV gen bus +580, Substation 1337292650 345 kV +560, Channelview Cogen Substation 345 kV gen bus +480, Substation 1428418588 138 kV +410, Bendix Substation 345 kV +400, Substation 1490408596 138 kV +390, Substation 686972909 345 kV +380, Paris Substation 345 kV +340, Substation 1524785493 138 kV +320, Substation 1302777336 138 kV +310, Substation 1560226726 345 kV +310, Rio Hondo Substation 345 kV +290, Substation 1105404314 345 kV +285, Cagnon Road Substation 345 kV +270, Webberville Solar Substation 138 kV (sw462642773_138) +260, Substation 1463496816 345 kV +260, Corn Trail Switching Station 345 kV +260

## Round history (the solver's findings that drove each round)

- r1: first build from OSM + EIA-860M + EIA-930; reactive repair by fixed bus shunts only.
- r2: r1 showed 156 overloads, 36.5 GVAr synthetic capacitors, Plano 0.867 pu and the slack (South Texas Project) carrying the whole 2,989.597 MW of losses. Changes: (1) demand rows scaled by (D - L) / D with L = the r1 transmission loss, because EIA-930 demand already contains the losses; (2) converter plant at fixed power factor (pq, Q 0), only synchronous units regulate voltage; (3) India's radial-chain demand relief removed, fitting); (4) fault levels sampled by kV with gridsim iec60909 --bus (the all-bus sweep timed out).
- r2 attempts without (5) stopped at 0.80 x snapshot (no folder written. (5) converter voltage control by the cited ERCOT rule (Nodal Protocols 3.15 VSS): wind / solar plants over 20 MVA at >= 10 % of nameplate are pv (+/- 0.95 pf of nameplate), all other converters and every battery at fixed pf; r1 made EVERY converter pv, idle ones included. (6) reactive repair _place = the copy from the JAO batch.
- r3: SEASONAL RATINGS (owner rule 2026-11-01): every overhead line's ASTM 25 C-ambient rating x 0.9439 (= JAO median summer / interseason ratio, the build rules) for the August snapshot; derived, [VERIFY]. No other change.

## Known gaps

- No 69 kV network: demand stands for everything below 138 kV; 138 kV fragments joined to the grid only through 69 kV are not modelled.
- Line parameters are one typical design per voltage (345 kV twin Rail, 138 kV single Drake); real ERCOT lines include bundled 1590 kcmil and ACSS CREZ circuits with much higher ratings, and older 138 kV lines with lower ones.
- Transformer impedances and sizes are typical (2 x 600 MVA, 8 %); no open ERCOT transformer list.
- No series compensation (the CREZ 345 kV lines in west Texas carry series capacitors), no SVC / STATCOM, no switched shunts: the bus shunts are fixed repairs.
- Wind and solar dispatched at one capacity factor each over the whole state; the snapshot hour's real west / south split is not used.
- Weather zones are approximated from county-to-anchor distances; ERCOT's own county list is not used.
- Fleet is EIA-860M September 2026 while the snapshot hour is 2025-08-18: newer plants run in the 2025 hour.
- DC-tie ratings are recalled, not read from an ERCOT document ([VERIFY]).
- No CEII used: impedances, ratings and topology are NOT ERCOT's planning-case values.

## Sources

- OpenStreetMap power layer, Geofabrik Texas extract texas-261030 (2026-10-30): 345 / 138 kV lines, substations, DC-tie converter sites (OpenStreetMap contributors (via Geofabrik GmbH)), ODbL 1.0
- EIA-860M Preliminary Monthly Electric Generator Inventory, September 2026 (Operating sheet): ERCO units, plant coordinates, capacity, technology; BA of plants near Texas (U.S. Energy Information Administration), public domain (US federal government work)
- EIA-930 Hourly Electric Grid Monitor, July-December 2025: ERCO weather-zone (sub-region) demand, BA demand, net generation by fuel and interchange (U.S. Energy Information Administration), public domain (US federal government work)
- Census Bureau Vintage 2024 county population estimates (co-est2024-alldata.csv) (U.S. Census Bureau), public domain (US federal government work)
- Model assembly steps: footprint cut, per-km conductor parameters, transformer defaults, placement, dispatch, demand allocation, DC ties, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries USA ADM1 / ADM2 (US Census MAF/TIGER), public domain: Texas outline and approximate weather zones in geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf ercot-spine-345-138-r3   (flat start: vm 1, vaDeg 0; exit 0, 2.8 s)
Power flow - ERCOT transmission 345/138 kV 2025 peak hour 2025-08-18 17:00 CDT (UnvalidatedAtScale, r3) (5771 buses)
  converged in 10 iteration(s), mismatch 1.11E-011 pu   losses 2619.182 MW / -11155.184 MVAr
  voltage range 0.8678 - 1.0550 pu
  lowest voltages:
      bus 4100   0.8678 pu    -28.878 deg
      bus 2772   0.8694 pu    -28.897 deg
      bus 3859   0.8718 pu    -28.927 deg
      bus 4103   0.8721 pu    -28.930 deg
      bus 1775   0.8764 pu    -28.982 deg
      bus 4573   0.8793 pu    -29.018 deg
      bus 1394   0.9066 pu    -29.336 deg
      bus 4081   0.9132 pu    -29.409 deg
      bus 3786   0.9186 pu    -29.469 deg
      bus 3787   0.9189 pu    -29.472 deg
      bus 1252   0.9190 pu    -29.474 deg
      bus 4080   0.9190 pu    -29.474 deg
(warm start baked into buses.json from that solve: flat start took 10 Newton iterations)
(the build pipeline reading of the pf result) angle spread 91.968 deg; branches over 100 %: 132, over 80 %: 269; west export (FWES + WEST zones, approx.) 6857.4 MW (ERCOT WESTEX static limit 12,240 MW, different interface definition); highest: L05733 (Substation 617471728 138 kV - Tee 138 kV t138_1251) 453.1 %; L05740 (Tee 138 kV t138_1251 - Substation 1528002712 138 kV) 270.3 %; L07692 (Substation 43705092 345 kV - Greens Bayou 345kV Substation 345 kV) 260.0 %; L01610 (OCI Alamo 1 138 kV - Substation 1428418588 138 kV) 206.6 %; L03513 (Substation 488981294 138 kV - Tee 138 kV t138_742) 206.5 %
$ gridsim pf ercot-spine-345-138-r3 (warm start)   (exit 0, 2.1 s)
Power flow - ERCOT transmission 345/138 kV 2025 peak hour 2025-08-18 17:00 CDT (UnvalidatedAtScale, r3) (5771 buses)
  converged in 6 iteration(s), mismatch 8.81E-012 pu   losses 2619.182 MW / -11155.184 MVAr
  voltage range 0.8678 - 1.0550 pu
  lowest voltages:
      bus 4100   0.8678 pu    -28.878 deg
      bus 2772   0.8694 pu    -28.897 deg
      bus 3859   0.8718 pu    -28.927 deg
      bus 4103   0.8721 pu    -28.930 deg
      bus 1775   0.8764 pu    -28.982 deg
      bus 4573   0.8793 pu    -29.018 deg
      bus 1394   0.9066 pu    -29.336 deg
      bus 4081   0.9132 pu    -29.409 deg
      bus 3786   0.9186 pu    -29.469 deg
      bus 3787   0.9189 pu    -29.472 deg
      bus 1252   0.9190 pu    -29.474 deg
      bus 4080   0.9190 pu    -29.474 deg
$ gridsim physics-check ercot-spine-345-138-r3   (exit 0, 1.8 s)
Physics-law audit  -  ercot-spine-345-138-r3  (5771 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.33E-009 | MW | independent dissipation 2619.181505 MW (branch 2619.1815 + shunt 0.0000) vs reported loss 2619.181505 MW |
| 2 | Ohm's law | Holds | 2.45E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.39E-009 | MW | total network loss 2619.181505 MW vs reported 2619.181505 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.54E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.58E-009 | MVA | same residual as law 6, reactive component included at 5279 PQ bus(es), by the bus types the solve ended with; 59 of them declared PV and solved as PQ (59 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 60 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
