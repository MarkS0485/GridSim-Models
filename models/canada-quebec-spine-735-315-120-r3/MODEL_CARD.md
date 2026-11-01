# MODEL CARD: Canada Quebec 735-315-230-161-115 kV 2023-02-03 (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against operator study results. A solvable rough map of the Quebec Interconnection (Hydro-Quebec TransEnergie: 735 / 315 / 230 / 161 / 120 kV) for one snapshot: OSM-mapped lines and stations (>= 100 kV), standard per-km parameters, NACEI / OSM plants, published system demand allocated by population. Use it to learn, compare and explore, not to plan or operate.

Round: r3. Frequency 60 Hz. Neighbouring systems are fixed boundary injections.

## What it is

- Snapshot: 2023-02-03 18:00 EST (hour ending), Quebec's record winter peak hour (published demand 42472.83 MW).
- Buses 843 (39 generator terminal buses, 350 tee buses), branches 1175 (lines 1061, transformers 114), generators 120.
- Buses by kV: 735 kV 37, 315 kV 176, 230 kV 123, 161 kV 118, 115 kV 350, 13.8 kV 39.
- Dispatch 36320.2 MW (in-system plant) + boundary imports 6960.7 MW; demand 40928.5 MW (incl. boundary exports 808.0 MW).
- Slack: 1 reference: Beauharnois.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 843 | 454 (53.9%) | 0 (0.0%) | 350 (41.5%) | 39 (4.6%) |
| Branches | 1175 | 0 (0.0%) | 1061 (90.3%) | 0 (0.0%) | 114 (9.7%) |
| Generators | 120 | 74 (61.7%) | 0 (0.0%) | 11 (9.2%) | 35 (29.2%) |
| Demand points | 278 | 0 (0.0%) | 0 (0.0%) | 278 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 97 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 97 (100.0%) |

Tag mapping: attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OSM via adapt_osm (CA_QC): CA_QC: 620 sites, 1271 branches, 1001 buses, 63 couplings, 184 branches dropped at a free end, 12 HVDC ways left out.
- HVDC converter sites (OSM substation=converter): 6; their AC buses removed: ['sw303543538_315'] (ties are boundary injections).
- Islands 18, sizes [804, 69, 58, 18, 10, 5, 5, 4, 4, 4]; main island kept (804 buses, 350 tees); by kV {'161': 118, '115': 350, '735': 37, '230': 123, '315': 176}; route km {'735': 12304.8, '315': 4465.4, '230': 2372.5, '161': 1915.0, '115': 3640.1}; 217 lines floored to 0.5 km.
- Largest dropped islands: 69 buses near 45.704, -75.602 (Substation 1312956008 120 kV); 58 buses near 48.06, -78.237 (Poste de la Mine-Casa-Berardi 120 kV); 18 buses near 45.851, -74.258 (Substation 1064918047 120 kV); 10 buses near 48.965, -64.663 (Poste de Grande-Vallee 161 kV); 5 buses near 45.28, -74.122 (Substation 125704539 230 kV); 5 buses near 54.305, -71.914 (Poste Laforge-1 315 kV).
- Per-km parameters: 735 kV R 0.0117 X 0.3273 ohm/km B 5.061 uS/km, 6620 MVA (Quad 1355 kcmil ACSR (HQ 735 kV, OPAL-RT HYPERSIM example)); 500 kV R 0.0242 X 0.3493 ohm/km B 4.604 uS/km, 2572 MVA (Triple Rail 954 kcmil 45/7 ACSR); 345 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1183 MVA (Twin Rail 954 kcmil 45/7 ACSR); 315 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1080 MVA (Twin Rail 954 kcmil 45/7 ACSR); 230 kV R 0.0432 X 0.3623 ohm/km B 4.462 uS/km, 723 MVA (Twin Drake 795 kcmil 26/7 ACSR); 161 kV R 0.0864 X 0.4761 ohm/km B 3.436 uS/km, 253 MVA (Drake 795 kcmil 26/7 ACSR); 138 kV R 0.0864 X 0.4647 ohm/km B 3.523 uS/km, 217 MVA (Drake 795 kcmil 26/7 ACSR); 115 kV R 0.0864 X 0.4593 ohm/km B 3.566 uS/km, 181 MVA (Drake 795 kcmil 26/7 ACSR).
- Couplings: 75 synthetic transformers at OSM sites with two voltages, 2 units by HV class (735: 1650, 500: 750, 345 / 315: 600, 230: 300, below: 150 MVA each), x 12 % own rating.

