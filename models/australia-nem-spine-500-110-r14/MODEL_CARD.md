# Australia NEM mainland transmission 500/330/275/220/132/110 kV winter peak 2025-07-01 18:00 AEST (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official Australian study results. A solvable rough map of the NEM mainland (QLD, NSW + ACT, VIC, SA) (500, 330, 275, 220, 132, 110 kV) for one snapshot: Geoscience Australia topology with typical per-km line parameters, synthetic transformers, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r12.

## What it is

- Snapshot: 2025-07-01 18:00 AEST (UTC+10; the 5-minute interval ending 18:00), the highest mainland NEM operational demand of June-August 2025 (AEMO price-and-demand files).
- Buses 1038 (91 generator buses), branches 1536 (lines 1309, transformers 227), generators 337.
- Buses by kV: 500 kV 28, 330 kV 78, 275 kV 106, 220 kV 68, 132 kV 560, 110 kV 107, 20 kV 91.
- Dispatch 31998.9 MW (incl. HVDC imports 700.0 MW); demand 31046.5 MW (incl. HVDC sending ends 250.0 MW).
- Slack: 1 reference: Eraring (coal).
- Tasmania / HVDC: Tasmania is NOT in the AC case: Basslink is a boundary injection of 450 MW into the Basslink-Loy Yang 500 kV bus (Tasmanian demand and plant left out). Murraylink (150 MW Red Cliffs 220 kV -> Monash 132 kV) and Directlink (100 MW Bungalora 110 kV -> Mullumbimby 132 kV) are injection pairs (load at the sending end, generator at the receiving end). All three flows estimated [VERIFY].
- Islands before selection 16; buses dropped 42.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1038 | 0 (0.0%) | 0 (0.0%) | 947 (91.2%) | 91 (8.8%) |
| Branches | 1536 | 0 (0.0%) | 0 (0.0%) | 1400 (91.1%) | 136 (8.9%) |
| Generators | 337 | 334 (99.1%) | 0 (0.0%) | 3 (0.9%) | 0 (0.0%) |
| Demand points | 659 | 0 (0.0%) | 0 (0.0%) | 659 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 451 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 451 (100.0%) |

