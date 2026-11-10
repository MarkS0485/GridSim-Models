# Canada West 500-345-230-161-138 kV 2025-12-11 (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against operator study results. A solvable rough map of the Alberta and British Columbia grids (Western Interconnection: 500 / 360 / 287 / 240 / 230 / 138 kV) for one snapshot: OSM-mapped lines and stations (>= 100 kV), standard per-km parameters, NACEI / OSM plants, published system demand allocated by population. Use it to learn, compare and explore, not to plan or operate.

Round: r4. Frequency 60 Hz. Neighbouring systems are fixed boundary injections.

## What it is

- Snapshot: 2025-12-11 18:00 MST (hour ending; 17:00 PST), Alberta's record peak day with BC coincident (published demand 22382.00 MW).
- Buses 1371 (58 generator terminal buses, 374 tee buses), branches 1973 (lines 1780, transformers 193), generators 106.
- Buses by kV: 500 kV 47, 345 kV 6, 230 kV 410, 161 kV 5, 138 kV 845, 13.8 kV 58.
- Dispatch 22010.0 MW (in-system plant) + boundary imports 372.0 MW; demand 21468.7 MW (incl. boundary exports 0.0 MW).
- Slack: 1 reference: Mica.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1371 | 939 (68.5%) | 0 (0.0%) | 374 (27.3%) | 58 (4.2%) |
| Branches | 1973 | 0 (0.0%) | 1780 (90.2%) | 0 (0.0%) | 193 (9.8%) |
| Generators | 106 | 57 (53.8%) | 0 (0.0%) | 49 (46.2%) | 0 (0.0%) |
| Demand points | 326 | 0 (0.0%) | 0 (0.0%) | 326 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 180 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 180 (100.0%) |

Tag mapping: attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OSM via adapt_osm (CA_AB, CA_BC): CA_AB: 649 sites, 1159 branches, 953 buses, 68 couplings, 117 branches dropped at a free end, 13 HVDC ways left out; CA_BC: 456 sites, 680 branches, 550 buses, 40 couplings, 52 branches dropped at a free end, 25 HVDC ways left out.
- HVDC converter sites (OSM substation=converter): 8; their AC buses removed: ['sw273431768_138'] (ties are boundary injections).
- Islands 20, sizes [1313, 9, 7, 6, 6, 5, 5, 4, 4, 3]; main island kept (1313 buses, 374 tees); by kV {'138': 845, '345': 6, '230': 410, '500': 47, '161': 5}; route km {'500': 6762.9, '345': 242.8, '230': 11426.3, '161': 145.4, '138': 14625.7}; 314 lines floored to 0.5 km.
- Largest dropped islands: 9 buses near 53.89, -128.47 (Kemano Substation 287 kV); 7 buses near 50.624, -113.058 (Blackie 144 kV); 6 buses near 50.471, -127.095 (Keogh Substation 138 kV); 6 buses near 57.094, -130.319 (Substation 610199852 287 kV); 5 buses near 49.27, -123.112 (Olympic Village Substation 230 kV); 5 buses near 55.938, -129.79 (Substation 532973978 138 kV).
- Per-km parameters: 735 kV R 0.0117 X 0.3273 ohm/km B 5.061 uS/km, 6620 MVA (Quad 1355 kcmil ACSR (HQ 735 kV, OPAL-RT HYPERSIM example)); 500 kV R 0.0242 X 0.3493 ohm/km B 4.604 uS/km, 2572 MVA (Triple Rail 954 kcmil 45/7 ACSR); 345 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1183 MVA (Twin Rail 954 kcmil 45/7 ACSR); 315 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1080 MVA (Twin Rail 954 kcmil 45/7 ACSR); 230 kV R 0.0432 X 0.3623 ohm/km B 4.462 uS/km, 723 MVA (Twin Drake 795 kcmil 26/7 ACSR); 161 kV R 0.0864 X 0.4761 ohm/km B 3.436 uS/km, 253 MVA (Drake 795 kcmil 26/7 ACSR); 138 kV R 0.0864 X 0.4647 ohm/km B 3.523 uS/km, 217 MVA (Drake 795 kcmil 26/7 ACSR); 115 kV R 0.0864 X 0.4593 ohm/km B 3.566 uS/km, 181 MVA (Drake 795 kcmil 26/7 ACSR).
- Couplings: 135 synthetic transformers at OSM sites with two voltages, 2 units by HV class (735: 1650, 500: 750, 345 / 315: 600, 230: 300, below: 150 MVA each), x 12 % own rating.

