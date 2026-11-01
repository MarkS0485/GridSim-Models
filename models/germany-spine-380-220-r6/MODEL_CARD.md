# MODEL CARD: Germany transmission 380/220 kV winter evening 2025-11-27 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official German study results. A solvable rough map of the German 220/380 kV transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO), register-based generation, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2025-11-27 16:30 UTC (17:30 CET), winter evening peak quarter-hour of 2025 (energy-charts: load incl. self-consumption 80671.1 MW; public net generation 73633.2 MW).
- Buses 986 (68 tee junctions, 27 cross-border boundary buses, 434 generator / embedded buses), branches 1516 (lines 962, transformers 554), generators 6259.
- Buses by kV: 380 kV 330, 220 kV 222, 110 kV 381, 21 kV 53.
- Dispatch 73633.2 MW (German plant) + boundary imports 6819.0 MW; demand 78851.1 MW (incl. boundary exports 6526.9 MW and pumping 156.6 MW).
- Slack: 1 reference: Neurath F.
- Islands before selection 2; buses dropped 2.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 986 | 0 (0.0%) | 0 (0.0%) | 525 (53.2%) | 461 (46.8%) |
| Branches | 1516 | 627 (41.4%) | 416 (27.4%) | 473 (31.2%) | 0 (0.0%) |
| Generators | 6259 | 1111 (17.8%) | 0 (0.0%) | 5148 (82.2%) | 0 (0.0%) |
| Demand points | 401 | 0 (0.0%) | 0 (0.0%) | 401 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 137 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 137 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (JAO map / OSM); their existence and the branches between them are JAO's. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, German TSOs: 848 internal lines (all with R, X, B), 153 tie-line rows, 133 transformers.
- Buses resolved by normalised name and voltage: 458 stations, 72 tee junctions, 29 boundary buses.
- Coordinates: JAO map polyline ends for every line, then an OSM ladder (OSM 220/380 kV substations from Overpass + PyPSA-Eur OSM v0.7 buses with OSM names): exact name within 40 km 407, whole-word name and voltage within 10 km 37, position only within 3 km 7, JAO map point only 7; matched 98.5% of stations; by kV {'380': {'1_name_exact': 247, '1_name_word': 21, '2_position': 4, '3_jao_map_only': 5}, '220': {'3_jao_map_only': 2, '1_name_exact': 160, '1_name_word': 16, '2_position': 3}}; placed at a neighbour centroid 1.
- Shape check (crow-fly distance vs JAO length): 9 lines longer than 1.3 x JAO length + 5 km as the crow flies, 26 lines over 20 km shorter than half their JAO length, 7 non-boundary buses outside the Germany outline (+5 km): ['beznau:220', 'beznau:380', 'buers:220', 'buers:380', 'kuehtai:220', 'silz:220', 'y-werben:220'].
- German-German tie-lines: 91 rows reported by both TSOs; kept 50, dropped 28 duplicates, 13 merged (both ends one station), 2 already internal lines.
- Transformers: 91 of 133 JAO units modelled; 42 not (phase shifters and 380/380 kV units in series with a line; 380/220 kV units whose 220 kV side has no JAO line).
- Synthetic 380/220 kV couplings (estimated; median JAO unit {'mva': 712.2, 'x_pct_own': 20.02, 'x_over_r': 75.2}): same-name stations 13 ['bentwisch', 'beznau', 'birkenfeld', 'brunsbuettel', 'garenfeld', 'guetersloh', 'hesseln', 'ibbenbueren', 'luestringen', 'osterath', 'schwandorf', 'st barbara', 'wiesloch']; near-site ['mehrum/n 380 / mehrum 220 (0.49 km)'].
- Islands in the topology: 2 (sizes [557, 2]).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 3743.0 | 0.0 |
| biomass | 10161.6 | 5028.2 |
| coal | 15050.1 | 4897.7 |
| gas | 33972.5 | 12328.4 |
| geothermal | 58.7 | 22.8 |
| hydro | 5314.2 | 2344.9 |
| interconnector | 6819.0 | 6819.0 |
| lignite | 14772.6 | 8922.2 |
| oil | 3319.1 | 514.5 |
| other | 4673.6 | 1583.4 |
| pumped_storage | 9892.3 | 1045.8 |
| solar | 110600.5 | 49.5 |
| waste | 1900.0 | 1110.9 |
| wind_offshore | 9077.9 | 6251.8 |
| wind_onshore | 67320.6 | 29533.1 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| AT | -455.9 | DE:westtirol [AT]:380 (AC boundary bus, share 0.385 of AT tie rating) |
| AT | -182.6 | DE:werben [AT]:220 (AC boundary bus, share 0.154 of AT tie rating) |
| AT | -123.4 | DE:meiningen [AT]:220 (AC boundary bus, share 0.104 of AT tie rating) |
| AT | -123.4 | DE:walgau [AT]:220 (AC boundary bus, share 0.104 of AT tie rating) |
| AT | -297.8 | DE:st peter [AT]:220 (AC boundary bus, share 0.252 of AT tie rating) |
| BE | 272.0 | DE:oberzier:380 (HVDC Oberzier - Lixhe ALEGRO at German converter) |
| CZ | -1181.8 | DE:hradec vychod [CZ]:380 (AC boundary bus, share 0.757 of CZ tie rating) |
| CZ | -380.2 | DE:prestice [CZ]:380 (AC boundary bus, share 0.243 of CZ tie rating) |
| DK | -137.2 | DE:kassoe [DK]:380 (AC boundary bus, share 0.607 of DK tie rating) |
| DK | -88.8 | DE:endrup [DK]:380 (AC boundary bus, share 0.393 of DK tie rating) |
| FR | 184.6 | DE:st avold [FR]:220 (AC boundary bus, share 0.050 of FR tie rating) |
| FR | 2057.6 | DE:vigy [FR]:380 (AC boundary bus, share 0.562 of FR tie rating) |
| FR | 1134.7 | DE:muhlbach [FR]:380 (AC boundary bus, share 0.310 of FR tie rating) |
| FR | 285.1 | DE:vogelgrun [FR]:220 (AC boundary bus, share 0.078 of FR tie rating) |
| LU | -209.0 | DE:flebour [LU]:220 (AC boundary bus, share 0.500 of LU tie rating) |
| LU | -104.5 | DE:blooren [LU]:220 (AC boundary bus, share 0.250 of LU tie rating) |
| LU | -104.5 | DE:heisdorf [LU]:220 (AC boundary bus, share 0.250 of LU tie rating) |
| NL | 500.2 | DE:doetinchem [NL]:380 (AC boundary bus, share 0.320 of NL tie rating) |
| NL | 377.9 | DE:hengelo [NL]:380 (AC boundary bus, share 0.242 of NL tie rating) |
| NL | 377.9 | DE:maasbracht [NL]:380 (AC boundary bus, share 0.242 of NL tie rating) |
| NL | 307.9 | DE:meeden [NL]:380 (AC boundary bus, share 0.197 of NL tie rating) |
| NO | 1104.0 | DE:wilster/w:380 (HVDC Nordlink Cable at German converter) |
| PL | -1040.5 | DE:krajnik [PL]:380 (AC boundary bus, share 0.500 of PL tie rating) |
| PL | -1040.5 | DE:mikulowa [PL]:380 (AC boundary bus, share 0.500 of PL tie rating) |
| SE | 217.0 | DE:siems:220 (Baltic Cable (not in JAO) at nearest station, 3.3 km) |
| CH | -827.1 | DE:laufenburg [CH]:380 (AC boundary bus, share 0.700 of CH tie rating) |
| CH | -178.2 | DE:asphard [CH]:380 (AC boundary bus, share 0.151 of CH tie rating) |
| CH | -51.6 | DE:oftringen [CH]:220 (AC boundary bus, share 0.044 of CH tie rating) |
| CH | -62.0 | DE:y-kuehmoos [CH]:220 (AC boundary bus, share 0.052 of CH tie rating) |
| CH | -63.1 | DE:y-laufenburg [CH]:220 (AC boundary bus, share 0.053 of CH tie rating) |

