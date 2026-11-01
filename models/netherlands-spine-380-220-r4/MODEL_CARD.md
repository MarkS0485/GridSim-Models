# MODEL CARD: Netherlands transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Dutch study results. A solvable rough map of the Dutch 220/380 kV transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, TenneT NL), register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r4.

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), the winter peak quarter-hour of 2025 (energy-charts 'Load') (energy-charts: load 19632.0 MW; public net generation 23663.3 MW).
- Buses 138 (7 cross-border boundary buses, 46 generator / embedded buses), branches 208 (lines 114, transformers 94), generators 814.
- Buses by kV: 380 kV 42, 220 kV 13, 150 kV 74, 21 kV 9.
- Dispatch 23663.3 MW (Dutch plant) + boundary imports 223.0 MW; demand 23523.2 MW (incl. boundary exports 5732.0 MW).
- Slack: 1 reference: Eem #2.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 138 | 0 (0.0%) | 0 (0.0%) | 48 (34.8%) | 90 (65.2%) |
| Branches | 208 | 95 (45.7%) | 0 (0.0%) | 76 (36.5%) | 37 (17.8%) |
| Generators | 814 | 0 (0.0%) | 0 (0.0%) | 814 (100.0%) | 0 (0.0%) |
| Demand points | 45 | 0 (0.0%) | 0 (0.0%) | 45 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 39 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 39 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map); their existence and the branches between them are JAO's (except the OSM-added corridors, estimated). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, TenneT NL: 92 internal lines (all with R, X, B and Imax; 70 at 380 kV, 22 at 220 kV), 12 tie-line rows (BE 4, DE 8), 10 transformers (8 x 380/220 kV, 2 phase shifters at Meeden).
- Buses: 48 stations and 7 boundary buses; positions from a curated JAO name -> OSM substation table for 53 buses, JAO map points for 2 (diele [DE]:380, eemshaven synergieweg:380).
- Circuits added from OSM (not in the JAO list; estimated): 10 circuits added from OSM (estimated): oostzaan - beverwijk x2; beverwijk - vijfhuizen x2; vijfhuizen - bleiswijk x2; wijk aan zee - beverwijk x2; maasbracht - boxmeer x1; boxmeer - dodewaard x1; per km R 0.0200 ohm, X 0.2733 ohm, B 4.234 uS, rating Imax 3300 A (medians of 43 JAO TenneT 380 kV overhead lines).
- Transformers: 8 JAO 380/220 kV units modelled (Eemshaven 4, Ens 3, Meeden 1); synthetic couplings (median JAO unit {'mva': 789.8, 'x_pct_own': 15.35, 'x_over_r': 346.5}): ['vierverlaten'] and near-site ['zwolle 380 / hessenweg 220 (0.17 km)']; not modelled: the 2 Meeden phase shifters (Diele ties end at a fixed-injection boundary bus).
- Islands in the topology: 1 (sizes [55]).
- Shape check (crow-fly distance vs JAO length): 0 outliers [].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 390.7 | 0.0 |
| biomass | 877.0 | 510.5 |
| coal | 3470.0 | 3221.1 |
| gas | 13702.5 | 9207.0 |
| interconnector | 223.0 | 223.0 |
| nuclear | 515.0 | 482.7 |
| oil | 107.0 | 0.0 |
| other | 5254.9 | 4203.9 |
| solar | 7177.1 | 0.0 |
| waste | 696.2 | 283.7 |
| wind_offshore | 6362.0 | 4414.4 |
| wind_onshore | 5027.4 | 1340.0 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| BE | -1008.1 | NL:zandvliet [BE]:380 (AC boundary bus, share 0.519 of BE tie rating) |
| BE | -934.9 | NL:van eyck [BE]:380 (AC boundary bus, share 0.481 of BE tie rating) |
| DK | -618.0 | NL:eemshaven converterstation:380 (HVDC COBRAcable at the Dutch converter station) |
| DE | -680.7 | NL:gronau [DE]:380 (AC boundary bus, share 0.270 of DE tie rating) |
| DE | -315.6 | NL:oberzier [DE]:380 (AC boundary bus, share 0.125 of DE tie rating) |
| DE | -315.6 | NL:siersdorf [DE]:380 (AC boundary bus, share 0.125 of DE tie rating) |
| DE | -333.8 | NL:diele [DE]:380 (AC boundary bus, share 0.132 of DE tie rating) |
| DE | -878.3 | NL:niederrhein [DE]:380 (AC boundary bus, share 0.348 of DE tie rating) |
| NO | -647.0 | NL:eemshaven converterstation:380 (HVDC NorNed at the Dutch converter station) |
| GB | 223.0 | NL:maasvlakte:380 (HVDC BritNed at the Dutch converter station) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 9 lumped GSUs (17952 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (150 / 110 kV units and the 'Others' aggregates) on 37 embedded buses behind lumped supply equivalents (24934 MVA, x 20 % own rating; estimated), role pq with Q = 0
- r4: embedded plant behind the station's EHV/HV transformation: 37 synthetic HV buses and EHV/HV transformers (42000 MVA in units of 500 MVA, at least 2 per station, x 12 % own rating, X/R 40; ASSUMED typical [VERIFY]; synthetic)
- station export cap: NL:delesto:220: 447.3 MW dispatched vs 340.1 MW cap (85% of 400 MVA of branches); 107.2 MW moved to the same fuel elsewhere
- unit commitment: per synchronous fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 3/3 units (0 MW offline); gas 16/40 units (2144 MW offline); biomass 4/11 units (193 MW offline); waste 3/10 units (313 MW offline); oil 0/1 units (107 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- offshore-landing converter plant runs at Q = 0 (pq): a 1.02 pu setpoint there fought the neighbouring synchronous setpoints and needed 2,710 MVAr of synthetic capacitors in r1
- register correction: Maasvlakte Uniper (Hard Coal, 2306 MW): capacity -> 1070 MW: Maasvlakte Power Plant 3 (Uniper) is the one coal unit left at that site, about 1,070 MW; units MV1/MV2 closed
- register correction: Eemshaven (Natural Gas, 1410 MW): drop: duplicate of the Eemscentrale (Engie, register row 'Eem')
- register correction: Eem (Natural Gas, 3210 MW): capacity -> 1950 MW: Eemscentrale (Engie) is about 1,950 MW of CCGT; the register row sums more than the station
- register correction: Amazon Shell Hkn Offshore Wind Farm (Wind, 759 MW): drop: duplicate of 'Hollandse Kust Noord Offshore Wind Farm' (CrossWind, 759 MW)
- slack: largest dispatched EHV synchronous unit Eem #2 at Eemshaven Oudeschip 380kV gen bus, reactive band +/-11471 MVAr (synthetic)
- demand on radial chains capped at 60% of the feeding branch rating: 1 chains, 702 MW moved to the meshed root (estimated)
- bus shunts placed where the snapshot needs reactive support (3 passes of a Newton solve without reactive limits): 0 reactors 0 MVAr, 39 capacitors 3510 MVAr (synthetic; JAO publishes no reactive compensation; TenneT runs many 380 kV shunt reactors and capacitor banks): Ens 220kV HV bus +10, Ens 220kV +10, Ens 220kV embedded bus +10, Breukelen Kortrijk 380kV embedded bus +10, Hessenweg 220kV HV bus +10, Hessenweg 220kV +10, Breukelen Kortrijk 380kV HV bus +10, Hessenweg 220kV embedded bus +10, Oostzaan 380kV embedded bus +10, Oostzaan 380kV HV bus +10, Oudehaske 220kV embedded bus +20, Oudehaske 220kV HV bus +20, Oudehaske 220kV +20, Bergum 220kV HV bus +30, Bergum 220kV +30, Louwsmeer 220kV HV bus +30, Bergum 220kV embedded bus +30, Louwsmeer 220kV +30, Louwsmeer 220kV embedded bus +30, Breukelen Kortrijk 380kV +70, Doetinchem 380kV HV bus +70, Van Eyck [BE] 380kV +80, Maasbracht 380kV +80, Eindhoven 380kV +80, Oberzier [DE] 380kV +90, Siersdorf [DE] 380kV +90, Lelystad 380kV +110, Ens 380kV +120, Boxmeer 380kV +140, Zwolle 380kV +140, Geertruidenberg 380kV gen bus +160, Dodewaard 380kV +170, Wijk Aan Zee 380kV gen bus +180, Niederrhein [DE] 380kV +190, Doetinchem 380kV +190, Gronau [DE] 380kV +190, Hengelo 380kV +190, Diemen 380kV gen bus +220, Maasbracht 380kV gen bus +610

## Fitted and assumed values (the brief's NO FITTING TO THE SOLVER rule; added by hand 2026-11-01)

- ASSUMED [VERIFY] (r4): the embedded plant sits behind a synthetic HV bus per station and synthetic EHV/HV
  transformers: at least 2 units of 500 MVA each, x 12 % on own rating, X/R 40 (typical 380/150 kV units; 37 buses,
  42,000 MVA in all). This is a physical rule that keeps embedded plant from feeding the EHV bus directly. It was
  not tuned to the fault level: Krimpen 380 kV Ik'' moved from 67.94 to 65.76 kA and stays above 63 kA.
- Krimpen above 63 kA is an open-data gap, not something to fit. OSM maps no busbar or bay inside the Krimpen a/d
  IJssel 380 / 150 kV substations (Overpass check 2026-11-01: 0 busbar ways, 0 bays in 51.88-51.94 N,
  4.55-4.66 E), so no busbar split is possible. No current TenneT per-station short-circuit table was found in
  open data.
- No other value was set from the solve.

## Round history (the solver's findings that drove each round)

- r1: first build; reactive repair by fixed bus shunts only (no other change).
- r1 solve: pf 5 iterations flat, V 0.9547-1.0210 pu, losses 293.393 MW, angle spread 39.138 deg, no branch over 100 % (Vierverlaten synthetic coupling 96.9 %), 20 synthetic capacitors 3640 MVAr (2710 MVAr at the offshore-landing converter PV buses), IEC 60909 380 kV Ik'' max 71.51 kA (Krimpen), median 47.54 kA.
- r2 changes: (1) offshore-landing converter plant at Q = 0 (pq) instead of a 1.02 pu setpoint; (2) unit commitment of register coal / gas / biomass / waste / oil units, largest first until committed capacity x 0.8 covers the energy-charts target (the Germany rule; offline units feed no fault current); (3) a second synthetic 380/220 kV unit at Vierverlaten.
- r2 solve: pf 6 iterations flat, V 0.9567-1.0200 pu, losses 321.879 MW, angle spread 40.886 deg, 2 branches over 100 % (Delesto - Weiwerd 220 kV W and Z, 100.0 %), 30 synthetic capacitors 2870 MVAr (no landing-bus setpoint fights left; the rest spread over the 220 kV north and the east), IEC 60909 380 kV Ik'' max 67.94 kA (Krimpen), median 45.98 kA.
- r3 change: station export cap (plant at one station <= 85 % of the summed rating of its branches; the excess moves to the same fuel's other committed units). Only Delesto binds.

## Known gaps

- No 150 / 110 kV network: demand and embedded generation stand for everything below 220 kV; the embedded supply equivalent is one lumped transformer per station.
- JAO lists only the elements relevant to flow-based capacity calculation: TenneT 380 kV stations missing from it (Tilburg, Hoek van Holland, Tweede Maasvlakte, the plant stations at Maasvlakte, Sloe, Enecogen, Onyx) are not modelled; their plant sits on the nearest modelled station.
- No reactive compensation from JAO; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per station and voltage.
- Neighbouring grids are fixed boundary injections (energy-charts physical flows at the snapshot): no foreign network, no fault infeed from abroad, so fault levels near the borders are low; the Meeden phase shifters are absent.
- Generator fleet from powerplantmatching (merged registers): some rows are duplicates or carry retired capacity; four are corrected by hand ([VERIFY]); onshore wind 5,027 MW in the register vs about 7 GW installed; solar 7,177 MW vs about 28 GW (solar is at 0 MW in the snapshot, so only its fault infeed flag matters).
- energy-charts 'Others' (4,203.9 MW) is modelled as an embedded aggregate spread by population; in reality it is mostly industrial CHP in the Rotterdam, Moerdijk, Geleen, Delfzijl and IJmond clusters.
- Demand is allocated by population only (no industrial load map). energy-charts 'Load' is 19,632.0 MW; the modelled public-grid demand is (generation + net import) x 0.98.
- HVDC link ratings (NorNed 700, COBRAcable 700, BritNed 1,000 MW) are public figures, not JAO's ([VERIFY]).

## Sources

- Core Static Grid Model, 9th release (2026-03): TenneT NL lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (TenneT TSO B.V. for the Netherlands)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap 220/380 kV substations (Overpass API, 2026-10-31): station and converter positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7 (lines): route length and circuits of the 380 kV corridors missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Netherlands units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- GeoNames Netherlands populated places (population, position) (GeoNames), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Netherlands, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries NLD ADM1 (National Georegister), CC0 1.0: province assignment and province shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: Netherlands outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf netherlands-spine-380-220-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.9 s)
Power flow - Netherlands transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (138 buses)
  converged in 6 iteration(s), mismatch 3.67E-012 pu   losses 325.853 MW / 260.030 MVAr
  voltage range 0.9556 - 1.0463 pu
  lowest voltages:
      bus 66     0.9556 pu    -14.449 deg
      bus 65     0.9566 pu     -7.696 deg
      bus 86     0.9582 pu     -4.453 deg
      bus 109    0.9599 pu     -4.891 deg
      bus 87     0.9603 pu    -12.102 deg
      bus 97     0.9604 pu    -14.013 deg
      bus 110    0.9610 pu    -11.678 deg
      bus 96     0.9612 pu     -6.569 deg
      bus 5      0.9616 pu    -18.340 deg
      bus 80     0.9638 pu    -25.962 deg
      bus 79     0.9647 pu    -21.729 deg
      bus 30     0.9653 pu    -17.219 deg
(warm start baked into buses.json from that solve: flat start took 6 Newton iterations)
(the build pipeline reading of the pf result) angle spread 39.271 deg; branches over 100 %: 0, over 80 %: 0; highest: gsu:NL:maasvlakte:380 (Maasvlakte 380kV gen bus - Maasvlakte 380kV) 78.6 %; gsu:NL:diemen:380 (Diemen 380kV gen bus - Diemen 380kV) 78.4 %; gsu:NL:wijk aan zee:380 (Wijk Aan Zee 380kV gen bus - Wijk Aan Zee 380kV) 78.2 %; gsu:NL:geertruidenberg:380 (Geertruidenberg 380kV gen bus - Geertruidenberg 380kV) 74.8 %; gsu:NL:borssele:380 (Borssele 380kV gen bus - Borssele 380kV) 74.3 %
$ gridsim pf netherlands-spine-380-220-r4 (warm start)   (exit 0, 1.1 s)
Power flow - Netherlands transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (138 buses)
  converged in 1 iteration(s), mismatch 1.45E-011 pu   losses 325.853 MW / 260.030 MVAr
  voltage range 0.9556 - 1.0463 pu
  lowest voltages:
      bus 66     0.9556 pu    -14.449 deg
      bus 65     0.9566 pu     -7.696 deg
      bus 86     0.9582 pu     -4.453 deg
      bus 109    0.9599 pu     -4.891 deg
      bus 87     0.9603 pu    -12.102 deg
      bus 97     0.9604 pu    -14.013 deg
      bus 110    0.9610 pu    -11.678 deg
      bus 96     0.9612 pu     -6.569 deg
      bus 5      0.9616 pu    -18.340 deg
      bus 80     0.9638 pu    -25.962 deg
      bus 79     0.9647 pu    -21.729 deg
      bus 30     0.9653 pu    -17.219 deg
$ gridsim physics-check netherlands-spine-380-220-r4   (exit 0, 0.9 s)
Physics-law audit  -  netherlands-spine-380-220-r4  (138 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.34E-010 | MW | independent dissipation 325.853309 MW (branch 325.8533 + shunt 0.0000) vs reported loss 325.853309 MW |
| 2 | Ohm's law | Holds | 1.47E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 2.30E-010 | MW | total network loss 325.853309 MW vs reported 325.853309 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 3.89E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.44E-009 | MVA | same residual as law 6, reactive component included at 129 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses netherlands-spine-380-220-r4   (exit 0, 1.5 s)
(full sweep in iec60909_all_buses.txt) 380 kV stations (35): Ik'' max 65.76 kA (Krimpen Aan Den Ijssel 380kV), min 19.07 kA (Boxmeer 380kV), median 45.08 kA; 220 kV stations (13): Ik'' max 42.09 kA (Eemshaven 220kV), min 12.93 kA (Bergum 220kV), median 33.11 kA
```
