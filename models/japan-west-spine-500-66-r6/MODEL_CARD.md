# Japan west 60 Hz transmission 500/275/220/187/154/110/77/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official Japanese study results. A solvable rough map of the Japan west 60 Hz (Chubu, Hokuriku, Kansai, Chugoku, Shikoku, Kyushu areas) (500, 275, 220, 187, 154, 110, 77, 66 kV) for one snapshot: OpenStreetMap topology with typical per-km line parameters, synthetic transformers, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r5.

## What it is

- Snapshot: 2025-01-15 18:00-18:30 JST (Wednesday, winter evening).
- Buses 3611 (135 generator buses), branches 4423 (lines 3975, transformers 448), generators 206.
- Buses by kV: 500 kV 135, 275 kV 215, 220 kV 211, 187 kV 57, 154 kV 382, 110 kV 377, 77 kV 873, 66 kV 1226, 20 kV 135.
- Dispatch 71231.9 MW (incl. HVDC imports 1921.9 MW); demand 69021.0 MW (incl. HVDC sending ends 450.9 MW).
- Slack: 1 reference: Himeji-Daini Power Station.
- HVDC and frequency converters: Shin-Shinano FC: 420.3 MW east -> west (60 Hz side at by OSM name (??????, 275 kV, 5.4 km from the listed position)); Sakuma FC: 210.1 MW east -> west (60 Hz side at by nearness (Substation 618344827, 275 kV, 0.6 km)); Higashi-Shimizu FC: 210.1 MW east -> west (60 Hz side at by OSM name (??????, 275 kV, 2.7 km from the listed position)); Hida-Shinano HVDC (Hida converter, 60 Hz side) / Shin-Shinano (50 Hz side): 630.4 MW east -> west (60 Hz side at by OSM name (?????, 500 kV, 26.3 km from the listed position)); Kii Channel HVDC: 450.9 MW Shikoku -> Kansai (Shikoku net export 1224 MW x 1400 / (1400 + Honshi 2400); Anan by OSM name (????????, 500 kV, 3.9 km from the listed position); Kihoku by OSM name (?????, 500 kV, 7.8 km from the listed position))
- Islands before selection 54; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 3611 | 0 (0.0%) | 0 (0.0%) | 3476 (96.3%) | 135 (3.7%) |
| Branches | 4423 | 0 (0.0%) | 0 (0.0%) | 4110 (92.9%) | 313 (7.1%) |
| Generators | 206 | 0 (0.0%) | 0 (0.0%) | 206 (100.0%) | 0 (0.0%) |
| Demand points | 523 | 0 (0.0%) | 0 (0.0%) | 523 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 808 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 808 (100.0%) |