## Repairs (every change made so the case solves)

- islands dropped (not joined to the main grid in JAO): 1 with 2 buses: [['DE:neckarwestheim:380', 'DE:y-neckarwestheim:380']]
- open-ended tee stubs removed (a 'Y-' junction with one line: the rest of that tee is not in JAO): 5 line(s): ['Putlitz/Sued - Perleberg - Putlitz 596', 'Vieselbach - Remptendorf - Grossschwabhausen 415', 'Y-Grafenrheinfeld (-Hoepfingen - Stalldorf) 411/416', 'Y-Kuehmoos (-Laufenburg - Lindenholz) bl', 'Y-Laufenburg (-Gurtweil - Stokach) rtge']
- neighbouring grids (round 4): external network equivalent of 37 branches, a Kron reduction of the non-German Core TSOs' JAO lines and their mutual tie-lines onto the boundary stations (derived; no thermal rating, 9999 MVA; branches weaker than 10 pu left out): {'jao_rows': 1778, 'nodes': 1275, 'reduced_part': 1231, 'border_stations': 17, 'boundary_buses_mapped': 18, 'boundary_buses_unmapped': ['DE:asphard [CH]:380', 'DE:endrup [DK]:380', 'DE:kassoe [DK]:380', 'DE:laufenburg [CH]:220', 'DE:laufenburg [CH]:380', 'DE:oftringen [CH]:220', 'DE:st peter [AT]:220', 'DE:walgau [AT]:220', 'DE:werben [AT]:220']}; the boundary injections stay fixed
- round 4 rules: converter plant (wind, solar, batteries) at fixed power factor (pq, Q = 0; r1-r3 had EHV-connected converters regulating voltage with +/- 0.33 MVAr per MW); India's radial-chain demand relief not used; r3 moved 698 MW from 8 chains); r3's coarse spanning-tree equivalent (0.3 ohm/km guessed) replaced by the JAO reduction above
- voltage-control rule (r5 EU limits, r6 national): RfG (Regulation (EU) 2016/631) Art. 5 with the German thresholds (BK6-16-166: B 0.135 / C 36 / D 45 MW) - synchronous register units >= 0.135 MW (type B+) and converter units at or above the national type C (36 MW) or connected at 110 kV+ (type D, incl. every offshore farm) control voltage; aggregates of small units and idle converters (< 1 % output) run at unity pf; replaces the round-4 judgement for the North Sea HVDC landings
- (superseded in round 5 by the RfG rule) round 4 judgement (recorded for review): the offshore wind at the four North Sea VSC-HVDC landing stations (Diele, Doerpen/West, Emden/Ost, Buettel) is modelled voltage-controlling (pv, +/- 0.33 MVAr per MW), because the onshore HVDC converter stations are TSO assets that regulate voltage at the landing point; every other converter (all onshore wind, solar, batteries, the AC-connected Baltic farms) is at fixed pf. With ALL converters at fixed pf the staged repair stopped at 0.75 x snapshot (0.85-0.92 x without the regional balance); with only these terminals pv it reaches 1.0 x (diagnostic runs 2026-11-01)
- data (from round 4): national dispatch per fuel and national demand shared over the four control areas (50Hertz, Amprion, TenneT, TransnetBW) by SMARD quarter-hour shares at 2025-11-27 16:30 UTC
- data (round 6): onshore wind and biomass placed from the MaStR bulk export 2026-11-01 (units in operation on 2025-11-27 at their coordinates, grouped by grid connection point / park, EHV-connected parks on the station bus, others embedded; RfG class per park from connection level and park size; state aggregates of these fuels kept only for the units without coordinates): {"units": 52329, "mw": 76300.4, "by_fuel_mw": {"biomass": 8975.9, "wind_onshore": 67324.5}, "ehv_mw": 2136.0, "rfg_regulating_mw": 30911.0, "no_coordinates_mw": 113.8, "beyond_place_max_km_mw": 0.0, "no_coordinates_by_state_code": {"biomass:1400": 0.1, "biomass:1401": 0.1, "biomass:1402": 2.1, "biomass:1403": 33.9, "biomass:1404": 0.0, "biomass:1405": 0.6, "biomass:1406": 0.1, "biomass:1407": 1.0, "biomass:1408": 4.6, "biomass:1409": 21.5, "biomass:1410": 0.5, "biomass:1411": 0.7, "biomass:1412": 0.0, "biomass:1413": 0.4, "biomass:1414": 0.7, "biomass:1415": 0.3, "wind_onshore:1400": 0.1, "wind_onshore:1401": 0.0, "wind_onshore:1402": 0.3, "wind_onshore:1403": 1.0, "wind_onshore:1404": 0.1, "wind_onshore:1405": 0.1, "wind_onshore:1406": 0.0, "wind_onshore:1407": 0.2, "wind_onshore:1408": 1.8, "wind_onshore:1409": 40.7, "wind_onshore:1410": 0.1, "wind_onshore:1411": 2.5, "wind_onshore:141
- unit commitment: per synchronous fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; lignite 15/34 units; coal 10/34 units; gas 35/769 units; oil 2/76 units; hydro 29/341 units; pumped_storage 5/98 units; biomass 0/105 units; waste 48/108 units; other 9/134 units. Offline units in the case: 1494 (0 MW, pq, no inertia, no fault infeed; estimated)
- RfG classification of generator rows: converter/other unity pf 1427, converter/other voltage-controlling 275, synchronous unity pf 2667, synchronous voltage-controlling 1879
- synchronous plant connected at extra-high voltage moved behind 53 lumped GSUs (44891 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (HV/MV units and state aggregates) on 381 embedded buses behind lumped supply equivalents (244121 MVA, x 20 % own rating; estimated), role pq with Q = 0
- slack: largest dispatched EHV synchronous unit Neurath F at Osterath 380kV gen bus, reactive band +/-20000 MVAr (synthetic)
- reactive repair stopped early at some stage(s): pass limit 60 reached
- bus shunts placed where the snapshot needs reactive support (60 passes of a Newton solve without reactive limits): 2 reactors 70 MVAr, 135 capacitors 10060 MVAr (synthetic; JAO publishes no reactive compensation, real German stations run many reactors, capacitors and STATCOMs)

## Known gaps

- No 110 kV network: demand and embedded generation stand for everything below 220 kV; the embedded supply equivalent is one lumped transformer per station.
- No reactive compensation from JAO (excluded by scope); the bus shunts are fixed repairs.
- Phase shifters (21 in JAO) and 380/380 kV units are not modelled: 28 units; their series reactance (about 12 ohm) and angle control are absent, so loop flows through Vierraden, Roehrsdorf, Hamburg/Ost, Diele, Krempermarsch and Wuergau are uncontrolled.
- Busbar splits are not modelled: one bus per station and voltage (JAO 'C1/C2' and 'Abzweig' parts merged).
- Neighbouring grids are fixed boundary injections (energy-charts physical flows at the snapshot): no foreign network, no fault infeed from abroad, so fault levels near the borders are low.
- Generator locations: register coordinates for 1,111 units, district centre (MaStR publishes only the district key) for 774 units; wind, solar and small units are state totals spread by municipality area / population.
- Offshore wind landing weights are recalled export capacities ([VERIFY]).
- Demand is allocated by population only (no industrial load map); load incl. self-consumption 80,671 MW versus modelled public-grid demand.
- GridSim IEC 60909 feeds the fault from every machine in the file at its rating: offline units (not committed, reserve not called) and idle inverters are flagged converterInterfaced / converterFaultCurrentPu 0 here; committed plant feeds at full rating whatever its dispatch; all wind converters feed at GridSim's default k = 1.2 x rated current (German grid code fault-ride-through reactive current).

## Sources

- Core Static Grid Model, 9th release (2026-03): lines, tie-lines, transformers (R, X, B, Imax), and its publication map (JAO S.A. on behalf of the Core TSOs (50Hertz, Amprion, TenneT DE, TransnetBW for Germany)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- PyPSA-Eur prebuilt OSM network v0.7 (buses), with OSM names fetched by element id 2026-10-31 (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- Kraftwerksliste der Bundesnetzagentur, Datenstand 26.06.2026 (Bundesnetzagentur), derived from MaStR (dl-de/by-2-0); page states no licence
- Marktstammdatenregister public unit list (locations, municipality keys) (Bundesnetzagentur), Datenlizenz Deutschland Namensnennung 2.0
- Gemeindeverzeichnis GV-ISys 31.12.2025 (population, area, centre points) (Statistisches Bundesamt (Destatis)), Datenlizenz Deutschland Namensnennung 2.0
- Public net generation by type, load and cross-border physical flows, 2025-11-27 16:30 UTC (Fraunhofer ISE, energy-charts.info), CC BY 4.0
- Model assembly steps: name resolution, coordinates, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries DEU ADM1 (BKG NUTS250), dl-de/by-2-0: state assignment and state shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: Germany outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf germany-spine-380-220-r6   (flat start: vm 1, vaDeg 0; exit 0, 1.0 s)
Power flow - Germany transmission 380/220 kV winter evening 2025-11-27 (UnvalidatedAtScale) (986 buses)
  converged in 13 iteration(s), mismatch 7.25E-012 pu   losses 2209.940 MW / -3268.766 MVAr
  voltage range 0.9749 - 1.0309 pu
  lowest voltages:
      bus 449    0.9749 pu    -56.524 deg
      bus 939    0.9753 pu    -55.961 deg
      bus 440    0.9759 pu     -1.508 deg
      bus 382    0.9762 pu    -26.680 deg
      bus 934    0.9767 pu     -0.387 deg
      bus 889    0.9767 pu    -26.051 deg
      bus 433    0.9772 pu    -42.152 deg
      bus 380    0.9772 pu    -28.075 deg
      bus 334    0.9773 pu     -1.291 deg
      bus 929    0.9777 pu    -41.415 deg
      bus 887    0.9780 pu    -26.822 deg
      bus 852    0.9783 pu      0.464 deg
(warm start baked into buses.json from that solve: flat start took 13 Newton iterations)
$ gridsim pf germany-spine-380-220-r6 (warm start)   (exit 0, 0.9 s)
Power flow - Germany transmission 380/220 kV winter evening 2025-11-27 (UnvalidatedAtScale) (986 buses)
  converged in 10 iteration(s), mismatch 7.29E-012 pu   losses 2209.940 MW / -3268.766 MVAr
  voltage range 0.9749 - 1.0309 pu
  lowest voltages:
      bus 449    0.9749 pu    -56.524 deg
      bus 939    0.9753 pu    -55.961 deg
      bus 440    0.9759 pu     -1.508 deg
      bus 382    0.9762 pu    -26.680 deg
      bus 934    0.9767 pu     -0.387 deg
      bus 889    0.9767 pu    -26.051 deg
      bus 433    0.9772 pu    -42.152 deg
      bus 380    0.9772 pu    -28.075 deg
      bus 334    0.9773 pu     -1.291 deg
      bus 929    0.9777 pu    -41.415 deg
      bus 887    0.9780 pu    -26.822 deg
      bus 852    0.9783 pu      0.464 deg
$ gridsim physics-check germany-spine-380-220-r6   (exit 0, 0.9 s)
Physics-law audit  -  germany-spine-380-220-r6  (986 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.72E-010 | MW | independent dissipation 2209.940153 MW (branch 2209.9402 + shunt 0.0000) vs reported loss 2209.940153 MW |
| 2 | Ohm's law | Holds | 2.51E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 4.42E-010 | MW | total network loss 2209.940153 MW vs reported 2209.940153 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 3.52E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.17E-009 | MVA | same residual as law 6, reactive component included at 732 PQ bus(es), by the bus types the solve ended with; 64 of them declared PV and solved as PQ (64 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