## Generation and dispatch by fuel (MW)

| Fuel | Generators | Capacity in case | Dispatch |
|---|---:|---:|---:|
| biomass | 1 | 28.0 | 24.8 |
| gas | 2 | 918.0 | 812.1 |
| hydro | 54 | 39127.2 | 34612.4 |
| interconnector | 3 | 6960.7 | 6960.7 |
| wind | 25 | 2903.2 | 870.9 |

## Boundary injections (MW, + import)

| Tie | MW | Bus | Source |
|---|---:|---|---|
| New York (Chateauguay back-to-back) | 1101.0 | Poste de Chateauguay 315 kV (7.6 km) | EIA-930 interchange NYIS -> HQT, hour ending 2023-02-03 18:00 EST: +1,101 MW (NYIS export) |
| New England (Phase II HVDC, rectifier at Radisson; Highgate and Phase I at Des Cantons not split out) | -808.0 | Poste Radisson 735 kV (0.6 km) | EIA-930 interchange ISNE -> HQT, same hour: -808 MW (ISNE import from HQ); withdrawn at Radisson, the Phase II rectifier (Radisson - Nicolet - Sandy Pond multi-terminal HVDC), estimated [VERIFY] the split between Phase II and the Highgate / Des Cantons ties |
| Ontario (Outaouais back-to-back, IESO intertie PQ.AT) | 1058.0 | Poste du Grand-Brule 735 kV (99.6 km) | IESO PUB_IntertieScheduleFlowYear_2023, PQ.AT flow at 2023-02-03 hour 18 EST (+ = Ontario export, i.e. import into Quebec; the IESO Total column is Exp - Imp) |
| New Brunswick (Madawaska back-to-back, Eel River) | 0.0 | Poste de Degelis 120 kV (24.5 km) | no open hourly NB - Quebec flow found: 0 MW assumed [VERIFY] |
| Churchill Falls (Labrador, 735 kV, synchronous with Quebec) | 4801.7 | Poste des Montagnais 735 kV (217.2 km) | NACEI Churchill Falls capacity (Newfoundland and Labrador row); output at the Quebec hydro dispatch share (estimated, [VERIFY]) |

## Repairs (every change made so the case solves)