Buses are 'estimated' (positions and connectivity inferred from OSM drawings); lines are 'estimated' (drawn route length is OSM's, the per-km parameters are typical values); transformers are 'synthetic'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OpenStreetMap (Overpass, 2026-11-01) through the shared adapter a build step build_network: 3476 buses, 3975 lines, 313 couplings in this grid before island selection; cables 180.
- Converter couplings cut (frequency converters are not transformers): ['Anan Static Inverter Plant (????????)', 'Hida CS (?????)', 'Higashi-Shimizu Frequency Converter (??????)', 'Imabetsu CS (?????)', 'Kamikita CS (?????)', 'Kanzaki Substation (???? ?????)', 'Katagai SwS (?????)', 'Kihoku CS (?????)', 'Minamifukumitsurenkeitokoro (??????)', 'Nankan SS (?????)', 'Sakuma Frequency Converter Station (?????????)', 'Shin Shinano Frequency Converter Station (??????)', 'Substation 586398086 ()', 'Substation 607893570 ()', 'Substation 788177039 ()'].
- Islands over all Japan after the cut: 54 (largest [3445, 23, 13, 9, 8, 8, 8, 7, 6, 6]); the east grid is the island nearest central Tokyo, the west grid the one nearest central Osaka.
- OSM frequency tags that disagree with this grid: 0 ([]).
- Line kinds (count by kV and construction): {'110 cable': 1, '110 overhead': 431, '154 cable': 7, '154 overhead': 450, '187 cable': 2, '187 overhead': 70, '220 cable': 16, '220 overhead': 230, '275 cable': 2, '275 overhead': 265, '500 cable': 2, '500 overhead': 207, '66 cable': 120, '66 overhead': 1210, '77 cable': 30, '77 overhead': 932}.
- Line route km by kV (topology, before island selection): {'66': 4517.1, '77': 3259.0, '110': 2502.0, '154': 3225.2, '187': 1006.8, '220': 2473.4, '275': 3637.8, '500': 5006.0}.
- Adapter counts: {}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| coal | 29986.5 | 22707.0 |
| gas | 32644.2 | 24870.0 |
| geothermal | 200.0 | 162.0 |
| hydro | 20417.0 | 9284.0 |
| interconnector | 1921.9 | 1921.9 |
| nuclear | 12428.0 | 10429.0 |
| oil | 27515.0 | 1858.0 |

## Regions (MW)

| Area | Area demand (attested) | Modelled demand | Interchange (attested) |
|---|---:|---:|---:|
| chubu | 20350.00 | 18977.5 | 4098.0 |
| chugoku | 9525.00 | 8853.2 | -608.0 |
| hokuriku | 4529.00 | 4192.1 | -534.0 |
| kansai | 21639.00 | 20403.8 | 2248.0 |
| kyushu | 14104.00 | 12514.9 | -2504.0 |
| shikoku | 4118.00 | 3628.5 | -1224.0 |

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

- winter line ratings (owner seasonal rule, tightened, rung 2): 3795 overhead lines x 1.1187 (median over 5 TSOs of OCCTO-published winter / summer tie-line thermal capacities, 2021; summer base 40 C [VERIFY]); cables static; transformers untouched; per line in ambient_ratings.json
- coupling transformers (synthetic): 313 units at sites with lines at two voltages, rating 0.6 x the smaller side's summed line ratings clipped to 200-3000 MVA (median 600 MVA), x 12 % own rating, X/R 40
- synchronous plant moved behind 135 lumped GSUs (144930 MVA, x 14.5 % own rating, X/R 40; estimated)
- station export cap at J-Power Matsuura Thermal Power Plant switchyard 500kV: plant 3332 MW > 0.85 x network 2909 MVA (+ local demand); 860 MW moved to west's other synchronous units (estimated)
- station export cap at Miyazu Energy Research Center switchyard 275kV: plant 1426 MW > 0.85 x network 1454 MVA (+ local demand); 190 MW moved to west's other synchronous units (estimated)
- station export cap at Kawagoe Power Station switchyard 275kV: plant 3698 MW > 0.85 x network 1454 MVA (+ local demand); 2462 MW moved to west's other synchronous units (estimated)
- station export cap at Chita Power Station switchyard 275kV: plant 4027 MW > 0.85 x network 2909 MVA (+ local demand); 1554 MW moved to west's other synchronous units (estimated)
- station export cap at Joetsu Power Plant switchyard 275kV: plant 1901 MW > 0.85 x network 1454 MVA (+ local demand); 665 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 170247393 275kV: plant 3277 MW > 0.85 x network 1454 MVA (+ local demand); 2041 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 798162352 275kV: plant 2517 MW > 0.85 x network 2909 MVA (+ local demand); 44 MW moved to west's other synchronous units (estimated)
- station export cap at Shindaifun SS 220kV: plant 1869 MW > 0.85 x network 1942 MVA (+ local demand); 217 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 1427454449 220kV: plant 752 MW > 0.85 x network 671 MVA (+ local demand); 182 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 620155920 220kV: plant 694 MW > 0.85 x network 671 MVA (+ local demand); 123 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 619265282 154kV: plant 1032 MW > 0.85 x network 336 MVA (+ local demand); 747 MW moved to west's other synchronous units (estimated)
- station export cap at Takehara Thermal Power Plant switchyard 110kV: plant 1063 MW > 0.85 x network 336 MVA (+ local demand); 778 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 1395747282 110kV: plant 1153 MW > 0.85 x network 168 MVA (+ local demand); 1011 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 738027101 77kV: plant 314 MW > 0.85 x network 112 MVA (+ local demand); 219 MW moved to west's other synchronous units (estimated)
- station export cap at Substation 831552351 77kV: plant 122 MW > 0.85 x network 112 MVA (+ local demand); 27 MW moved to west's other synchronous units (estimated)
- station export cap at Kyuushuudenryokuichinomiya SS 66kV: plant 89 MW > 0.85 x network 89 MVA (+ local demand); 13 MW moved to west's other synchronous units (estimated)
- station export cap at Nanao SS 66kV: plant 992 MW > 0.85 x network 268 MVA (+ local demand); 764 MW moved to west's other synchronous units (estimated)
- slack: largest dispatched coal / gas station Himeji-Daini Power Station at Substation 367261471 275kV gen bus, reactive band +/-24229 MVAr (synthetic)
- seed reactive step (build._seed_shunts): fixed shunts equal to the reactive power of a fictitious 1.02 pu voltage controller at every bus without a generator, where at least 10 MVAr: 593 capacitors 38710 MVAr, 215 reactors 10540 MVAr (synthetic)
- reactive trim with reactive limits (build._trim_qlim, 1 passes, ended: inside 0.95-1.05 pu): 0 reactor steps 0 MVAr, 0 capacitor steps 0 MVAr (synthetic): 
- bus shunts placed where the snapshot needs reactive support (1 passes of a Newton solve without reactive limits): 215 reactors 10540 MVAr, 593 capacitors 38710 MVAr (synthetic; OSM maps no reactive compensation). Largest 40: Shinyamaguchi SS 500kV +1240, Substation 189777972 500kV +930, Substation 102958903 500kV -480, Shin-Hokushin Substation 275kV +420, Toumeifuruya SS 275kV +330, Itami Substation 275kV +300, Tee 500 kV t500_1 500kV +290, Substation 288316775 154kV +270, New Kagoshima Substation 66kV +240, West Shimane Substation 500kV +230, Substation 315614776 275kV +230, Higashikyuushuu SS 220kV +230, Konyou SS 154kV +230, Tee 275 kV t275_84 275kV +220, Minamianjou SS 154kV +220, Substation 1303913194 77kV +220, Yokooji Substation 77kV +220, Minamifukuoka SS 66kV +220, West Kobe Substation 275kV +210, Torishima SS 77kV +210, Tootoumi SS 275kV +200, Sankaku SS 110kV +200, Shin-Ayabe Substation 275kV +190, North Katsuragi Substation 275kV +190, Seinsein Substation 275kV +190, Matsuoka Station 154kV +190, Iwakura Substation 77kV +190, Gifu Substation 500kV -180, East Yamaguchi Substation 500kV +180, North Osaka Substation 275kV +180, Nishiochou SS 275kV +180, Inuyama Substation 275kV +180, Substation 161767717 154kV +180, East Osaka Substation 275kV +170, Tobu Substation 275kV +170, Mikawa Substation 275kV +170, South Kawachi Substation 275kV +170, Kakoshima SS 220kV +170, Substation 170247393 154kV +170, Tokuyama Substation 110kV +170

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
- Area supply and demand results (eria jukyu jisseki), half-hourly, January 2025, of the nine general transmission and distribution companies (HEPCO NW, Tohoku EPCO NW, TEPCO PG, Chubu PG, Hokuriku EPCO TD, Kansai TD, Chugoku EPCO NW, Shikoku EPCO TD, Kyushu EPCO TD) (the general transmission and distribution companies (METI grid-information guidelines)), published for public information
- Global Power Plant Database v1.3.0 (2021), rows for Japan (World Resources Institute), CC BY 4.0
- GeoNames Japan populated places (JP.zip: population, position) (GeoNames), CC BY 4.0
- Public figures for link ratings (OCCTO tie-line capacities, rounded) and station positions ([VERIFY]) (OCCTO and the utilities), facts, no licence needed
- Model assembly steps: adapter run, grid split, per-km parameters, couplings, GSUs, dispatch split, demand allocation, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries JPN ADM1 (ODbL 1.0): outlines in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf japan-west-spine-500-66-r5   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Japan west 60 Hz transmission 500/275/220/187/154/110/77/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale) (3611 buses)
  converged in 7 iteration(s), mismatch 3.64E-010 pu   losses 2227.308 MW / -13924.907 MVAr
  voltage range 1.0002 - 1.0507 pu
  lowest voltages:
      bus 2770   1.0002 pu    -24.755 deg
      bus 3274   1.0003 pu    -24.756 deg
      bus 3275   1.0003 pu    -24.756 deg
      bus 2786   1.0003 pu    -24.756 deg
      bus 3265   1.0003 pu    -24.756 deg
      bus 2771   1.0003 pu    -24.756 deg
      bus 3272   1.0003 pu    -24.757 deg
      bus 2890   1.0003 pu    -24.757 deg
      bus 3285   1.0004 pu    -24.760 deg
      bus 3287   1.0005 pu    -24.760 deg
      bus 2538   1.0005 pu    -24.760 deg
      bus 3288   1.0007 pu    -24.766 deg
