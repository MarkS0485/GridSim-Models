# MODEL CARD: Japan east 50 Hz transmission 500/275/220/154/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official Japanese study results. A solvable rough map of the Japan east 50 Hz (Tohoku and Tokyo areas; Hokkaido behind its HVDC injections) (500, 275, 220, 154, 66 kV) for one snapshot: OpenStreetMap topology with typical per-km line parameters, synthetic transformers, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r6.

## What it is

- Snapshot: 2025-01-15 18:00-18:30 JST (Wednesday, winter evening).
- Buses 4551 (133 generator buses), branches 5765 (lines 5349, transformers 416), generators 231.
- Buses by kV: 500 kV 99, 275 kV 231, 220 kV 2, 154 kV 643, 66 kV 3443, 20 kV 133.
- Dispatch 53692.0 MW (incl. HVDC imports 104.0 MW); demand 52030.4 MW (incl. HVDC sending ends 1471.0 MW).
- Slack: 1 reference: Futtsu.
- HVDC and frequency converters: Shin-Shinano FC: 420.3 MW east -> west (50 Hz side at by OSM name (??????, 500 kV, 5.4 km from the listed position)); Sakuma FC: 210.1 MW east -> west (50 Hz side at by nearness (Substation 618344827, 275 kV, 0.6 km)); Higashi-Shimizu FC: 210.1 MW east -> west (50 Hz side at by OSM name (??????, 154 kV, 2.7 km from the listed position)); Hida-Shinano HVDC (Hida converter, 60 Hz side) / Shin-Shinano (50 Hz side): 630.4 MW east -> west (50 Hz side at by OSM name (??????, 500 kV, 5.4 km from the listed position)); Kitahon HVDC (Kamikita terminal): 69.3 MW Hokkaido -> Honshu (terminal by OSM name (?????, 275 kV, 3.1 km from the listed position)); Hokuto-Imabetsu HVDC (Imabetsu terminal): 34.7 MW Hokkaido -> Honshu (terminal by OSM name (?????, 275 kV, 3.4 km from the listed position)) Hokkaido is NOT in the AC model: its HVDC links are fixed injections at the Honshu terminals.
- Islands before selection 20; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 4551 | 0 (0.0%) | 0 (0.0%) | 4418 (97.1%) | 133 (2.9%) |
| Branches | 5765 | 0 (0.0%) | 0 (0.0%) | 5482 (95.1%) | 283 (4.9%) |
| Generators | 231 | 0 (0.0%) | 0 (0.0%) | 231 (100.0%) | 0 (0.0%) |
| Demand points | 491 | 0 (0.0%) | 0 (0.0%) | 491 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 711 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 711 (100.0%) |