Buses are 'estimated' (positions and connectivity inferred from GA drawings); lines are 'estimated' (drawn route length is GA's, the per-km parameters are typical values); transformers are 'synthetic'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- Geoscience Australia power lines: 3147 features; kept 1479 operational features at 500, 330, 275, 220, 132, 110 kV in the grid's states; left out: {'voltage 66': 1230, 'voltage 400': 1, 'other grid': 412, 'status Non-Operational': 11, 'status Under Construction': 5, 'voltage 88': 1, 'HVDC cable labelled AC': 2, 'exact duplicate drawing': 6}.
- HVDC cables left out of the AC network: ['Mullumbimby to Bungalora (GA 132 kV Underground, 37.0 km)', 'Monash to Red Cliffs Terminal (GA 220 kV Underground, 174.1 km)']
- 1493 GA substations -> 1446 sites (42 sites merge 2+ GA points closer than 0.5 km)
- line ends resolved: {'exact': 2503, 'name': 320, 'near': 42, 'tee-to-site': 5, 'tee': 60, 'far': 14, 'dangling': 14}
- junction buses merged out (series drawing breaks): 5; self-loop lines dropped: 164 (all no longer than 1.0 km); line ends reopened as end buses (both ends on one site, line longer than 1.0 km): 49
- circuit counts from OSM (ODbL): 1196 of 1479 GA features matched; 310 model lines raised above 1 circuit (by kV {500: 10, 330: 20, 275: 65, 220: 12, 132: 148, 110: 55})
- r4 OSM circuits not in GA: 1828 OSM ways uncovered by GA; added 29 lines ({132: 798.6, 275: 218.7, 330: 61.7} km by kV; 8 cables) and 26 site buses (118 new sites from OSM substations GA does not list); left out: {'ring or no ends': 6, 'an end at no GA site, or both ends at one': 497, 'branching chain': 105, 'cut-in: 0 candidate GA lines (need exactly 1)': 85, 'cut-in: 2 candidate GA lines (need exactly 1)': 3, 'cut-ins made (r6)': 1, 'dead-end stub at a new OSM site (r5)': 89}
- Line kinds (count by kV and construction): {'110 cable': 20, '110 overhead': 110, '132 cable': 98, '132 overhead': 629, '220 cable': 1, '220 overhead': 121, '275 cable': 2, '275 overhead': 170, '330 cable': 6, '330 overhead': 115, '500 overhead': 37}.
- Line route km by kV (topology, before island selection): {'500': 2374.4, '330': 7565.3, '275': 10813.7, '220': 5326.4, '132': 21536.4, '110': 2087.8}.
- End snaps beyond 1 km (estimated): 14; self-loop features dropped: 164; ends reopened as end buses: 49.
- Islands in the topology: 16 (sizes [947, 13, 3, 2, 2, 2, 2, 2, 2, 2, 2, 2]).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 2322.8 | 580.7 |
| biomass | 370.5 | 185.2 |
| coal | 21255.0 | 18066.8 |
| gas_ccgt | 2649.9 | 1604.4 |
| gas_ocgt | 6877.1 | 3431.6 |
| gas_other | 1923.5 | 454.0 |
| hydro | 5668.0 | 3400.8 |
| interconnector | 750.0 | 700.0 |
| other | 148.7 | 42.0 |
| solar | 10122.4 | 0.0 |
| wind | 11777.7 | 3533.3 |

## Regions (MW)

| Region | Operational demand | Modelled demand | Dispatch in region |
|---|---:|---:|---:|
| NSW1 | 13111.66 | 12718.3 | 11862.4 |
| QLD1 | 8315.10 | 8165.6 | 9029.1 |
| SA1 | 2215.04 | 2148.6 | 2551.6 |
| VIC1 | 8107.12 | 8013.9 | 8555.8 |

## Fitted and assumed values (the brief's NO FITTING TO THE SOLVER rule)

- ASSUMED (no source): line R / X / B and thermal ratings per circuit by voltage and construction (overhead {500: (0.017, 0.28, 4.1, 2600.0), 400: (0.02, 0.3, 3.8, 1500.0), 330: (0.03, 0.32, 3.55, 1200.0), 275: (0.04, 0.32, 3.55, 950.0), 220: (0.07, 0.4, 2.85, 450.0), 132: (0.11, 0.4, 2.85, 180.0), 110: (0.13, 0.4, 2.85, 140.0)}; cable {330: (0.02, 0.13, 70.0, 700.0), 275: (0.02, 0.13, 65.0, 550.0), 220: (0.025, 0.13, 60.0, 400.0), 132: (0.035, 0.13, 55.0, 200.0), 110: (0.04, 0.13, 50.0, 150.0)}; R ohm/km, X ohm/km, B uS/km, MVA).
- ASSUMED: coupling transformers x 12 % on own rating, X/R 40; size by a physical rule: 0.6 x the smaller side's line ratings, and at least 1.5 x the demand on the LV bus (the unit must carry it); clipped to 200-3000 MVA (assumed).
- ASSUMED: GSU x 14.5 %, X/R 40; unit Q range -0.3 to 0.62 MVAr per MW (synchronous), +/-0.33 (inverter).
- PHYSICAL RULE: station export cap 0.85 x the station's network branch ratings (plant cannot export more than its connection carries); the excess goes to the region's other synchronous units.
- SYNTHETIC REPAIR: every bus shunt (seed step, copied staged repair, reactive-limit trim).
- SOURCED: circuit counts above 1 from OpenStreetMap 'circuits' / 'cables' tags (ODbL).

## Repairs (every change made so the case solves)

- islands dropped: 15 with 42 buses (largest 13): Century Mine, Chumvale, Diamantina; Kojonup Substation, OSM substation 250487628, OSM substation 760927975; End Gunnedah East Solar Farm to Tee, Gunnedah East Solar Farm; Bodangora Wind Farm, End Bodangora Wind Farm to Tee; End Jindabyne Power Station to Jindabyne Substation, Jindabyne; Schofields, South Marsden Park; Newman Alinta Substation, OSM substation 759562864; End Mudgee Tee to Ilford Tee, Mudgee; End Eucumbene to Snowy Adit, Snowy Adit; Dorrigo, End Dorrigo to Tee; Cape River East, Jardine Creek; End Moree Solar to Tee, Moree Solar; East Lake Zone Substation, End Eastlake to Tee; OSM substation 44315236, OSM substation 760020579; Croydon, Leichhardt
- winter line ratings (owner seasonal rule, tightened): 1143 overhead lines x 1.0595 (rung 2: median winter/summer of Ausgrid's 233 published 132 kV feeder ratings, DTAPR 2025; OH base taken as summer [VERIFY]; 220-500 kV same factor [VERIFY]); 85 132 kV lines take Ausgrid's published winter 2026 feeder rating (rung 1, matched by end names); cables otherwise static; transformers untouched; per line in ambient_ratings.json
- Ausgrid feeder counts (DTAPR 2025, attested): 16 single GA 132 kV lines carry more published Ausgrid feeders than circuits and take that count: L643 Bunnerong to Kurnell 1 -> 2 (245, 246); L665 Haymarket to City North 1 -> 3 (91G, 92E, 93C); L668 Sydney East to Willoughby 132 1 -> 4 (9E3, 9E5, 9Y4, 9Y5); L755 Chullora to St Peters 1 -> 2 (92C, 92X); L758 Chullora to Marrickville 1 -> 2 (91X, 91Y); L764 Hurstville North to Peakhurst 1 -> 2 (91C, 91R); L766 Haymarket to Beaconsfield North 1 -> 2 (9S2, 9S4); L788 Sydney North to Galston 1 -> 2 (257, 258); L798 Sydney East to Willoughby (Overhead) 2 -> 3 (9E3, 9E4, 9E5); L801 Sydney East to Warringah 2 -> 4 (9M1, 9M2, 9M3, 9M4); L842 Haymarket to Pyrmont 1 -> 2 (9S6, 9S9); L851 Tuggerah to Berkeley Vale 1 -> 2 (94L, 954); L1039 Bankstown to Sydney South 1 -> 2 (914, 915); L1040 Greenacre Park to Bankstown 1 -> 2 (293, 294); OSM96 Willoughby to Mosman 1 -> 2 (9H4, 9H6); OSM98 Willoughby to Crows Nest 1 -> 2 (9H3, 9H5)
- coupling transformers (synthetic): 136 units at sites with lines at two voltages, rating 0.6 x the smaller side's summed line ratings clipped to 200-3000 MVA (median 435 MVA), x 12 % own rating, X/R 40
- synchronous plant moved behind 91 lumped GSUs (45756 MVA, x 14.5 % own rating, X/R 40; estimated)
- slack: largest dispatched coal station Eraring (coal) at Eraring 330kV gen bus, reactive band +/-16941 MVAr (synthetic)
- seed reactive step (build._seed_shunts): fixed shunts equal to the reactive power of a fictitious 1.02 pu voltage controller at every bus without a generator, where at least 10 MVAr: 292 capacitors 15730 MVAr, 147 reactors 9330 MVAr (synthetic)
- reactive repair stopped early at some stage(s): pass 1: no damped step solves; 19 buses still outside
- reactive trim with reactive limits (build._trim_qlim, 3 passes, ended: inside 0.95-1.05 pu): 8 reactor steps 40 MVAr, 0 capacitor steps 0 MVAr (synthetic): Leigh Creek Coalfield 132kV -5, Leigh Creek South 132kV -5, End Prominent Hill to Tee 132kV -5, Nyngan Solar Farm 132kV -5, Nyngan 132kV -5, Tee Leigh Creek South Tee to Neuroodla Tee 132kV -5, Neuroodla 132kV -5, Nevertire 132kV -5, Endevour Mine 132kV +0, CSA Maine 132kV +0, Tee Nyngan to Tee 132kV +0, Peak Gold Mine 132kV +0
- bus shunts placed where the snapshot needs reactive support (1 passes of a Newton solve without reactive limits): 155 reactors 9370 MVAr, 292 capacitors 15730 MVAr (synthetic; GA publishes no reactive compensation). Largest 40: Bayswater 500kV -410, Wollar 500kV -330, Gin Gin 275kV +330, Boyne Island 275kV +290, Tomago 330kV +260, South Pine 275kV +240, Bannaby 500kV -230, Cherry Gardens 132kV +220, Rookwood Road 330kV -200, Holroyd 330kV -200, Halys 275kV +200, Ringwood 220kV +200, Heywood 500kV -190, Woolooga 275 275kV +190, South Pine 110kV -190, Mount Piper 500 330kV -180, Blackwall 275kV +180, Brunswick 220kV +180, Richmond 220kV +180, Mooloolaba 132kV +180, Sydney South 132kV -180, Tarrone 500kV -170, Malvern 220kV +170, Kemps Creek 500kV -160, Armidale 330kV -160, West Melbourne 220kV +160, Templestowe 220kV +160, Beaconsfield 132kV -160, Sydney East 132kV -160, Para 132kV +160, Haunted Gully 500kV -150, Dederang 330kV -150, Sydney South 330kV -150, Newport 220kV +150, Heatherton 220kV +150, End Millbrook to Millbrook Tee 132kV +150, Sydney North 132kV -150, Belmont 110kV -150, Cleveland 110kV +150, Bundey 330kV -140

## Round history (the solver's findings that drove each round)

- r1: first build; reactive repair by seed shunts (fictitious voltage control) and the copied staged repair.
- r1 solve (NEM): pf flat 14 iterations, warm 11, physics-check PASS; V 0.9456-1.1479 pu (Endevour Mine 132 kV high, units at reactive limits), losses 1278.178 MW, angle spread 82.545 deg, 34 branches over 100 % (Sydney and Brisbane 132 / 110 kV, Adelaide Para 132 kV, worst Bankstown - Sydney South 216.3 %), 9 synthetic couplings over 100 %; IEC 60909 132 kV max 61.20 kA (Sydney West), 220 kV max 53.55 kA (Keilor).
- r2 changes: (1) synthetic couplings loaded above 90 % in r1 resized to carry that flow at 80 %; (2) 132 / 110 kV cable ratings 250 / 200 MVA (were 200 / 150); (3) a final reactive trim with reactive limits.
- r2 solve (NEM): pf flat 12 iterations, warm 9, physics-check PASS; V 0.9694-1.0470 pu, losses 1242.775 MW, angle spread 83.472 deg, 17 branches over 100 % (worst Millbrook - Para 132 kV 214.7 %, Vineyard - Rouse Hill 200.0 %, Potts Hill - Rookwood Road 196.0 %).
- r3 changes (NO FITTING rule from here on): r2's two unsourced changes WITHDRAWN (the 10 couplings sized to r1 flow; the 250 / 200 MVA cable ratings): back to the r1 assumptions. Demand: each metropolitan total spread over its GeoNames suburbs (PPLX, by population) instead of in equal parts over every bus within reach (a topology / demand-placement fix). The reactive-limit trim stays (synthetic repair).
- r7 (owner seasonal rule, tightened, rung 2): every overhead line x the median winter/summer ratio of Ausgrid's 233 published 132 kV feeder ratings (1.0595); cables static; couplings sized from static ratings.
- r8 (rung 1 + published counts): 132 kV lines matched by end names to Ausgrid DTAPR 2025 feeders take the mean published winter 2026 feeder rating per circuit, and a single GA line takes Ausgrid's feeder count.

## Known gaps

- Line impedances and ratings are TYPICAL per-km values by voltage, not the TNSPs' own: circuit counts are taken as one per GA feature (double-circuit towers drawn once would be under-counted) [VERIFY].
- Transformers are synthetic (one coupling per voltage pair per site); real 500/330/275/220/132/110 kV transformer fleets, taps and OLTCs are not modelled.
- No reactive compensation is published in the GA data; the bus shunts are fixed repairs.
- Mid-span tees whose GA end lies on another line's interior are not split, so a few small 132 kV pieces fall off as islands (listed in the repairs).
- Plant register: AEMO Generation Information July 2025 placed by name on GA points; 32 sites (1379.1 MW) could not be placed by name and are left out.
- Dispatch is a merit rule by fuel (solar 0 after dark, wind 30 %, batteries 25 %, coal to 85 %, hydro to 60 %, gas to 85 %), not AEMO's unit dispatch for the interval [VERIFY].
- Demand is AEMO regional operational demand spread by GeoNames population, with four large industrial loads placed by hand ([VERIFY] figures); no load map below 110 kV.
- Tasmania is outside the case: Basslink is a fixed import at Basslink-Loy Yang 500 kV; Murraylink and Directlink are fixed injection pairs (flows estimated, [VERIFY]).

## Sources

- Electricity Infrastructure (Power Lines, Substations, Major Power Stations), MapServer query of 2026-10-31 (Geoscience Australia (Commonwealth of Australia)), CC BY 4.0
- NEM Generation Information, July 2025 (existing units: site, fuel, nameplate MW, status) (Australian Energy Market Operator (AEMO)), AEMO copyright permissions: reuse with attribution
- Aggregated price and demand data, 5-minute TOTALDEMAND per NEM region, June-August 2025 (Australian Energy Market Operator (AEMO)), AEMO copyright permissions: reuse with attribution
- WEM operational demand / generation data (AEMO WA) (Australian Energy Market Operator (AEMO)), AEMO copyright permissions: reuse with attribution
- GeoNames Australia populated places (AU.zip: population, position) (GeoNames), CC BY 4.0
- OpenStreetMap power lines and cables 110 kV and above in Australia (Overpass API, 2026-10-31): circuit counts ('circuits', else cables / 3) matched onto GA features (OpenStreetMap contributors), ODbL 1.0
- Public figures for HVDC flows and large industrial loads (rounded, [VERIFY]) (various (company and AEMO publications)), facts, no licence needed
- Model assembly steps: site grouping, end resolution, per-km parameters, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- ABS ASGS 2021 States and Territories (generalised), CC BY 4.0: outlines in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf australia-nem-spine-500-110-r12   (flat start: vm 1, vaDeg 0; exit 0, 0.6 s)
Power flow - Australia NEM mainland transmission 500/330/275/220/132/110 kV winter peak 2025-07-01 18:00 AEST (UnvalidatedAtScale) (1038 buses)
  converged in 13 iteration(s), mismatch 3.42E-012 pu   losses 1208.866 MW / -9311.481 MVAr
  voltage range 0.9846 - 1.0439 pu
  lowest voltages:
      bus 648    0.9846 pu     34.051 deg
      bus 643    0.9852 pu     34.042 deg
      bus 405    0.9937 pu    -19.401 deg
      bus 404    0.9940 pu    -18.439 deg
      bus 407    0.9941 pu    -17.961 deg
      bus 537    0.9952 pu    -17.016 deg
      bus 406    0.9960 pu    -19.079 deg
      bus 536    0.9966 pu    -17.485 deg
      bus 469    0.9976 pu    -19.032 deg
      bus 947    0.9977 pu    -20.155 deg
      bus 597    0.9982 pu    -19.081 deg
      bus 538    0.9986 pu    -17.501 deg
(warm start baked into buses.json from that solve: flat start took 13 Newton iterations)
(the build pipeline reading of the pf result) angle spread 89.979 deg; branches over 100 %: 20, over 80 %: 43; highest: L1036 (Potts Hill 132kV - Rookwood Road 132kV) 160.6 %; L1074 (Rozelle 132kV - Pyrmont 132kV) 158.8 %; L968 (Millbrook 132kV - End Millbrook to Millbrook Tee 132kV) 153.9 %; L867 (Vineyard 132kV - Rouse Hill 132kV) 153.3 %; L1225 (West Darra 110kV - Goodna 110kV) 135.6 %; L575 (Mooloolaba 132kV - Palmwoods 132kV) 135.5 %; L576 (Mooloolaba 132kV - Palmwoods 132kV) 135.4 %; L1238 (Stafford 110kV - South Pine 110kV) 120.3 %
$ gridsim pf australia-nem-spine-500-110-r12 (warm start)   (exit 0, 0.5 s)
Power flow - Australia NEM mainland transmission 500/330/275/220/132/110 kV winter peak 2025-07-01 18:00 AEST (UnvalidatedAtScale) (1038 buses)
  converged in 9 iteration(s), mismatch 4.23E-012 pu   losses 1208.866 MW / -9311.481 MVAr
  voltage range 0.9846 - 1.0439 pu
  lowest voltages:
      bus 648    0.9846 pu     34.051 deg
      bus 643    0.9852 pu     34.042 deg
      bus 405    0.9937 pu    -19.401 deg
      bus 404    0.9940 pu    -18.439 deg
      bus 407    0.9941 pu    -17.961 deg
      bus 537    0.9952 pu    -17.016 deg
      bus 406    0.9960 pu    -19.079 deg
      bus 536    0.9966 pu    -17.485 deg
      bus 469    0.9976 pu    -19.032 deg
      bus 947    0.9977 pu    -20.155 deg
      bus 597    0.9982 pu    -19.081 deg
      bus 538    0.9986 pu    -17.501 deg
$ gridsim physics-check australia-nem-spine-500-110-r12   (exit 0, 0.5 s)
Physics-law audit  -  australia-nem-spine-500-110-r12  (1038 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.68E-011 | MW | independent dissipation 1208.865829 MW (branch 1208.8658 + shunt -0.0000) vs reported loss 1208.865829 MW |
| 2 | Ohm's law | Holds | 1.03E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 5.16E-011 | MW | total network loss 1208.865829 MW vs reported 1208.865829 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 3.96E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.34E-009 | MVA | same residual as law 6, reactive component included at 889 PQ bus(es), by the bus types the solve ended with; 18 of them declared PV and solved as PQ (18 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses australia-nem-spine-500-110-r12   (exit 0, 7.3 s)
(full sweep in iec60909_all_buses.txt) 500 kV (28): Ik'' max 31.79 kA (Loy Yang 500kV), min 9.18 kA (Chirnside 500kV), median 20.49 kA; 330 kV (78): Ik'' max 46.92 kA (Eraring 330kV), min 2.73 kA (Lismore 330kV), median 20.98 kA; 275 kV (106): Ik'' max 39.90 kA (Tarong 275kV), min 2.30 kA (Kidston 275kV), median 18.97 kA; 220 kV (68): Ik'' max 54.86 kA (Keilor 220kV), min 2.85 kA (Silverton 220kV), median 17.54 kA; 132 kV (560): Ik'' max 63.66 kA (Sydney West 132kV), min 0.82 kA (Endevour Mine 132kV), median 9.90 kA; 110 kV (107): Ik'' max 39.25 kA (Belmont 110kV), min 1.67 kA (Stanthorpe 110kV), median 15.64 kA
```

## Inference round australia-nem-spine-500-110-r14 (base australia-nem-spine-500-110-r12, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 4 (6 circuits / units, 32.02 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 401 sites, 15080 MVAr capacitive / 9570 MVAr inductive, replacing the generic repair (447 shunts, 15730 / 9370 MVAr) (mode 'consolidated').
- Taps: 94 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 18; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 13 | 13 |
| iterations_warm | 9 | 9 |
| loss_mw | 1208.866 | 1214.249 |
| vmin_pu | 0.985 | 0.965 |
| vmax_pu | 1.044 | 1.049 |
| angle_spread_deg | 87.420 | 88.419 |
| over_100 | 20 | 15 |
| over_120 | 8 | 3 |
| over_140 | 4 | 0 |
| auto_cap_mvar | 15730.000 | 0 |
| auto_reactor_mvar | 9370.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 24650.000 |
| units_held_at_q_limit | 18 | 15 |
| cpf_lambda | 1.049 | 1.033 |
| physics_pass | True | True |

Worst after: 134.5 % L575 (Mooloolaba 132kV - Palmwoods 132kV); 134.5 % L576 (Mooloolaba 132kV - Palmwoods 132kV); 133.8 % L1225 (West Darra 110kV - Goodna 110kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 112.5 % L1237 (Ashgrove West 110kV - Milton 110kV)
- 110.5 % T16 (Rocklea 275kV - Rocklea 132kV)
- 108.3 % L1074 (Rozelle 132kV - Pyrmont 132kV)
- 104.6 % L879 (Sydney West 132kV - Blacktown 132kV)
- 104.5 % T109 (Rookwood Road 330kV - Rookwood Road 132kV)
- 104.2 % L880 (Sydney West 132kV - Blacktown 132kV)
- 101.4 % T50 (Beaconsfield 330kV - Beaconsfield 132kV)
- 100.8 % L687 (West Wetherill 132kV - Sydney West 132kV)
- 100.7 % L1036 (Potts Hill 132kV - Rookwood Road 132kV)
- 100.7 % T4 (Molendinar 275kV - Molendinar 132kV)

Inferred feeds:

- inferred feed 1: 132 kV line x2 Rookwood Road 132kV - Potts Hill 132kV 0.82 km; demanded by L1036 (Potts Hill 132kV - Rookwood Road 132kV) at 160.6 % (N-0 snapshot); and L1036 (Potts Hill 132kV - Rookwood Road 132kV) at 126.1 % -> 104.4 %; after 104.4 %
- inferred feed 2: 132 kV line x2 Haymarket 132kV - Rozelle 132kV 3.98 km; demanded by L1074 (Rozelle 132kV - Pyrmont 132kV) at 158.8 % (N-0 snapshot); and L1074 (Rozelle 132kV - Pyrmont 132kV) at 128.2 % -> 109.3 %; after 109.3 %
- inferred feed 3: 132 kV line x1 Para 132kV - End Millbrook to Millbrook Tee 132kV 15.29 km; demanded by L968 (Millbrook 132kV - End Millbrook to Millbrook Tee 132kV) at 153.9 % (N-0 snapshot, bridge: no alternative path); after 90.6 %
- inferred feed 4: 132 kV line x1 Vineyard 132kV - Rouse Hill 132kV 7.13 km; demanded by L867 (Vineyard 132kV - Rouse Hill 132kV) at 153.1 % (N-0 snapshot); after 87.3 %

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: -510 MVAr at Bayswater 500kV
- inferred compensation 2: -330 MVAr at Wollar 500kV
- inferred compensation 3: -330 MVAr at Sydney South 132kV
- inferred compensation 4: +330 MVAr at Gin Gin 275kV
- inferred compensation 5: +320 MVAr at Boyne Island 275kV
- inferred compensation 6: -280 MVAr at Kemps Creek 500kV
- inferred compensation 7: +280 MVAr at Cherry Gardens 132kV
- inferred compensation 8: +260 MVAr at Tomago 330kV
- inferred compensation 9: -250 MVAr at Rookwood Road 330kV
- inferred compensation 10: +240 MVAr at South Pine 275kV
- inferred compensation 11: -230 MVAr at Bannaby 500kV
- inferred compensation 12: -200 MVAr at Holroyd 330kV
- inferred compensation 13: +200 MVAr at Halys 275kV
- inferred compensation 14: +200 MVAr at Ringwood 220kV
- inferred compensation 15: -190 MVAr at Heywood 500kV