(warm start baked into buses.json from that solve: flat start took 7 Newton iterations)
(the build pipeline PV/PQ complementarity check of the flat-start result: 0 unit bus(es) violate it)
(the build pipeline reading of the pf result) angle spread 126.416 deg; branches over 100 %: 126, over 80 %: 244; highest: OSM 110kV w216611060 (Tee 110 kV t110_12 110kV - Uto Substation 110kV) 306.0 %; OSM 154kV w315639799 (Matsuoka Station 154kV - Substation 315614776 154kV) 288.9 %; OSM 77kV w1551216402#2 (Tee 77 kV t77_175 77kV - Tee 77 kV t77_177 77kV) 282.3 %; OSM 77kV w949748577 (Tee 77 kV t77_173 77kV - Tee 77 kV t77_175 77kV) 282.1 %; OSM 77kV w949748576 (Tee 77 kV t77_177 77kV - Substation 691052545 77kV) 275.7 %; OSM 154kV w950033426 (Tee 154 kV t154_22 154kV - Tee 154 kV t154_23 154kV) 262.5 %; OSM 77kV w161870228#2 (Rakunan SS 77kV - Tee 77 kV t77_173 77kV) 253.5 %; OSM 110kV w373882012 (Tee 110 kV t110_18 110kV - Oosumi SS 110kV) 249.3 %
$ gridsim pf japan-west-spine-500-66-r5 (warm start)   (exit 0, 0.6 s)
Power flow - Japan west 60 Hz transmission 500/275/220/187/154/110/77/66 kV winter evening 2025-01-15 18:00 JST (UnvalidatedAtScale) (3611 buses)
  converged in 1 iteration(s), mismatch 5.77E-010 pu   losses 2227.308 MW / -13924.907 MVAr
  voltage range 1.0002 - 1.0507 pu
  lowest voltages:
      bus 2770   1.0002 pu    -24.755 deg
      bus 3274   1.0003 pu    -24.756 deg
      bus 3275   1.0003 pu    -24.756 deg
      bus 2786   1.0003 pu    -24.756 deg
      bus 3265   1.0003 pu    -24.756 deg
      bus 2771   1.0003 pu    -24.756 deg
      bus 3272   1.0003 pu    -24.757 deg
      bus 2890   1.0003 pu    -24.757 deg
      bus 3285   1.0004 pu    -24.760 deg
      bus 3287   1.0005 pu    -24.760 deg
      bus 2538   1.0005 pu    -24.760 deg
      bus 3288   1.0007 pu    -24.766 deg