Buses are 'estimated' (positions and connectivity inferred from OSM drawings); lines are 'estimated' (drawn route length is OSM's, the per-km parameters are typical values); transformers are 'synthetic'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OpenStreetMap (Overpass, 2026-11-01) through the shared adapter a build step build_network: 4418 buses, 5349 lines, 283 couplings in this grid before island selection; cables 260.
- Converter couplings cut (frequency converters are not transformers): ['Anan Static Inverter Plant (????????)', 'Hida CS (?????)', 'Higashi-Shimizu Frequency Converter (??????)', 'Imabetsu CS (?????)', 'Kamikita CS (?????)', 'Kanzaki Substation (???? ?????)', 'Katagai SwS (?????)', 'Kihoku CS (?????)', 'Minamifukumitsurenkeitokoro (??????)', 'Nankan SS (?????)', 'Sakuma Frequency Converter Station (?????????)', 'Shin Shinano Frequency Converter Station (??????)', 'Substation 586398086 ()', 'Substation 607893570 ()', 'Substation 788177039 ()'].
- Islands over all Japan after the cut: 20 (largest [4405, 15, 14, 11, 8, 8, 7, 6, 5, 4]); the east grid is the island nearest central Tokyo, the west grid the one nearest central Osaka.
- OSM frequency tags that disagree with this grid: 0 ([]).
- Line kinds (count by kV and construction): {'154 cable': 8, '154 overhead': 793, '220 overhead': 1, '275 cable': 49, '275 overhead': 242, '500 cable': 27, '500 overhead': 106, '66 cable': 176, '66 overhead': 3947}.
- Line route km by kV (topology, before island selection): {'66': 11115.5, '154': 5575.9, '220': 5.4, '275': 3645.2, '500': 3104.4}.
- Adapter counts: {}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| coal | 14512.0 | 13819.0 |
| gas | 34384.9 | 33016.0 |
| geothermal | 278.0 | 158.0 |
| hydro | 14194.9 | 4524.0 |
| interconnector | 104.0 | 104.0 |
| nuclear | 825.0 | 791.0 |
| oil | 22757.2 | 1280.0 |

## Regions (MW)

| Area | Area demand (attested) | Modelled demand | Interchange (attested) |
|---|---:|---:|---:|
| tohoku | 13546.00 | 10836.6 | -5310.0 |
| tokyo | 41841.00 | 39722.8 | 3943.0 |

## Fitted and assumed values (the brief's NO FITTING TO THE SOLVER rule)

- ASSUMED (no source): line R / X / B and thermal ratings per circuit by voltage and construction (overhead {500: (0.012, 0.28, 4.1, 2600.0), 275: (0.03, 0.31, 3.7, 1300.0), 220: (0.05, 0.38, 3.0, 600.0), 187: (0.06, 0.39, 2.95, 450.0), 154: (0.07, 0.4, 2.9, 300.0), 132: (0.1, 0.4, 2.85, 180.0), 110: (0.12, 0.4, 2.85, 150.0), 77: (0.15, 0.4, 2.8, 100.0), 66: (0.17, 0.4, 2.8, 80.0)}; cable {500: (0.01, 0.12, 90.0, 1200.0), 275: (0.015, 0.12, 70.0, 900.0), 220: (0.02, 0.13, 60.0, 600.0), 187: (0.025, 0.13, 58.0, 450.0), 154: (0.03, 0.13, 55.0, 350.0), 132: (0.04, 0.13, 50.0, 200.0), 110: (0.05, 0.13, 45.0, 150.0), 77: (0.07, 0.13, 40.0, 100.0), 66: (0.08, 0.13, 40.0, 80.0)}; R ohm/km, X ohm/km, B uS/km, MVA).
- ASSUMED: coupling transformers x 12 % on own rating, X/R 40; size by a physical rule: 0.6 x the smaller side's line ratings, and at least 1.5 x the demand on the LV bus; clipped to 200-3000 MVA (assumed); floor 2 typical banks per voltage pair {500: {275: 1500.0, 220: 1000.0, 187: 1000.0, 154: 750.0, 0: 750.0}, 275: {154: 450.0, 0: 300.0}, 220: {0: 300.0}, 187: {0: 300.0}, 154: {0: 200.0}, 0: {0: 100.0}} (ASSUMED typical Japanese bank sizes, [VERIFY]).
- ASSUMED: GSU x 14.5 %, X/R 40; unit Q range -0.3 to 0.62 MVAr per MW; unit setpoint 1.02 pu; inertia H by fuel {'coal': 4.0, 'gas': 4.0, 'oil': 4.0, 'nuclear': 5.0, 'hydro': 3.0, 'geothermal': 2.0}.
- ASSUMED: transmission losses 3 % of area demand; load power factor 0.98; nuclear stations operating in January 2025 by the public restart record [VERIFY].
- ESTIMATED (rule, no fit): link flows from the attested area interchange balance split by link rating; link ratings are rounded public figures [VERIFY].
- PHYSICAL RULE: station export cap 0.85 x the station's network branch ratings; the excess goes to the grid's other synchronous units.
- SYNTHETIC REPAIR: every bus shunt (seed step, copied staged repair, reactive-limit trim).
- SOURCED: circuit counts from OpenStreetMap 'circuits' / 'cables' tags (ODbL); area demand and output by source from the utilities' area supply-demand results (attested).
- NOTE: the two-bank coupling floor was added after a DC diagnostic showed 200-360 MVA 500 kV couplings; it replaces the line-share size with typical unit sizes (an assumption to [VERIFY]), and no value was tuned to the solve. If review counts it as fitted, tag the couplings synthetic (they already are). No radial demand relief.

## Repairs (every change made so the case solves)

- winter line ratings (owner seasonal rule, tightened, rung 2): 5089 overhead lines x 1.1187 (median over 5 TSOs of OCCTO-published winter / summer tie-line thermal capacities, 2021; summer base 40 C [VERIFY]); cables static; transformers untouched; per line in ambient_ratings.json
- coupling transformers (synthetic): 283 units at sites with lines at two voltages, rating 0.6 x the smaller side's summed line ratings clipped to 200-3000 MVA (median 400 MVA), x 12 % own rating, X/R 40
- synchronous plant moved behind 133 lumped GSUs (102297 MVA, x 14.5 % own rating, X/R 40; estimated)
- station export cap at Substation 211412000 500kV: plant 3862 MW > 0.85 x network 2909 MVA (+ local demand); 1390 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 315461259 500kV: plant 4839 MW > 0.85 x network 2909 MVA (+ local demand); 2367 MW moved to east's other synchronous units (estimated)
- station export cap at Takanawa SS 275kV: plant 1154 MW > 0.85 x network 900 MVA (+ local demand); 389 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 1018771434 275kV: plant 2523 MW > 0.85 x network 1454 MVA (+ local demand); 1287 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 1027413725 275kV: plant 1904 MW > 0.85 x network 1454 MVA (+ local demand); 668 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 1028585766 275kV: plant 5291 MW > 0.85 x network 2354 MVA (+ local demand); 3289 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 704195148 275kV: plant 3149 MW > 0.85 x network 2909 MVA (+ local demand); 677 MW moved to east's other synchronous units (estimated)
- station export cap at Minamikawasaki SS 275kV: plant 8214 MW > 0.85 x network 1800 MVA (+ local demand); 6684 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 1133622351 154kV: plant 1917 MW > 0.85 x network 671 MVA (+ local demand); 1346 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 315461256 154kV: plant 288 MW > 0.85 x network 336 MVA (+ local demand); 3 MW moved to east's other synchronous units (estimated)
- station export cap at South Uonuma Substation 154kV: plant 898 MW > 0.85 x network 336 MVA (+ local demand); 612 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 519055295 154kV: plant 1367 MW > 0.85 x network 336 MVA (+ local demand); 1081 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 704399790 154kV: plant 1198 MW > 0.85 x network 336 MVA (+ local demand); 913 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 708298814 154kV: plant 667 MW > 0.85 x network 336 MVA (+ local demand); 381 MW moved to east's other synchronous units (estimated)
- station export cap at Ishihara Bayside Energy power station switchyard 66kV: plant 103 MW > 0.85 x network 89 MVA (+ local demand); 27 MW moved to east's other synchronous units (estimated)
- station export cap at Shiroyamasuiryoku PS switchyard 66kV: plant 225 MW > 0.85 x network 89 MVA (+ local demand); 149 MW moved to east's other synchronous units (estimated)
- station export cap at Kashima Minami Power Plant switchyard 66kV: plant 306 MW > 0.85 x network 89 MVA (+ local demand); 230 MW moved to east's other synchronous units (estimated)
- station export cap at South Tokamachi Substation 66kV: plant 159 MW > 0.85 x network 179 MVA (+ local demand); 7 MW moved to east's other synchronous units (estimated)
- station export cap at Hitachioomiya SS 66kV: plant 217 MW > 0.85 x network 80 MVA (+ local demand); 149 MW moved to east's other synchronous units (estimated)
- station export cap at Substation 638624993 66kV: plant 144 MW > 0.85 x network 89 MVA (+ local demand); 68 MW moved to east's other synchronous units (estimated)
- station export cap at Oohira SS 66kV: plant 142 MW > 0.85 x network 89 MVA (+ local demand); 66 MW moved to east's other synchronous units (estimated)
- slack: largest dispatched coal / gas station Futtsu at Substation 315461259 500kV gen bus, reactive band +/-29647 MVAr (synthetic)
- seed reactive step (build._seed_shunts): fixed shunts equal to the reactive power of a fictitious 1.02 pu voltage controller at every bus without a generator, where at least 10 MVAr: 527 capacitors 37140 MVAr, 182 reactors 9950 MVAr (synthetic)
- reactive trim with reactive limits (build._trim_qlim, 1 passes, ended: inside 0.95-1.05 pu): 0 reactor steps 0 MVAr, 0 capacitor steps 0 MVAr (synthetic): 
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 184 reactors 10020 MVAr, 527 capacitors 37090 MVAr (synthetic; OSM maps no reactive compensation). Largest 40: Arakikoutsu SS 500kV +1910, Minamikawasaki SS 154kV +980, Ikegami SS 275kV +920, Shin Sahara Hendensho 500kV +780, Higashi-Gunma Substation 275kV +640, Niigata Substation 275kV +610, Echigo SwS 275kV +540, Ikegami SS 66kV -480, Shiniwaki SwS 500kV -430, Substation 708227253 154kV +390, Bbsbs Substation 275kV +340, Yonezawa Substation 275kV +340, Kawasaki SS 154kV +330, Substation 225414665 66kV +320, Sankeo SS 500kV +290, Nerima SS 66kV +280, Iwate Substation 500kV -270, Naka Substation 275kV +260, Keihin SS 275kV +250, Shin Tochigi Hendensho 275kV +240, Wadahori SS 66kV +230, Tee 500 kV t500_2 500kV -230, Substation 1160171158 500kV -220, New Tokorozawa Substation 500kV +220, New Motegi Substation 275kV +220, North Niigata Substation 275kV +220, Tee 500 kV t500_1 500kV -210, Kitakatsushika SS 275kV +200, Musashisakaikouryuu SS 66kV +200, Tee 500 kV t500_3 500kV -190, New Fukushima Substation 275kV +190, Kita Tkita Tkykita Tky Hendensho 275kV +190, Arakikoutsu SS 275kV +190, Ishioka SS 154kV +190, Toda SS 154kV +190, Wadahori SS 154kV +190, Substation 1133622351 66kV +190, Tee 500 kV t500_6 500kV +180, Shinkyouha SS 275kV +180, Tsukada SS 66kV +180

## Round history (the solver's findings that drove each round)

- r1: first build; reactive repair by seed shunts (fictitious voltage control), the copied staged repair and a reactive-limit trim (all synthetic).

## Known gaps

- Line impedances and ratings are TYPICAL per-km values by voltage and construction, not the utilities' own [VERIFY]; circuit counts are OSM's tags (1 when untagged, so double-circuit routes drawn once are under-counted).
- Transformers are synthetic (one coupling per voltage pair per site, only where OSM gives evidence: a voltage tag on the site or a mapped transformer); taps and OLTCs are not modelled.
- No reactive compensation is mapped; the bus shunts are fixed repairs (synthetic).
- Plant register: WRI GPPD v1.3 (2021) placed by nearness; 34 rows (6922.6 MW, incl. Hokkaido and Okinawa) have no bus in reach and are left out; GPPD lists some units retired since 2021 and misses newer ones [VERIFY].
- Dispatch: each source's attested area output pooled over the grid and split pro rata to placed capacity; nuclear only at the stations operating in January 2025; solar, wind, biomass, batteries and 'other' netted off area demand as embedded generation.
- Demand: attested area demand x 0.97 (losses assumed 3 %) minus embedded generation, spread by GeoNames population to the nearest bus of 154 kV or below; power factor 0.98 (assumed).
- HVDC and frequency converters are fixed injections; flows from the area interchange balance split by link rating ([VERIFY] against OCCTO tie-line flow records).

## Sources

- OpenStreetMap power layer of Japan (lines and cables 66 kV and above, substations, transformers), Overpass API snapshot of 2026-11-01 (OpenStreetMap contributors), ODbL 1.0
- Area supply and demand results (eria jukyu jisseki), half-hourly, January 2025, of the nine general transmission and distribution companies (HEPCO NW, Tohoku EPCO NW, TEPCO PG, Chubu PG, Hokuriku EPCO TD, Kansai TD, Chugoku EPCO NW, Shikoku EPCO TD, Kyushu EPCO TD) (the general transmission and distribution companies (METI grid-information guidelines)), published for public information; reuse terms [VERIFY] before publication
- Global Power Plant Database v1.3.0 (2021), rows for Japan (World Resources Institute), CC BY 4.0
- GeoNames Japan populated places (JP.zip: population, position) (GeoNames), CC BY 4.0
- Public figures for link ratings (OCCTO tie-line capacities, rounded) and station positions ([VERIFY]) (OCCTO and the utilities), facts, no licence needed
- Model assembly steps: adapter run, grid split, per-km parameters, couplings, GSUs, dispatch split, demand allocation, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries JPN ADM1 (ODbL 1.0): outlines in geography.json.

Licence: pending a licence check (see ATTRIBUTION.txt and LICENSING.md).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf japan-east-spine-500-66-r6   (flat start: vm 1, vaDeg 0; exit 0, 1.2 s)
Power flow - Japan east 50 Hz transmission 500/275/220/154/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale) (4551 buses)
  converged in 7 iteration(s), mismatch 2.38E-010 pu   losses 2701.647 MW / -8529.356 MVAr
  voltage range 0.9757 - 1.0365 pu
  lowest voltages:
      bus 131    0.9757 pu    -70.698 deg
      bus 184    0.9757 pu    -70.699 deg
      bus 224    0.9764 pu    -70.703 deg
      bus 2339   0.9889 pu    -69.248 deg
      bus 2940   0.9964 pu    -58.578 deg
      bus 3029   0.9966 pu    -60.582 deg
      bus 1193   0.9966 pu    -60.582 deg
      bus 1192   0.9966 pu    -60.582 deg
      bus 1115   0.9972 pu    -65.991 deg
      bus 2518   0.9974 pu    -65.996 deg
      bus 3244   0.9984 pu    -49.440 deg
      bus 3231   0.9984 pu    -49.440 deg