## Generation and dispatch by fuel (MW)

| Fuel | Generators | Capacity in case | Dispatch |
|---|---:|---:|---:|
| biomass | 3 | 262.0 | 194.1 |
| gas | 34 | 13867.0 | 10271.0 |
| hydro | 27 | 14384.2 | 10654.1 |
| interconnector | 2 | 372.0 | 372.0 |
| solar | 16 | 556.5 | 0.0 |
| wind | 24 | 2969.2 | 890.8 |

## Boundary injections (MW, + import)

| Tie | MW | Bus | Source |
|---|---:|---|---|
| Montana (MATL and Langdon - Montana ties, NWMT) | 87.0 | Stirling 138 kV (62.7 km) | EIA-930 interchange NWMT -> AESO, hour ending 2025-12-11 18:00 MST: +87 MW (NWMT export) |
| Bonneville (BPAT, Ingledow - Custer and Nelway ties) | 285.0 | McLellan Substation 230 kV (11.1 km) | EIA-930 interchange BPAT -> BCHA, hour ending 2025-12-11 17:00 PST: +285 MW (BPAT export) |
| Saskatchewan (McNeill back-to-back) | 0.0 | Cypress 240 kV (7.5 km) | no open hourly AB - SK flow at the hour (AESO 2025 average +1 MW): 0 MW assumed [VERIFY] |

## Repairs (every change made so the case solves)