$ gridsim physics-check japan-west-spine-500-66-r5   (exit 0, 0.6 s)
Physics-law audit  -  japan-west-spine-500-66-r5  (3611 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.17E-009 | MW | independent dissipation 2227.308188 MW (branch 2227.3082 + shunt -0.0000) vs reported loss 2227.308188 MW |
| 2 | Ohm's law | Holds | 5.92E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 4.40E-009 | MW | total network loss 2227.308188 MW vs reported 2227.308188 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 3.60E-010 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.49E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.61E-008 | MVA | same residual as law 6, reactive component included at 3476 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 60 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses japan-west-spine-500-66-r5   (exit 0, 73.9 s)
(full sweep in iec60909_all_buses.txt) 500 kV (135): Ik'' max 81.00 kA (West Kyoto Substation 500kV), min 14.87 kA (Substation 1037299172 500kV), median 44.15 kA; 275 kV (215): Ik'' max 101.70 kA (Substation 367261471 275kV), min 2.76 kA (Substation 134117848 275kV), median 40.91 kA; 220 kV (211): Ik'' max 61.61 kA (Kitakyuushuu SS 220kV), min 2.79 kA (Substation 1212140524 220kV), median 23.98 kA; 187 kV (57): Ik'' max 60.90 kA (Sanuki Substation 187kV), min 3.92 kA (Substation 1037463586 187kV), median 24.36 kA; 154 kV (382): Ik'' max 79.89 kA (South Kyoto Substation 154kV), min 3.02 kA (Nikenkoyasuiryoku PS switchyard 154kV), median 19.98 kA; 110 kV (377): Ik'' max 54.84 kA (Hiroshima Substation 110kV), min 2.10 kA (Substation 1024863226 110kV), median 15.34 kA; 77 kV (873): Ik'' max 84.56 kA (Kansaidenryokukitanodai SS 77kV), min 1.55 kA (Onsen SS 77kV), median 19.12 kA; 66 kV (1226): Ik'' max 82.25 kA (Kyuushuudenryoku Minoshima SS 66kV), min 2.05 kA (Substation 641710785 66kV), median 17.03 kA
```

## Inference round japan-west-spine-500-66-r6 (base japan-west-spine-500-66-r5, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 28 (45 circuits / units, 410.89 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 0 sites, 0 MVAr capacitive / 0 MVAr inductive, replacing the generic repair (808 shunts, 38710 / 10540 MVAr); NOT inferred in this round: every compensation mode broke the no-worsening rule, so the generic repair is kept exactly as the base round placed it (mode 'repair kept').
- Taps: 289 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 0; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 7 | 7 |
| iterations_warm | 1 | 1 |
| loss_mw | 2227.308 | 2163.421 |
| vmin_pu | 1.000 | 0.975 |
| vmax_pu | 1.051 | 1.136 |
| angle_spread_deg | 118.770 | 119.563 |
| over_100 | 126 | 88 |
| over_120 | 78 | 46 |
| over_140 | 53 | 30 |
| auto_cap_mvar | 38710.000 | 38710.000 |
| auto_reactor_mvar | 10540.000 | 10540.000 |
| inferred_comp_mvar_abs | 0.000 | 0 |
| units_held_at_q_limit | None | None |
| cpf_lambda | 1.105 | 1.100 |
| physics_pass | True | True |

Worst after: 263.5 % OSM 154kV w950033426 (Tee 154 kV t154_22 154kV - Tee 154 kV t154_23 154kV); 257.6 % OSM 154kV w315639799 (Matsuoka Station 154kV - Substation 315614776 154kV); 246.9 % OSM 154kV w192179210#2 (Tee 154 kV t154_187 154kV - Tee 154 kV t154_188 154kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 113.8 % TX sw179417733 275/154kV (Toumeifuruya SS 275kV - Toumeifuruya SS 154kV)
- 113.8 % OSM 154kV w1190176153 (Substation 1190176152 154kV - Substation 288316775 154kV)
- 113.0 % OSM 110kV w303757127#2 (Tomikichi SS 110kV - Tee 110 kV t110_185 110kV)
- 112.2 % OSM 154kV w211037498 (Komagane Substation 154kV - Tee 154 kV t154_191 154kV)
- 111.9 % OSM 110kV w704468606 (Sankaku SS 110kV - Uto Substation 110kV)
- 111.8 % OSM 77kV w680210357 (Substation 680210367 77kV - Tee 77 kV t77_327 77kV)
- 111.1 % OSM 110kV w373882012 (Tee 110 kV t110_18 110kV - Oosumi SS 110kV)
- 110.9 % OSM 154kV w192388310 (Chuubudenryokupawaaguriddokabushikigaisha Kamikyuuro SS 154kV - Tee 154 kV t154_186 154kV)
- 110.5 % OSM 154kV w192448296 (Takashinunone SS 154kV - Iwata Substation 154kV)
- 110.2 % OSM 110kV w148291916 (Hatsukaichi Substation 110kV - Tee 110 kV t110_75 110kV)
- 110.2 % OSM 110kV w317570291 (Tee 110 kV t110_164 110kV - Substation 242389846 110kV)
- 110.0 % OSM 110kV w317557215 (Kibi SS 110kV - Okayama Substation 110kV)
- 110.0 % OSM 220kV w238176475#3 (Tee 220 kV t220_2 220kV - Tee 220 kV t220_3 220kV)
- 110.0 % OSM 154kV w191382969#2 (Tee 154 kV t154_20 154kV - Tee 154 kV t154_22 154kV)
- 109.2 % TX sw170247308 275/154kV (Mikawa Substation 275kV - Mikawa Substation 154kV)
- 109.0 % TX sw161948515 275/154kV (Seinsein Substation 275kV - Seinsein Substation 154kV)
- 108.9 % TX sw641527416 220/110kV (Shintottori SS 220kV - Shintottori SS 110kV)
- 108.8 % OSM 154kV w211037498#3 (Tee 154 kV t154_192 154kV - Substation 211037497 154kV)
- 107.1 % OSM 110kV w317570286 (Tee 110 kV t110_101 110kV - North Onomichi Substation 110kV)
- 105.6 % OSM 154kV w254574143 (Substation 191462506 154kV - Yodogawa SS 154kV)
- 105.5 % OSM 154kV w191382969 (Substation 288316775 154kV - Tee 154 kV t154_20 154kV)
- 105.2 % OSM 154kV w102286794 (Substation 170247393 154kV - Minamianjou SS 154kV)
- 104.5 % OSM 154kV w192599335 (West Nagoya Substation 154kV - Substation 192599334 154kV)
- 104.1 % OSM 110kV w429529624#2 (Tee 110 kV t110_177 110kV - Chuugokudenryoku Tottoridenryokusentaa 110kV)
- 103.9 % OSM 110kV w100138049#2 (Tee 110 kV t110_76 110kV - Tee 110 kV t110_77 110kV)
- 103.2 % OSM 110kV w627624212 (Tee 110 kV t110_104 110kV - North Matsue Substation 110kV)
- 103.1 % OSM 110kV w317444447 plant (Takehara Thermal Power Plant switchyard 110kV - Substation 860296910 110kV)
- 102.8 % OSM 110kV w1427454351 (Tee 110 kV t110_104 110kV - Tee 110 kV t110_105 110kV)
- 102.8 % OSM 110kV w303792003 (Substation 242389846 110kV - Tee 110 kV t110_166 110kV)
- 102.7 % OSM 77kV w643389781 (Tee 77 kV t77_225 77kV - Maibara Substation 77kV)
- 102.2 % OSM 154kV w176265157 (Toyohashidenryokusentaa 154kV - Mikawa Substation 154kV)
- 101.7 % OSM 110kV w151462899 (New Hiroshima Substation 110kV - Tee 110 kV t110_95 110kV)
- 101.2 % OSM 110kV w318438190 (Tee 110 kV t110_33 110kV - Tee 110 kV t110_37 110kV)
- 100.9 % OSM 77kV w159177103 (Suwa Substation 77kV - Tee 77 kV t77_381 77kV)
- 100.7 % OSM 220kV w1558047743 (Kyuushuunyuugyouhonshakoujouc S 220kV - Tee 220 kV t220_65 220kV)
- 100.5 % OSM 110kV w641527469#2 (Tee 110 kV t110_178 110kV - Tee 110 kV t110_180 110kV)

Inferred feeds:

- inferred feed 1: 110 kV line x2 South Kumamoto Substation 110kV - Uto Substation 110kV 10.53 km; demanded by OSM 110kV w216611060 (Tee 110 kV t110_12 110kV - Uto Substation 110kV) at 306.0 % (N-0 snapshot, bridge: no alternative path); after 121.9 %
- inferred feed 2: 77 kV line x2 South Kyoto Substation 77kV - Substation 691052545 77kV 6.74 km; demanded by OSM 77kV w1551216402#2 (Tee 77 kV t77_175 77kV - Tee 77 kV t77_177 77kV) at 282.3 % (N-0 snapshot, bridge: no alternative path); after 154.7 %
- inferred feed 3: 110 kV line x2 Oosumi SS 110kV - Substation 614199719 110kV 4.83 km; demanded by OSM 110kV w373882012 (Tee 110 kV t110_18 110kV - Oosumi SS 110kV) at 249.4 % (N-0 snapshot, bridge: no alternative path); after 112.3 %
- inferred feed 4: 110 kV line x2 Onoda SS 110kV - Ube Substation 110kV 7.17 km; demanded by OSM 110kV w318438190 (Tee 110 kV t110_33 110kV - Tee 110 kV t110_37 110kV) at 248.2 % (N-0 snapshot); after 101.5 %
- inferred feed 5: 110 kV line x1 North Matsue Substation 110kV - Substation 641699577 110kV 14.48 km; demanded by OSM 110kV w317520866 (North Matsue Substation 110kV - Tee 110 kV t110_103 110kV) at 234.0 % (N-0 snapshot); after 174.8 %
- inferred feed 6: 77 kV line x2 Isami SS 77kV - Substation 1303913194 77kV 0.77 km; demanded by OSM 77kV w1196865072 (Substation 1303913194 77kV - Isami SS 77kV) at 233.6 % (N-0 snapshot); after 96.6 %
- inferred feed 7: 77 kV line x2 Minamianjou SS 77kV - Nishio SS 77kV 3.19 km; demanded by OSM 77kV w909220822 (Minamianjou SS 77kV - Nishio SS 77kV) at 208.9 % (N-0 snapshot, bridge: no alternative path); after 66.0 %
- inferred feed 8: 154 kV line x1 Rittou SS 154kV - Substation 707961022 154kV 1.43 km; demanded by OSM 154kV w633287254 (Tee 154 kV t154_32 154kV - Substation 707961022 154kV) at 194.8 % (N-0 snapshot, bridge: no alternative path); after 117.9 %
- inferred feed 9: 66 kV line x2 Kumamoto Substation 66kV - Yuge SS 66kV 12.86 km; demanded by OSM 66kV w726536492 (Yuge SS 66kV - Tee 66 kV t66_129 66kV) at 171.5 % (N-0 snapshot); and OSM 66kV w726536492 (Yuge SS 66kV - Tee 66 kV t66_129 66kV) at 146.3 % -> 128.6 %; after 128.6 %
- inferred feed 10: 77 kV line x2 Kotou SS 77kV - Maibara Substation 77kV 1.79 km; demanded by OSM 77kV w316459333 (Maibara Substation 77kV - Tee 77 kV t77_227 77kV) at 165.0 % (N-0 snapshot, bridge: no alternative path); after 96.4 %
- inferred feed 11: 77 kV line x1 New Ikoma Substation 77kV - Substation 726967823 77kV 9.15 km; demanded by OSM 77kV w241805094 (Substation 726967823 77kV - Tee 77 kV t77_176 77kV) at 163.8 % (N-0 snapshot, bridge: no alternative path); after 95.5 %
- inferred feed 12: 77 kV line x1 Itami Substation 77kV - Konyou SS 77kV 1.36 km; demanded by OSM 77kV w1300171854 (Itami Substation 77kV - Konyou SS 77kV) at 163.6 % (N-0 snapshot); after 96.3 %
- inferred feed 13: 110 kV line x2 Hiroshima Substation 110kV - Substation 1381570768 110kV 20.71 km; demanded by OSM 110kV w199426932 (Tee 110 kV t110_75 110kV - Substation 1381570768 110kV) at 155.0 % (N-0 snapshot, bridge: no alternative path); and OSM 110kV w148291916 (Hatsukaichi Substation 110kV - Tee 110 kV t110_75 110kV) at 124.9 % -> 111.4 %; after 111.4 %
- inferred feed 14: 77 kV line x2 Hirakata SS 77kV - Jouyou SS 77kV 9.65 km; demanded by OSM 77kV w949748577 (Tee 77 kV t77_173 77kV - Tee 77 kV t77_175 77kV) at 154.0 % (N-0 snapshot, bridge: no alternative path); after 97.2 %
- inferred feed 15: 275 kV line x2 New Mikawa Substation 275kV - Mikawa Substation 275kV 5.42 km; demanded by OSM 275kV w204310100 (Tee 275 kV t275_95 275kV - Mikawa Substation 275kV) at 146.9 % (N-0 snapshot); after 80.0 %
- inferred feed 16: 77 kV line x2 Inuyama Substation 77kV - Haguro Substation 77kV 4.32 km; demanded by OSM 77kV w202112671 (Haguro Substation 77kV - Inuyama Substation 77kV) at 144.7 % (N-0 snapshot); after 67.2 %
- inferred feed 17: 154 kV line x1 Itami Substation 154kV - Konyou SS 154kV 1.36 km; demanded by OSM 154kV w448931395 (Itami Substation 154kV - Konyou SS 154kV) at 142.3 % (N-0 snapshot); after 99.8 %
- inferred feed 18: 77 kV line x2 Higashi-Shimizu Frequency Converter 77kV - Shimizu Substation 77kV 6.19 km; demanded by OSM 77kV w618344851 (Tee 77 kV t77_401 77kV - Tee 77 kV t77_402 77kV) at 141.8 % (N-0 snapshot); after 80.8 %
- inferred feed 19: 77 kV line x1 Kosai Substation 77kV - Ueda SS 77kV 12.18 km; demanded by OSM 77kV w416887747 (Tee 77 kV t77_344 77kV - Tee 77 kV t77_346 77kV) at 135.9 % (N-0 snapshot); after 97.4 %
- inferred feed 20: 154 kV line x1 Inuyama Substation 154kV - Koizumi SS 154kV 11.26 km; demanded by OSM 154kV w209269402 (Inuyama Substation 154kV - Koizumi SS 154kV) at 132.8 % (N-0 snapshot, bridge: no alternative path); after 60.2 %
- inferred feed 21: 66 kV line x1 Kyuushuudenryokumidorikawa SS 66kV - Ginzabashi SS 66kV 7.98 km; demanded by OSM 66kV w1520534465 (Shinmachi SS 66kV - Tee 66 kV t66_93 66kV) at 132.8 % (N-0 snapshot); after 98.2 %
- inferred feed 22: 154 kV line x2 Shigi Substation 154kV - Nagasone Substation 154kV 13.14 km; demanded by OSM 154kV w191434696 (Tee 154 kV t154_4 154kV - Yao Substation 154kV) at 132.1 % (N-0 snapshot); after 99.8 %
- inferred feed 23: 66 kV line x2 Kakoshima SS 66kV - New Kagoshima Substation 66kV 12.33 km; demanded by OSM 66kV w237475189 (New Kagoshima Substation 66kV - Shihara SS 66kV) at 126.2 % (N-0 snapshot); after 84.1 %
- inferred feed 24: 77 kV line x2 Substation 315614783 77kV - Matsuoka Station 77kV 12.94 km; demanded by OSM 77kV w1239340728 (Kanetsu SS 77kV - Matsuoka Station 77kV) at 123.7 % (N-0 snapshot); after 66.5 %
- inferred feed 25: 77 kV line x1 Nakasei SS 77kV - Substation 241916075 77kV 18.73 km; demanded by OSM 77kV w444367621 (Tee 77 kV t77_235 77kV - Tee 77 kV t77_244 77kV) at 122.2 % (N-0 snapshot); after 98.2 %
- inferred feed 26: 154 kV line x1 Konan SS 154kV - Substation 707961022 154kV 9.71 km; demanded by OSM 154kV w633287254 (Tee 154 kV t154_32 154kV - Substation 707961022 154kV) at 118.2 % (N-0 snapshot, bridge: no alternative path); after 86.6 %
- inferred feed 27: 77 kV line x1 North Kariya Substation 77kV - Substation 1303913189 77kV 3.21 km; demanded by OSM 77kV w253935213 (Tee 77 kV t77_325 77kV - Tee 77 kV t77_323 77kV) at 117.5 % (N-0 snapshot); after 87.4 %
- inferred feed 28: 66 kV line x2 Kirishima SS 66kV - Substation 614215624 66kV 27.44 km; demanded by OSM 66kV w715757179 (Substation 614215624 66kV - Substation 608351638 66kV) at 117.5 % (N-0 snapshot); after 87.9 %

Inferred compensation (largest 15; full list in inferred_elements.json):