(warm start baked into buses.json from that solve: flat start took 7 Newton iterations)
(the build pipeline PV/PQ complementarity check of the flat-start result: 0 unit bus(es) violate it)
(the build pipeline reading of the pf result) angle spread 108.700 deg; branches over 100 %: 168, over 80 %: 273; highest: OSM 66kV w1549902541 (Substation 225414665 66kV - Ikegami SS 66kV) 772.9 %; OSM 66kV w1549903483 (Tee 66 kV t66_646 66kV - Substation 225414665 66kV) 609.6 %; OSM 66kV w41956643 (Tairamachi SS 66kV - Tee 66 kV t66_646 66kV) 573.7 %; TX sw82104580 275/154kV (Minamikawasaki SS 275kV - Minamikawasaki SS 154kV) 521.4 %; OSM 66kV w35262643 (Wadahori SS 66kV - Substation 41955092 66kV) 515.2 %; OSM 66kV w762059409 (Katsuta SS 66kV - Substation 1321557847 66kV) 340.0 %; OSM 66kV w1081036320 (Tee 66 kV t66_1481 66kV - Jouban SS 66kV) 331.6 %; OSM 154kV w79291236 (Kawasaki SS 154kV - Minamikawasaki SS 154kV) 316.4 %
$ gridsim pf japan-east-spine-500-66-r6 (warm start)   (exit 0, 0.6 s)
Power flow - Japan east 50 Hz transmission 500/275/220/154/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale) (4551 buses)
  converged in 1 iteration(s), mismatch 2.38E-010 pu   losses 2701.647 MW / -8529.356 MVAr
  voltage range 0.9757 - 1.0365 pu
  lowest voltages:
      bus 131    0.9757 pu    -70.698 deg
      bus 184    0.9757 pu    -70.699 deg
      bus 224    0.9764 pu    -70.703 deg
      bus 2339   0.9889 pu    -69.248 deg
      bus 2940   0.9964 pu    -58.578 deg
      bus 3029   0.9966 pu    -60.582 deg
      bus 1193   0.9966 pu    -60.582 deg
      bus 1192   0.9966 pu    -60.582 deg
      bus 1115   0.9972 pu    -65.991 deg
      bus 2518   0.9974 pu    -65.996 deg
      bus 3244   0.9984 pu    -49.440 deg
      bus 3231   0.9984 pu    -49.440 deg