- seasonal line ratings: all 1061 overhead lines x 1.0415 (seasonal factor 1.0415 = JAO ratio winter 1.1034 / base 'interseason' 1.0594 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- synchronous plants of 20 MW or more behind 39 lumped GSUs (44526 MVA, x 13 % own rating, X/R 40, terminal 13.8 kV; synthetic), role pv at 1.02 pu, Q range -0.3 to +0.48 x MW (estimated); wind, solar, small plants and boundary imports pq with Q = 0
- 35 synthetic SVCs (+/-300 MVAr, set point 1.0 pu, P = 0) at every station bus of 700 kV and above (physical rule; sizes estimated) [VERIFY]
- slack: largest dispatched unit within 150 km of the demand centre (46.01, -73.04): Beauharnois at Poste de Chateauguay 735 kV 735kV gen bus, reactive band +/-10428 MVAr (synthetic)
- loss accounting: the snapshot demand figure includes transmission losses; population demand 42472.8 MW scaled by 0.944616 (L = 2352.329 MW, the r1 gridsim pf loss; estimated)
- no radial-chain demand relief (India routine not used:
- line-end shunt reactors on 79 lines at 500 kV and above: 70% of each line's charging, 23551 MVAr in all, as fixed bus shunts at the two ends (physical rule; sizes estimated, synthetic) [VERIFY]
- bus shunts placed where the snapshot needs reactive support (13 passes of a Newton solve without reactive limits): 11 reactors 1520 MVAr, 78 capacitors 28670 MVAr (synthetic; no open reactive compensation list; 735 kV systems run large shunt reactors and SVCs / synchronous condensers): Poste LG-2 735 kV 735kV -760, Poste Tilly 735 kV 735kV -290, Poste des Montagnais 735 kV 735kV -120, Poste Parc Eolien du Lac-Alfred 315 kV 315kV -60, Substation 774866881 315 kV 315kV -60, Tee 315 kV t315_100 315kV -60, Poste de Chissibi 735 kV 735kV -60, Poste Rimouski 315 kV 315kV -50, Matapedia 315 kV 315kV -30, Poste Natashquan 161 kV 161kV -20, Poste de Gros-Morne 230 kV 230kV -10, Poste de Provost 120 kV 115kV +10, Poste Laurendeau 120 kV 115kV +10, Poste de Sainte-Emelie 120 kV 115kV +10, Tee 120 kV t120_103 115kV +10, Tee 120 kV t120_95 115kV +10, Tee 120 kV t120_87 115kV +10, Tee 120 kV t120_102 115kV +10, Poste Ramezay 120 kV 115kV +10, Tee 120 kV t120_104 115kV +10, Poste de Sainte-Rosalie 120 kV 115kV +10, Poste de Kildare 120 kV 115kV +10, Tee 120 kV t120_126 115kV +10, Poste de Vaudreuil-Soulanges 120 kV 115kV +10, Tee 120 kV t120_39 115kV +10, Tee 120 kV t120_53 115kV +10, Tee 315 kV t315_24 315kV +20, Poste des Bois-Franc 120 kV 115kV +20, Substation 669500209 120 kV 115kV +20, Tee 120 kV t120_153 115kV +20, Poste de Plessisville 120 kV 115kV +20, Poste de Stanstead 120 kV 115kV +20, Poste des Cedres 120 kV 115kV gen bus +20, Poste de Coaticook 120 kV 115kV +20, Tee 120 kV t120_142 115kV +20, Poste d'Hydro-Magog 120 kV 115kV +20, Poste d'EKA Chimie 120 kV 115kV +20, Poste de Messer Canada 120 kV 115kV +20, Tee 120 kV t120_141 115kV +20, Poste Baie-d'Urfe 120 kV 115kV +30, Poste Saint-Jean 120 kV 115kV +30, Poste Micmac 230 kV 230kV +40, Poste de Magnan 120 kV 115kV +40, Poste Casavant 120 kV 115kV +40, Poste de Lanaudiere 315 kV 315kV +50, Poste Monteregie 735 kV 735kV +80, Tee 315 kV t315_17 315kV +80, Tee 315 kV t315_10 315kV +80, Tee 315 kV t315_8 315kV +80, Poste du Saguenay 735 kV 735kV +90, Poste Des Cantons 735 kV 735kV +90, Poste des Patriotes 315 kV 315kV +100, Poste de Saraguay 315 kV 315kV +100, Poste Micoua 735 kV 735kV +130, Tee 315 kV t315_18 315kV +140, Poste Chenier 735 kV 735kV +160, Poste Arnaud 735 kV 735kV +170, Tee 315 kV t315_7 315kV +170, Poste de l'Aqueduc 315 kV 315kV +200, Poste Manicouagan 735 kV 735kV +230, Poste Chibougamau 735 kV 735kV +240, Poste des Sources 315 kV 315kV +280, Poste Viger 315 kV 315kV +290, Poste de Blainville 315 kV 315kV +310, Poste Charland 315 kV 315kV +320, Poste Fleury 315 kV 315kV +340, Hydro-Quebec - Poste Roll-Royce 315 kV 315kV +350, Poste Atwater 315 kV 315kV +350, Poste Saint-Jean 315 kV 315kV +360, Poste Belanger 315 kV 315kV +370, Poste Albanel 735 kV 735kV +380, Poste Saint-Patrick 315 kV 315kV +400, Poste de Rosemont 315 kV 315kV +430, Poste de Bergeronnes 735 kV 735kV +560, Poste Nicolet 735 kV 735kV +650, Poste du Grand-Brule 735 kV 735kV +660, Poste Carignan 735 kV 735kV +670, Poste de la Chamouchouane 735 kV 735kV +720, Poste Nemiscau 735 kV 735kV +800, Poste Judith-Jasmin 735 kV 735kV +820, Poste des Laurentides 735 kV 735kV +880, Poste de Levis 735 kV 735kV +1100, Poste Abitibi 735 kV 735kV +1190, Poste La Verendrye 735 kV 735kV +1240, Poste de la Jacques-Cartier 735 kV 735kV +1560, Poste de Boucherville 735 kV 735kV +2010, Poste du Bout-de-l'Ile 735 kV 735kV +2510, Poste Hertel 735 kV 735kV +2700, Poste de Duvernay 735 kV 735kV +3640

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
- Historique de la demande d'electricite au Quebec, 2023 (hourly) (Hydro-Quebec), CC BY-NC 4.0
- IESO public reports: hourly demand, generator output by fuel, intertie schedule and flow (Independent Electricity System Operator (Ontario)), IESO public reports (terms of use, ieso.ca)
- EIA-930 hourly interchange (six-month files) (U.S. Energy Information Administration), public domain (U.S. Government work)
- GeoNames cities1000 (Canadian places, population, position) (GeoNames), CC BY 4.0
- Per-km line parameters: 735 kV from the OPAL-RT HYPERSIM constant-parameter line example of a Hydro-Quebec 735 kV line; other classes from ACSR conductor data and typical geometry (GMR / GMD derivation copied from the the build pipeline ERCOT build) (OPAL-RT / the build pipeline), public documentation (cited values) / private derivation
- Model assembly steps: converter removal, island selection, couplings, GSUs, placement, dispatch, demand allocation, boundary injections, slack, repairs (a private build pipeline using GridSim's solver), private
- Natural Earth 1:10m admin-0 / admin-1, public domain: outline and provinces in geography.json.

Licence: pending a licence check (see ATTRIBUTION.txt and LICENSING.md).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf canada-quebec-spine-735-315-120-r3   (flat start: vm 1, vaDeg 0; exit 0, 0.6 s)
Power flow - Canada Quebec 735-315-230-161-115 kV 2023-02-03 (UnvalidatedAtScale) (843 buses)
  converged in 10 iteration(s), mismatch 3.75E-012 pu   losses 2299.398 MW / -2555.315 MVAr
  voltage range 0.9502 - 1.0503 pu
  lowest voltages:
      bus 525    0.9502 pu    -19.220 deg
      bus 564    0.9503 pu    -13.116 deg
      bus 118    0.9510 pu    -23.563 deg
      bus 484    0.9511 pu    -20.990 deg
      bus 524    0.9511 pu    -20.990 deg
      bus 38     0.9511 pu    -22.575 deg
      bus 106    0.9512 pu    -22.572 deg
      bus 500    0.9512 pu    -22.413 deg
      bus 85     0.9512 pu    -22.528 deg
      bus 91     0.9513 pu    -17.119 deg
      bus 456    0.9514 pu    -22.345 deg
      bus 559    0.9517 pu    -13.126 deg
(warm start baked into buses.json from that solve: that start took 10 Newton iterations)
(the build pipeline reading of the pf result) angle spread 125.855 deg; branches over 100 %: 36, over 80 %: 92; highest: L01005 (Tee 315 kV t315_22 315kV - Poste du Bout-de-l'Ile 315 kV 315kV) 209.7 %; L00134 (Tee 120 kV t120_47 115kV - Poste de Rigaud 120 kV 115kV) 209.1 %; L00135 (Tee 120 kV t120_47 115kV - Poste de Vaudreuil-Soulanges 120 kV 115kV) 207.6 %; L00149 (Poste de Vaudreuil-Soulanges 120 kV 115kV - Tee 120 kV t120_53 115kV) 198.1 %; L00167 (Tee 120 kV t120_62 115kV - Tee 120 kV t120_63 115kV) 197.4 %; L00985 (Tee 315 kV t315_18 315kV - Poste Belanger 315 kV 315kV) 193.0 %; L00994 (Tee 315 kV t315_20 315kV - Tee 315 kV t315_22 315kV) 183.7 %; L00988 (Tee 315 kV t315_19 315kV - Tee 315 kV t315_20 315kV) 183.0 %
$ gridsim pf canada-quebec-spine-735-315-120-r3 (warm start)   (exit 0, 0.5 s)
Power flow - Canada Quebec 735-315-230-161-115 kV 2023-02-03 (UnvalidatedAtScale) (843 buses)
  converged in 4 iteration(s), mismatch 5.58E-012 pu   losses 2299.398 MW / -2555.315 MVAr
  voltage range 0.9502 - 1.0503 pu
  lowest voltages:
      bus 525    0.9502 pu    -19.220 deg
      bus 564    0.9503 pu    -13.116 deg
      bus 118    0.9510 pu    -23.563 deg
      bus 484    0.9511 pu    -20.990 deg
      bus 524    0.9511 pu    -20.990 deg
      bus 38     0.9511 pu    -22.575 deg
      bus 106    0.9512 pu    -22.572 deg
      bus 500    0.9512 pu    -22.413 deg
      bus 85     0.9512 pu    -22.528 deg
      bus 91     0.9513 pu    -17.119 deg
      bus 456    0.9514 pu    -22.345 deg
      bus 559    0.9517 pu    -13.126 deg
$ gridsim physics-check canada-quebec-spine-735-315-120-r3   (exit 0, 0.5 s)
Physics-law audit  -  canada-quebec-spine-735-315-120-r3  (843 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 3.37E-010 | MW | independent dissipation 2299.397986 MW (branch 2299.3980 + shunt 0.0000) vs reported loss 2299.397986 MW |
| 2 | Ohm's law | Holds | 2.63E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 3.29E-010 | MW | total network loss 2299.397986 MW vs reported 2299.397986 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 5.00E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 8.05E-010 | MVA | same residual as law 6, reactive component included at 771 PQ bus(es), by the bus types the solve ended with; 2 of them declared PV and solved as PQ (2 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 60 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses canada-quebec-spine-735-315-120-r3   (exit 0, 5.0 s)
(full sweep in iec60909_all_buses.txt) 735 kV (35): Ik'' max 42.89 kA (Poste LG-2 735 kV 735kV), min 13.03 kA (Poste des Montagnais 735 kV 735kV), median 26.81 kA; 315 kV (84): Ik'' max 59.55 kA (Poste des Laurentides 315 kV 315kV), min 2.31 kA (Poste La Romaine-3 315 kV 315kV), median 31.29 kA; 230 kV (63): Ik'' max 55.85 kA (Poste Nicolet 230 kV 230kV), min 3.63 kA (Poste Micmac 230 kV 230kV), median 17.97 kA; 161 kV (66): Ik'' max 84.49 kA (Poste du Saguenay 161 kV 161kV), min 0.67 kA (Poste Natashquan 161 kV 161kV), median 16.70 kA; 115 kV (206): Ik'' max 90.85 kA (Poste Judith-Jasmin 120 kV 115kV), min 2.20 kA (Poste de Provost 120 kV 115kV), median 14.07 kA
```