- seasonal line ratings: all 1780 overhead lines x 1.0415 (seasonal factor 1.0415 = JAO ratio winter 1.1034 / base 'interseason' 1.0594 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- synchronous plants of 20 MW or more behind 58 lumped GSUs (31681 MVA, x 13 % own rating, X/R 40, terminal 13.8 kV; synthetic), role pv at 1.02 pu, Q range -0.3 to +0.48 x MW (estimated); wind, solar, small plants and boundary imports pq with Q = 0
- slack: largest dispatched unit within 150 km of the demand centre (51.06, -117.55): Mica at Kinbasket Mica Forebay 500 kV 500kV gen bus, reactive band +/-15256 MVAr (synthetic)
- loss accounting: the snapshot demand figure includes transmission losses; population demand 22382.0 MW scaled by 0.959194 (L = 913.327 MW, the r1 gridsim pf loss; estimated)
- no radial-chain demand relief (India routine not used:
- line-end shunt reactors on 79 lines at 500 kV and above: 70% of each line's charging, 5503 MVAr in all, as fixed bus shunts at the two ends (physical rule; sizes estimated, synthetic) [VERIFY]
- reactive repair staged by load scaling: shunts placed at 0.20, 0.22, 0.24, 0.26, 0.28, 0.30, 0.32, 0.34, 0.36, 0.38, 0.40, 0.42, 0.44, 0.46, 0.48, 0.50, 0.52, 0.54, 0.56, 0.58, 0.60, 0.62, 0.64, 0.66, 0.68, 0.70, 0.72, 0.74, 0.76, 0.78, 0.80, 0.82, 0.84, 0.86, 0.88, 0.90, 0.92, 0.94, 0.96, 0.98, 1.00 x demand and dispatch in turn (estimated)
- reactive repair stopped early at some stage(s): pass 3: no damped step solves; 5 buses still outside; one-stage repair stalled: shunts discarded, staged route used instead; pass 2: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside; pass 1: no damped step solves; 5 buses still outside
- bus shunts placed where the snapshot needs reactive support (179 passes of a Newton solve without reactive limits): 53 reactors 1080 MVAr, 79 capacitors 5320 MVAr (synthetic; no open reactive compensation list; 735 kV systems run large shunt reactors and SVCs / synchronous condensers): Glenannan Substation 500 kV 500kV -100, Telkwa Substation 500 kV 500kV -90, McLeese Capacitor Station 500 kV 500kV -70, Substation 753730282 230 kV 230kV -60, Livock Substation 500 kV 500kV -60, Cranberry Lake 144 kV 138kV -30, Lubicon 144 kV 138kV -30, Thickwood Hills Substation 500 kV 500kV -30, Soda Creek Substation 230 kV 230kV -30, Sulphur Point 144 kV 138kV -20, Rainbow Lake 144 kV 138kV -20, Chadotte River 144 kV 138kV -20, Substation 538665951 230 kV 230kV -20, Shamrock 240 kV 230kV -20, Round Hill Substation 240 kV 230kV -20, Tee 240 kV t240_73 230kV -20, Mc Millan 240 kV 230kV -20, Veteran 144 kV 138kV -20, Tee 144 kV t144_79 138kV -20, Tee 144 kV t144_50 138kV -20, Donnelly Substation 144 kV 138kV -20, Substation 912758780 138 kV 138kV -20, Valemount Substation 138 kV 138kV -20, Norcen 144 kV 138kV -10, Ribstone Creek 144 kV 138kV -10, Cypress 240 kV 230kV -10, Amoco Empress 240 kV 230kV -10, Waddell 144 kV 138kV -10, Chard 144 kV 138kV -10, Tee 144 kV t144_74 138kV -10, Leismer 144 kV 138kV -10, Vilna 144 kV 138kV -10, 100 Mile House Substation 230 kV 230kV -10, Tee 230 kV t230_25 230kV -10, Red Bluff Substation 230 kV 230kV -10, Tee 230 kV t230_24 230kV -10, Badlands Substation 144 kV 138kV -10, Wabasca Substation 240 kV 230kV -10, Brintnell 240 kV 230kV -10, Wheatland 144 kV 138kV -10, Substation 99445317 230 kV 230kV -10, Quality Wind IPP Substation 230 kV 230kV -10, Substation 109645554 230 kV 230kV -10, Crow Lake 144 kV 138kV -10, Tumbler Ridge Substation 230 kV 230kV -10, Goose River 144 kV 138kV -10, Virginia Hills 144 kV 138kV -10, Forty Mile Bow Island Substation 240 kV 230kV -10, Forty Mile Wind Power Project Substation 240 kV 230kV -10, Whitla 240 kV 230kV -10, Ring Creek 144 kV 138kV -10, High Level Substation 144 kV 138kV -10, Tee 144 kV t144_9 138kV -10, Zama Lake 144 kV 138kV +0, Tee 144 kV t144_13 138kV +0, Tee 144 kV t144_12 138kV +0, Blumenort 144 kV 138kV +0, Lakesend 144 kV 138kV +0, High Prairie Substation 144 kV 138kV +0, Bullpound 144 kV 138kV +0, Kidney Lake 144 kV 138kV +10, Tee 144 kV t144_11 138kV +10, Tee 144 kV t144_10 138kV +10, Tee 230 kV t230_15 230kV +10, Enmax Substation No. 12 138 kV 138kV +10, Substation 503378392 138 kV 138kV gen bus +10, Ervick Substation 138 kV 138kV +10, Lloydminster 144 kV 138kV +10, George Tripp Substation 138 kV 138kV +10, Arnott Substation 138 kV 138kV +10, Dow Chemical Substation 138 kV 138kV gen bus +10, Substation 401121457 144 kV 138kV +10, Substation 401121462 144 kV 138kV +10, Riverview Substation 240 kV 230kV +10, Poundmaker Substation 240 kV 230kV +10, North Calder Substation 240 kV 230kV +10, Lynn Valley Substation 230 kV 230kV +10, High River Substation 138 kV 138kV +10, Skeena Substation 500 kV 500kV +20, Tee 230 kV t230_14 230kV +20, Tee 230 kV t230_11 230kV +20, Tee 230 kV t230_6 230kV +20, East Camrose Substation 138 kV 138kV +20, Summit Substation 138 kV 138kV gen bus +20, Hill 144 kV 138kV +20, Mount Lehman Substation 230 kV 230kV gen bus +20, Clover Bar Substation 138 kV 138kV gen bus +20, Substation 159946156 138 kV 138kV gen bus +20, Scotford Upgrader Substation 138 kV 138kV gen bus +20, Tee 230 kV t230_18 230kV +20, Black Diamond 138 kV 138kV +30, Steveston Substation 230 kV 230kV +30, Tee 230 kV t230_13 230kV +30, Substation No. 28 138 kV 138kV +30, Harewood West Substation 230 kV 230kV +30, East Industrial Substation 240 kV 230kV +30, Argyll Substation 240 kV 230kV +30, Cochrane Substation 138 kV 138kV +40, Gaetz Substation 240 kV 230kV gen bus +40, Arnott Substation 230 kV 230kV +40, Bear Mountain Terminal 230 kV 230kV +40, East Calgary Substation 138 kV 138kV +50, Substation 2 138 kV 138kV +50, Substation 162 240 kV 230kV gen bus +60, Valley View Substation 230 kV 230kV +60, Harry Smith Substation 240 kV 230kV +60, McLellan Substation 230 kV 230kV +60, Meridian Substation 500 kV 500kV gen bus +60, Barnard Substation 230 kV 230kV +60, Tee 230 kV t230_7 230kV +70, Kidd #2 Substation 230 kV 230kV +70, Tee 240 kV t240_32 230kV +70, North Fraser Bank Cable Terminal 230 kV 230kV +70, Cambie Substation 230 kV 230kV +70, Walters Substation 230 kV 230kV +70, Fleetwood Substation 230 kV 230kV +70, Keating Substation 230 kV 230kV +80, South Fraser Bank Cable Terminal 230 kV 230kV +80, Aurum Substation 240 kV 230kV +80, Lambton Substation 240 kV 230kV +80, Hill Avenue Terminal Station 230 kV 230kV +90, Jasper Substation 240 kV 230kV +90, Goward Substation 138 kV 138kV +90, Boundary Rectifier Station 230 kV 230kV +100, Horne Payne Substation 230 kV 230kV +100, Goward Substation 230 kV 230kV +100, Castle Downs Substation 240 kV 230kV +100, Kidd #1 Substation 230 kV 230kV +110, Knight Rectifier Station 230 kV 230kV +110, Pike Lake Substation 230 kV 230kV +110, Substation 162 240 kV 230kV +110, Newell Substation 230 kV 230kV +120, Oakridge Rectifier Station 230 kV 230kV +140, Substation No. 25 240 kV 230kV gen bus +150, Substation 1241245610 230 kV 230kV +160, Bellamy Substation 240 kV 230kV +210, Victoria Substation 240 kV 230kV +260, Sarcee Substation 240 kV 230kV +360, East Calgary Substation 240 kV 230kV +750

## Round history

- r1: first build (owner's build-first instruction: r1 only). Reactive repair by fixed bus shunts only; no radial-chain demand relief; no value changed after a solver symptom.
- r2: loss accounting. The snapshot demand figures (Hydro-Quebec hourly demand; AESO Alberta Internal Load; BC Hydro balancing-authority load) are generation plus net interchange, so they already CONTAIN the transmission losses; r1 put the whole figure on the buses and dispatched plant to it, so the slack alone met the solved losses (Quebec 2,352.329 MW: slack GSU at Chateauguay 195.5 %; West 913.327 MW). The population demand rows are now scaled by (D - L) / D with L the r1 gridsim pf loss of the same system (estimated; [VERIFY] that the HQ open-data series includes losses). West: the West-only build rules are now in the West fit register.
- r3 (West only): the r2 attempt did not converge (folder kept as canada-west-spine-500-240-138-r2): with 4 % less demand the first full-snapshot solve converged onto a poor state (Vmin 0.7851, Vmax 1.2978 pu), the one-stage repair stalled at pass 3 and the staged route never ran.: on a one-stage stall the shunts are discarded and the staged route runs (procedure only; same loss accounting as r2).
- SEASONAL RATINGS (owner rule 2026-11-01): every overhead line's ASTM 25 C-ambient rating x the JAO median seasonal ratio for the snapshot month: Quebec (Feb) and West (Dec) winter x 1.0415, Ontario (Jun) summer x 0.9439; derived, [VERIFY]. No other change.

## Values set after a solver symptom (brief: no fitting to the solver)

- build: line-end shunt reactors, 70 % of the charging of every line at 500 kV and above (added in r1 after the first no-limit Newton showed Vmax 1.76 pu at 0.5 x snapshot from 12,300 km of 735 kV line charging). Basis: physical rule (long EHV lines are built with shunt reactors; Hydro-Quebec's 735 kV lines have them); the 70 % is a typical figure, NOT a cited Hydro-Quebec value. Tagged synthetic [VERIFY].
- topology: series compensation, 40 % of the reactance of every 735 kV line of 150 km or more (r1, after the no-limit Newton collapsed at 0.45 x snapshot with a 64 deg angle spread at 0.4 x). Basis: physical fact (Hydro-Quebec's long 735 kV lines carry series capacitors); the 40 % and the 150 km are typical figures, NOT cited HQ values. Tagged synthetic in the line notes [VERIFY].
- build: one SVC (+/-300 MVAr, 1.0 pu, P = 0) at every 735 kV station bus (r1, after a continuation solve collapsed at 0.69 x snapshot with 80 deg across the system). Basis: physical fact (Hydro-Quebec operates SVCs and synchronous condensers on its 735 kV corridors); sites and the 300 MVAr are NOT sourced. Synthetic [VERIFY].
- topology: synthetic coupling units sized to the LV-side line rating at the bus (2 to 4 units by HV class; Norway rule; r1, after the 735/315 kV couplings round Montreal showed 186 - 199 % in a DC check). Physical rule, estimated.
- electrify: population of a place goes to the stations of 230 kV and above within 20 km when there are any (Norway r2 rule, which used the top voltages 300 / 420 kV), and to the nearest such station when no station lies within 20 km (r1, before the first AC solve, after a DC check showed Montreal's 120 kV network carrying the city load). Physical rule: OSM lacks most city cable networks. Estimated.
- electrify (West only): demand allocated per province with its own published total (Alberta 12,785 MW AESO AIL; BC 9,597 MW BC Hydro BA load) instead of one MW-per-person figure for the system. Basis: published totals; estimated.
- electrify (West only): NACEI 2017 Alberta coal units relabelled gas (AESO 2025 Annual Market Statistics lists no coal capacity); unit capacities kept as NACEI gives them [VERIFY].
- electrify (West only): NACEI plants more than 50 km from any kept bus left out (Kemano 896 MW, Forrest Kerr 195 MW, Bighorn 120 MW): their connection is not in the kept OSM island. Set after r1 attempts did not converge with them on distant buses. Estimated [VERIFY].
- build (West only): 5 buses per reactive-repair pass (WORST_PER_PASS) instead of 20, set after two non-converging r1 attempts (repair algorithm setting, no network value).

## Known gaps

- Large industrial loads (aluminium smelters, pulp and paper, mines, oil sands) are not placed separately: demand is allocated by population only.
- Plants are NACEI 2017 (>= 100 MW) plus OSM plants with an output tag; newer or small plants without an OSM output tag are missing; plants far from any kept bus (OSM lacks their radial line) sit on the nearest bus.
- Line parameters are typical per-km values by voltage class; circuit counts are OSM's (a double-circuit line drawn once with no circuits tag counts once); series compensation (735 kV) is not modelled.
- No open reactive compensation list: the bus shunts are fixed repairs.
- Neighbouring systems are fixed injections at the nearest kept bus; no fault infeed from abroad.
- Dispatch is pro rata to capacity within fuel groups (no unit-level open data at the snapshot).
- Demand: allocated load = published demand (it includes losses; the slack adds the modelled losses).

## Sources

- OpenStreetMap power layer (lines, substations, plants >= 100 kV), Geofabrik provincial extracts 2026-10-30, via the shared the build pipeline OSM ingest and adapt_osm (OpenStreetMap contributors), ODbL 1.0
- Power Plants, 100 MW or more, North America (2017-08) (North American Cooperation on Energy Information (Natural Resources Canada)), Open Government Licence - Canada
- EIA-930 hourly interchange (six-month files) (U.S. Energy Information Administration), public domain (U.S. Government work)
- GeoNames cities1000 (Canadian places, population, position) (GeoNames), CC BY 4.0
- Per-km line parameters: 735 kV from the OPAL-RT HYPERSIM constant-parameter line example of a Hydro-Quebec 735 kV line; other classes from ACSR conductor data and typical geometry (GMR / GMD derivation copied from the the build pipeline ERCOT build) (OPAL-RT / the build pipeline), public documentation (cited values) / private derivation
- Model assembly steps: converter removal, island selection, couplings, GSUs, placement, dispatch, demand allocation, boundary injections, slack, repairs (a private build pipeline using GridSim's solver), private
- Natural Earth 1:10m admin-0 / admin-1, public domain: outline and provinces in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf canada-west-spine-500-240-138-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.9 s)
Power flow - Canada West 500-345-230-161-138 kV 2025-12-11 (UnvalidatedAtScale) (1371 buses)
  converged in 8 iteration(s), mismatch 2.98E-009 pu   losses 752.924 MW / -1009.370 MVAr
  voltage range 0.9491 - 1.0223 pu
  lowest voltages:
      bus 64     0.9491 pu    -44.028 deg
      bus 612    0.9492 pu    -44.839 deg
      bus 183    0.9493 pu    -43.487 deg
      bus 292    0.9493 pu    -31.683 deg
      bus 141    0.9493 pu    -44.177 deg
      bus 184    0.9494 pu    -43.548 deg
      bus 191    0.9494 pu    -50.557 deg
      bus 617    0.9495 pu    -48.732 deg
      bus 1032   0.9495 pu    -47.266 deg
      bus 74     0.9495 pu    -44.595 deg
      bus 254    0.9495 pu    -52.177 deg
      bus 1033   0.9495 pu    -49.535 deg
(warm start baked into buses.json from that solve: that start took 8 Newton iterations)
(the build pipeline reading of the pf result) angle spread 54.891 deg; branches over 100 %: 54, over 80 %: 98; highest: L00386 (Tee 138 kV t138_81 138kV - Tee 138 kV t138_97 138kV) 490.1 %; L01437 (Tee 138 kV t138_101 138kV - Bear Mountain Terminal 138 kV 138kV) 311.2 %; L00171 (Tee 138 kV t138_30 138kV - Tee 138 kV t138_36 138kV) 252.7 %; L00113 (Tee 138 kV t138_26 138kV - Sarcee Substation 138 kV 138kV) 240.5 %; L00103 (Tee 138 kV t138_14 138kV - Tee 138 kV t138_21 138kV) 238.2 %; L00105 (Tee 138 kV t138_21 138kV - Tee 138 kV t138_22 138kV) 235.8 %; L00104 (Tee 138 kV t138_21 138kV - Tee 138 kV t138_22 138kV) 235.8 %; L00106 (Tee 138 kV t138_22 138kV - Tee 138 kV t138_23 138kV) 221.2 %
$ gridsim pf canada-west-spine-500-240-138-r4 (warm start)   (exit 0, 0.6 s)
Power flow - Canada West 500-345-230-161-138 kV 2025-12-11 (UnvalidatedAtScale) (1371 buses)
  converged in 4 iteration(s), mismatch 2.98E-009 pu   losses 752.924 MW / -1009.370 MVAr
  voltage range 0.9491 - 1.0223 pu
  lowest voltages:
      bus 64     0.9491 pu    -44.028 deg
      bus 612    0.9492 pu    -44.839 deg
      bus 183    0.9493 pu    -43.487 deg
      bus 292    0.9493 pu    -31.683 deg
      bus 141    0.9493 pu    -44.177 deg
      bus 184    0.9494 pu    -43.548 deg
      bus 191    0.9494 pu    -50.557 deg
      bus 617    0.9495 pu    -48.732 deg
      bus 1032   0.9495 pu    -47.266 deg
      bus 74     0.9495 pu    -44.595 deg
      bus 254    0.9495 pu    -52.177 deg
      bus 1033   0.9495 pu    -49.535 deg
$ gridsim physics-check canada-west-spine-500-240-138-r4   (exit 0, 0.8 s)
Physics-law audit  -  canada-west-spine-500-240-138-r4  (1371 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.38E-010 | MW | independent dissipation 752.924307 MW (branch 752.9243 + shunt -0.0000) vs reported loss 752.924307 MW |
| 2 | Ohm's law | Holds | 5.01E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.64E-010 | MW | total network loss 752.924307 MW vs reported 752.924307 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.68E-008 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.98E-007 | MVA | same residual as law 6, reactive component included at 1315 PQ bus(es), by the bus types the solve ended with; 2 of them declared PV and solved as PQ (2 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 60 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses canada-west-spine-500-240-138-r4   (exit 0, 33.8 s)
(full sweep in iec60909_all_buses.txt) 500 kV (43): Ik'' max 43.03 kA (Ellerslie Substation 500 kV 500kV), min 1.81 kA (Skeena Substation 500 kV 500kV), median 15.65 kA; 345 kV (6): Ik'' max 13.32 kA (Upper Harrison Terminal 360 kV 345kV), min 7.27 kA (Wahleach Substation 360 kV 345kV), median 10.56 kA; 230 kV (249): Ik'' max 78.75 kA (Ellerslie Substation 240 kV 230kV), min 1.00 kA (Substation 753730282 230 kV 230kV), median 16.06 kA; 161 kV (5): Ik'' max 11.43 kA (Substation 753523016 161 kV 161kV), min 4.44 kA (Substation 753569578 161 kV 161kV), median 4.83 kA; 138 kV (636): Ik'' max 110.73 kA (East Edmonton Substation 138 kV 138kV), min 0.79 kA (Blumenort 144 kV 138kV), median 12.07 kA
```