$ gridsim physics-check japan-east-spine-500-66-r6   (exit 0, 0.7 s)
Physics-law audit  -  japan-east-spine-500-66-r6  (4551 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 9.92E-009 | MW | independent dissipation 2701.646754 MW (branch 2701.6468 + shunt -0.0000) vs reported loss 2701.646754 MW |
| 2 | Ohm's law | Holds | 8.36E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 9.74E-009 | MW | total network loss 2701.646754 MW vs reported 2701.646754 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 2.91E-011 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.63E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.72E-008 | MVA | same residual as law 6, reactive component included at 4418 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses japan-east-spine-500-66-r6   (exit 0, 438.4 s)
(full sweep in iec60909_all_buses.txt) 500 kV (99): Ik'' max 71.64 kA (Tee 500 kV t500_24 500kV), min 7.30 kA (Substation 1028554756 500kV), median 50.96 kA; 275 kV (231): Ik'' max 118.21 kA (Minamikawasaki SS 275kV), min 3.30 kA (Higashishinjuku SS 275kV), median 37.04 kA; 220 kV (2): Ik'' max 5.44 kA (Touhokudenryokunettowaaku Kabu Kariwa SS 220kV), min 5.03 kA (Substation 1160171158 220kV), median 5.23 kA; 154 kV (643): Ik'' max 92.06 kA (Kouhoku SS 154kV), min 2.07 kA (Substation 901872436 154kV), median 27.92 kA; 66 kV (3443): Ik'' max 113.32 kA (Keihoku SS 66kV), min 1.26 kA (Substation 409551364 66kV), median 21.30 kA
```
