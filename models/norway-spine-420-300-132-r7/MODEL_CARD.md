# Norway 420/300/132 kV winter peak 2026-01-07 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against Statnett study results. A solvable rough map of the Norwegian 420 / 300 kV transmission grid and the 132 / 110 kV regional grid for one winter-peak snapshot: NVE line routes and stations (connectivity recovered from geometry), standard per-km parameters, NVE hydro and wind registers, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r6. Frequency 50 Hz (Nordic synchronous area; Sweden, Finland and the HVDC links are fixed boundary injections).

## What it is

- Snapshot: 2026-01-07 15:30 UTC (16:30 CET), the highest 'Load' quarter-hour of Nov 2025 - Mar 2026 (energy-charts) (energy-charts: load 25389.3 MW).
- Buses 1349 (9 cross-border boundary buses, 263 generator terminal buses, 343 tee buses), branches 2004 (lines 1628, transformers 376), generators 802.
- Buses by kV: 420 kV 181, 300 kV 185, 220 kV 4, 132 kV 670, 110 kV 46, 13.8 kV 263.
- Dispatch 27108.6 MW (Norwegian plant) + boundary imports 199.0 MW; demand 26803.8 MW (incl. boundary exports 2118.0 MW).
- Slack: 1 reference: Kvilldal.
- Islands before selection 5; buses dropped 12.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1349 | 729 (54.0%) | 0 (0.0%) | 343 (25.4%) | 277 (20.5%) |
| Branches | 2004 | 0 (0.0%) | 1552 (77.4%) | 68 (3.4%) | 384 (19.2%) |
| Generators | 802 | 408 (50.9%) | 0 (0.0%) | 394 (49.1%) | 0 (0.0%) |
| Demand points | 463 | 0 (0.0%) | 0 (0.0%) | 463 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 70 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 70 (100.0%) |

Station buses are 'attested' (NVE station position); tees are 'estimated'; boundary and generator terminal buses 'synthetic'. Lines are 'derived' (NVE route length x standard per-km values; R, X, B and rating are flagged estimated in the model tables). Tag mapping: attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- NVE Nettanlegg utbygd: 2255 AC line parts at 110-420 kV kept (275 exact duplicates dropped; out of scope by voltage: {'regional 0 kV': 1, 'regional 22 kV': 8, 'regional 33 kV': 4, 'regional 36 kV': 16, 'regional 45 kV': 22, 'regional 47 kV': 325, 'regional 50 kV': 135, 'regional 52 kV': 106, 'regional 55 kV': 2, 'regional 60 kV': 17, 'regional 66 kV': 1470, 'regional 72 kV': 10, 'regional 73 kV': 46, 'regional None kV': 13, 'sea_cable 0 kV': 225, 'sea_cable 1 kV': 30, 'sea_cable 10 kV': 5, 'sea_cable 11 kV': 10, 'sea_cable 12 kV': 40, 'sea_cable 16 kV': 10, 'sea_cable 22 kV': 125, 'sea_cable 33 kV': 2, 'sea_cable 34 kV': 2, 'sea_cable 50 kV': 6, 'sea_cable 52 kV': 8, 'sea_cable 66 kV': 33, 'sea_cable None kV': 27, 'transmission 24 kV': 2, 'transmission 250 kV': 2, 'transmission 350 kV': 3, 'transmission 525 kV': 1}).
- Connectivity from geometry: 758 parts split at tees, 434 mid-route joints contracted, 78 dead ends snapped to a station within 3 km, 69 dead-end sections pruned (km by kV {'132': 528.29, '420': 37.68}).
- Sites: 1194 NVE station points merged into 1075 station sites, plus 546 power-station positions (NVE hydro >= 5 MW and wind farms) used as line-end targets.
- Buses in the main island: 1086 (729 station / plant buses, 343 tees, 9 boundary); by kV {'420': 181, '300': 185, '220': 4, '132': 670, '110': 46}; line km by kV {'420': 6674.9, '300': 4312.3, '220': 86.2, '132': 10928.6, '110': 502.6}, sea cable 104.2 km.
- Island bridges (synthetic underground cables, estimated): 11: J3829:132 - J3224:132 132 kV 0.14 km crow-fly (island of 3 buses); J4201:132 - J2226:132 132 kV 0.16 km crow-fly (island of 2 buses); PH209:132 - S1028:132 132 kV 0.54 km crow-fly (island of 12 buses); S0483:132 - S1013:132 132 kV 1.25 km crow-fly (island of 4 buses); S0645:132 - S0551:132 132 kV 1.75 km crow-fly (island of 2 buses); S0985:300 - S0984:300 300 kV 2.03 km crow-fly (island of 2 buses); S0082:132 - S0129:132 132 kV 4.07 km crow-fly (island of 2 buses); J5104:132 - J2982:132 132 kV 4.51 km crow-fly (island of 8 buses); PH415:420 - S0968:420 420 kV 6.33 km crow-fly (island of 2 buses); PH228:132 - S0726:132 132 kV 6.59 km crow-fly (island of 5 buses); S1052:132 - J2618:132 132 kV 7.96 km crow-fly (island of 3 buses)
- Islands before selection 5; dropped 4 with 12 buses: [{'buses': 4, 'kv': {'132': 4}, 'stations': ['NVE station 687', 'NVE station 689', 'NVE station 696', 'NVE station 697'], 'at': [69.594, 19.515]}, {'buses': 4, 'kv': {'132': 4}, 'stations': ['NVE station 669', 'NVE station 671', 'NVE station 672', 'NVE station 683'], 'at': [69.615, 18.452]}, {'buses': 2, 'kv': {'132': 2}, 'stations': ['Herand power station', 'Krossdalselvi power station'], 'at': [60.316, 6.369]}, {'buses': 2, 'kv': {'132': 2}, 'stations': ['NVE station 820', 'NVE station 824'], 'at': [66.022, 12.812]}].
- Per-km parameters (pandapower standard types, estimated): oh 420: R 0.0210 X 0.250 ohm/km, C 14.6 nF/km, Imax 2.300 kA (679-AL1/86-ST1A 380.0, duplex); oh 300: R 0.0210 X 0.275 ohm/km, C 11.7 nF/km, Imax 2.300 kA (679-AL1/86-ST1A 220.0 (nearest class), duplex); oh 220: R 0.0590 X 0.285 ohm/km, C 10 nF/km, Imax 0.960 kA (490-AL1/64-ST1A 220.0, simplex); oh 132: R 0.1188 X 0.390 ohm/km, C 9 nF/km, Imax 0.645 kA (243-AL1/39-ST1A 110.0 (nearest class), simplex); oh 110: R 0.1188 X 0.390 ohm/km, C 9 nF/km, Imax 0.645 kA (243-AL1/39-ST1A 110.0, simplex); cable 132: R 0.0600 X 0.144 ohm/km, C 144 nF/km, Imax 0.588 kA (N2XS(FL)2Y 1x300 RM/35 64/110 kV); cable 110: R 0.0600 X 0.144 ohm/km, C 144 nF/km, Imax 0.588 kA (N2XS(FL)2Y 1x300 RM/35 64/110 kV); cable 220: R 0.0300 X 0.144 ohm/km, C 144 nF/km, Imax 1.000 kA (stand-in (110 kV 1x300 cable, R/2, 1.0 kA)); cable 300: R 0.0300 X 0.144 ohm/km, C 144 nF/km, Imax 1.000 kA (stand-in (110 kV 1x300 cable, R/2, 1.0 kA)); cable 420: R 0.0300 X 0.144 ohm/km, C 144 nF/km, Imax 1.000 kA (stand-in (110 kV 1x300 cable, R/2, 1.0 kA))
- Transformers: 113 synthetic couplings at multi-voltage sites (each voltage to the next higher present), sized to the lower side's line rating (100-2000 MVA), x 12 % own rating.

## Generation and dispatch by group (MW)

| Group | Units / plants | Capacity in case | Dispatch |
|---|---:|---:|---:|
| boundary | 2 | 199.0 | 199.0 |
| reservoir | 346 | 30495.6 | 21784.9 |
| ror | 1476 | 3639.5 | 2772.9 |
| wind | 62 | 5015.7 | 2550.8 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| SE | -81.2 | Sweden equivalent 1 (near Brekke power station) [SE] (AC ties: -0.406 GW in equal shares over 5 Swedish equivalent nodes) |
| SE | -81.2 | Sweden equivalent 2 (near Marker wind farm) [SE] (AC ties: -0.406 GW in equal shares over 5 Swedish equivalent nodes) |
| SE | -81.2 | Sweden equivalent 3 (near Vessingfoss power station) [SE] (AC ties: -0.406 GW in equal shares over 5 Swedish equivalent nodes) |
| SE | -81.2 | Sweden equivalent 4 (near Molnhusbekken power station) [SE] (AC ties: -0.406 GW in equal shares over 5 Swedish equivalent nodes) |
| SE | -81.2 | Sweden equivalent 5 (near Ofoten) [SE] (AC ties: -0.406 GW in equal shares over 5 Swedish equivalent nodes) |
| FI | 19.0 | Tana Bru border [FI] (AC ties: +0.019 GW split by tie rating (366 of 366 MVA)) |
| DK | -208.0 | Kristiansand (HVDC Skagerrak 1-4 (1,700 MW) [VERIFY rating] at Kristiansand 420 kV) |
| NL | -149.0 | Feda (HVDC NorNed (700 MW) [VERIFY rating] at Feda 300 kV) |
| DE | 180.0 | Ertsmyra (HVDC NordLink (1,400 MW) [VERIFY rating] at Ertsmyra 420 kV) |
| GB | -1355.0 | Kvilldal (HVDC North Sea Link (1,400 MW) [VERIFY rating] at Kvilldal 420 kV) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 1608 overhead lines (cable sections kept static, branch = min of sections); per line in ambient_ratings.json
- hydro plants of 10 MW or more moved behind 263 lumped GSUs (33884 MVA, x 13 % own rating, X/R 40, terminal 13.8 kV; synthetic), role pv at 1.02 pu, Q range -0.3 to +0.48 x MW (estimated)
- 1476 small hydro plants (< 10 MW, 3639.5 MW) aggregated per host bus into 392 fixed injections (pq, Q = 0); wind farms pq with Q = 0
- slack: largest dispatched 420 kV hydro unit Kvilldal at Kvilldal 420kV gen bus, reactive band +/-10000 MVAr (synthetic)
- radial-chain demand relief OFF (round 4): demand stays where it was allocated
- bus shunts placed where the snapshot needs reactive support (11 passes of a Newton solve without reactive limits): 22 reactors 2970 MVAr, 44 capacitors 2150 MVAr (synthetic; NVE publishes no reactive compensation; Statnett runs many 420 / 300 kV shunt reactors and SVCs): Sweden equivalent 4 (near Molnhusbekken power station) [SE] 420kV -600, Sweden equivalent 3 (near Vessingfoss power station) [SE] 420kV -350, Vessingfoss power station border [SE] 420kV -350, Nea 420kV -210, Ofoten 420kV gen bus -110, Sweden equivalent 5 (near Ofoten) [SE] 420kV -100, Ofoten border [SE] 420kV -100, Nea 420kV gen bus -90, Ofoten 420kV -90, T Rombak 420kV -90, T Rombak #2 420kV -90, T Sildvik #2 420kV -90, T Sildvik 420kV -90, Kvandal 420kV -90, T Skarelva power station #2 420kV -90, T Skarelva power station 420kV -90, Balsfjord 420kV -80, Bardufoss 420kV -80, Vinnelys 420kV -80, T Kvalsunddalen #2 420kV -80, Varangerbotn 132kV -10, Tana Bru 132kV -10, Raggovidda wind farm 132kV +0, T Raggovidda wind farm 132kV +0, Tana Bru border [FI] 220kV +0, Varangerbotn 220kV +0, NVE station 272 132kV +10, NVE station 270 132kV +10, Kvitfossen 132kV +10, Melbu 132kV +10, Stokmarknes 132kV +10, Skagen 132kV +10, Sortland 132kV +10, NVE station 353 132kV +10, Hinnoy 132kV +10, T Djupfjord I power station 132kV +10, T Solum #6 132kV +10, T Solum #2 132kV +10, T Solum #3 132kV +10, T Solum 132kV +10, T Solum #5 132kV +10, NVE station 724 132kV +10, NVE station 273 132kV +20, Arna 300kV +20, Fana 300kV +20, Ljosoysundet 300kV +20, Arna #2 300kV +20, T Langedalen 300kV +20, T Arnavagen 300kV +20, N.Blomoy 300kV +30, Kollsnes 300kV +30, Breivik 300kV +40, Solsvik 300kV +40, Vardal 300kV +60, Vang 300kV +60, Frogner 300kV +70, Sylling 300kV +70, Minne 300kV +70, Hadeland 300kV +80, Roa 300kV +80, Roykas 300kV +90, Litle Sotra 300kV +90, Solum 132kV +90, Frogner 300kV gen bus +100, Furuset 300kV +110, Hamang 300kV +110, Ulven 300kV +120, Baerum 300kV +130, Smestad 300kV +190, Sogn 300kV +190

## Round history (the solver's findings that drove each round)

- r1: first build; reactive repair by fixed bus shunts only (no other change). Before the first solve two build-time fixes: population was first put on the nearest 132 / 110 kV bus (all of Oslo, 6,565 MW, on Abildso 132 kV) and is now shared by the stations within 20 km; Sweden was first independent fixed injections per tie, and the no-limit Newton failed above 0.5 x snapshot (angle spread 96 deg), so the Swedish tie ends are joined by a synthetic 420 kV equivalent.
- r1 solve: pf 10 iterations flat (4 warm), V 0.9491-1.1255 pu (Kollsnes 132 kV highest), losses 1,188.508 MW, angle spread 133.530 deg (Finnmark +91 deg, Asker / Baerum 132 kV -42 deg), 60 branches over 100 % (worst 132 kV round Hasle, Sylling, Solum, Asker: up to 452.1 %), radial relief 4,160 MW, shunts 1,370 MVAr reactors / 6,490 MVAr capacitors (repair hit its pass limit at 4 stages), IEC 60909 420 kV median 16.35 kA.
- r2 changes: (1) population is shared by the 300 / 420 kV stations within 20 km when there are any; (2) nine curated flat industrial loads, 2,900 MW (aluminium smelters, Kollsnes, Johan Sverdrup power from shore; the build rules, [VERIFY]); (3) the 132 kV Swedish ties are left open instead of joining the Swedish equivalent. Before the r2 build solved, two topology fixes: (4) gap closing - dead ends are joined to the station named at an end of their NVE line within 30 km, or to a dead end of the same line name, instead of being pruned; (5) name-implied links - a line that stops at a station that is not one of its named ends, and loose ends of the same line, are joined within 30 km (Lindas - Kollsnes, Litle Sotra - Kollsnes; cables NVE leaves out).
- r2 solve: pf 10 iterations flat (4 warm), V 0.9369-1.1451 pu (Vesteralen 132 kV highest, Solum 132 kV lowest), losses 952.916 MW, angle spread 125.221 deg (Finnmark gen buses +104.6 deg, Smestad 300 kV -20.6 deg), 27 branches over 100 % (Hasle 132 kV area up to 347.4 %), radial relief 1,397 MW, shunts 310 MVAr reactors / 4,070 MVAr capacitors (repair hit its 60-pass limit), IEC 60909 420 kV median 17.49 kA.
- Cause of the Hasle overloads: NVE's Vannkraftverk layer lists some plants once per powerhouse point (Vamma 344 MW three times on Vammafossen 132 kV); 1,934.14 MW was double counted (the build pipeline).
- r3 changes: (1) one hydro row per NVE plant number (bug fix); (2) a second reactive-repair sweep after the staged repair (build.SECOND_SWEEP). No rating, impedance or coupling size changed (brief: no fitting).
- r3 solve: pf 10 iterations flat (4 warm), V 0.9509-1.0377 pu, losses 895.008 MW, angle spread 129.353 deg, 22 branches over 100 % (Solum 132 kV 234.4 %, Holsbru - NVE station 748 132 kV 217.1 %, Dokka - By 172.8 %, Hasle 132 kV area up to 170.8 %), shunts 320 MVAr reactors / 4,070 MVAr capacitors (the staged repair finished in 8 passes, so the second sweep did not run), IEC 60909 420 kV median 17.46 kA.
- Cause of the Holsbru overload: the radial-chain relief moved the Hydro Ardal smelter (330 MW) off its 132 kV chain but left Tyin (374 MW) on it, so the chain exported at 217 %.
- r4 change: radial-chain demand relief OFF (build.RADIAL_RELIEF; it changes demand because of a rating, which the brief forbids). Nothing else changed.
- r4 solve: PASS, 23 branches over 100 % at 132 kV, angle spread about 130 deg (Finnmark / northern export).
- Found: (1) code bug - the synthetic Swedish equivalent's SE_PARALLEL = 4 never reached the case (the lines table carried it only as a 'circuits' column that a build step does not use), so the stand-in ran as ONE 420 kV circuit; (2) NVE draws parallel circuits as separate objects with identical geometry and a circuit number in the name ('...-1' / '-2', 'L1' / 'L2'), and r1-r4 dropped them as duplicates.
- r5 changes: APPLY_PARALLEL (an n-circuit edge is one equivalent branch, R and X / n, B and rating x n) and NVE_PARALLEL (circuit count = distinct circuit numbers in the names of an identical-geometry group: 15 lines at 132 kV now run as double circuits). Both are corrections to what the data and the earlier rounds' documentation say, not values tuned to the solve.

## Values set after a solver symptom (brief: no fitting to the solver)

- the build rules = 500 MVA floor for 300 / 420 kV couplings (set in r1 after Strinda 300/132 kV came out at 150 MVA and overloaded). Basis: 'two units of about 250 MVA, typical of Statnett stations' - NOT a cited source. The couplings are tagged synthetic.
- topology Swedish equivalent (r1, after the no-limit Newton failed above 0.5 x snapshot): a synthetic 420 kV chain joining the Swedish ends of the AC ties, SE_PARALLEL = 4 parallel duplex circuits. Physical rule: northern Norway's surplus also reaches southern Norway through Sweden; the circuit count is NOT sourced. Tagged synthetic. Not tuned since (the r2 angle spread did not change it).
- electrify population spread (r1 build-time): places shared by stations within 20 km, weight 1/(d+2 km), instead of the nearest 132 / 110 kV bus (all of Oslo, 6,565 MW, on one bus). Physical rule: city demand is fed through many stations; the 20 km and the weight are not sourced (estimated).
- the build rules (r2, after 132 kV overloads round Oslo): places within 20 km of a 300 / 420 kV station load those stations. Physical rule: NVE leaves out the city cable networks below them, so the 132 kV stations there have no modelled feed (estimated).
- the build rules = 220 (r2): the three 132 kV Swedish ties are open boundary buses. Basis: claimed operating practice (radial / open 132 kV ties), NOT sourced: [VERIFY]; the boundary buses are synthetic.
- build radial-chain demand relief (India routine, r1-r3): demand moved off radial chains above 60 % of the feeding branch rating - a demand weight changed because of a rating, i.e. fitting; switched OFF in r4.
- build: a second reactive-repair sweep after the staged repair (r3, after the r2 repair hit its 60-pass limit). The shunts are synthetic repairs in every round.

## Known gaps

- No zonal (NO1-NO5) dispatch or demand: energy-charts offers national series only; hydro is dispatched pro rata to capacity within two groups (reservoir / pumped storage, small run of river), wind pro rata.
- Demand is allocated by population only; Norway's large flat industrial loads (aluminium smelters, ferroalloys, petroleum electrification at Kollsnes, Kaarstoe, Haugsneset, Melkoeya) are not placed ([VERIFY]).
- Underground cables are not in NVE's dataset (Oslo, Bergen, Stavanger city cables): islands within 10 km are bridged by synthetic cables, others dropped with their demand moved to the main island's buses by population.
- 66 kV and lower regional networks are not modelled; 132 kV pockets fed only through 66 kV are lost or bridged.
- Circuit counts are not in NVE: each drawn line is one circuit (double-circuit towers drawn once are under-counted).
- Line R / X / B and ratings are standard per-km types by voltage, not the operators' values; transformer sizes are synthetic; no reactive compensation is published, the bus shunts are fixed repairs.
- Sweden and Finland are fixed boundary injections at the border (energy-charts physical flows), split over the AC ties by their (standard) rating; no foreign network and no fault infeed from abroad.
- HVDC link ratings in the notes are public figures recalled, not sourced ([VERIFY]); only the snapshot flow is used.
- Thermal plant (gas 143.7, waste 39.8, other renewables 63.0 MW at the snapshot) is not modelled; it nets out of demand.

## Sources

- Nettanlegg utbygd (transmission and regional overhead lines, sea cables, transformer stations), ArcGIS service Nettanlegg5, fetched 2026-10-31 (Norges vassdrags- og energidirektorat (NVE)), Norsk lisens for offentlige data (NLOD) 1.0
- Vannkraftverk (hydropower plants: position, type, maximum output), service Vannkraft1 (NVE), NLOD 1.0
- Vindkraftverk utbygd (wind farms in operation: position, MW), service Vindkraft2 (NVE), NLOD 2.0
- Public net generation by type, load and cross-border physical flows, Norway, 2026-01-07 15:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- GeoNames Norway populated places (population, position) (GeoNames), CC BY 4.0
- pandapower standard line types (per-km R, X, C, Imax; data from Oeding / Oswald) (pandapower (Fraunhofer IEE / University of Kassel)), BSD-3-Clause
- Model assembly steps: connectivity from geometry, tees, island bridges, couplings, GSUs, placement, dispatch, demand allocation, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries NOR ADM1 (Kartverket), CC BY 4.0: county shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: Norway outline in geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf norway-spine-420-300-132-r6   (flat start: vm 1, vaDeg 0; exit 0, 0.9 s)
Power flow - Norway 420/300/132 kV winter peak 2026-01-07 (UnvalidatedAtScale) (1349 buses)
  converged in 8 iteration(s), mismatch 4.44E-011 pu   losses 737.799 MW / -1508.343 MVAr
  voltage range 0.9499 - 1.0492 pu
  lowest voltages:
      bus 876    0.9499 pu    -19.293 deg
      bus 277    0.9511 pu    -20.998 deg
      bus 286    0.9511 pu    -21.059 deg
      bus 276    0.9519 pu    -23.082 deg
      bus 821    0.9533 pu      4.044 deg
      bus 360    0.9536 pu    -18.179 deg
      bus 287    0.9541 pu    -21.871 deg
      bus 359    0.9542 pu    -19.810 deg
      bus 811    0.9547 pu      4.290 deg
      bus 274    0.9568 pu    -20.498 deg
      bus 822    0.9580 pu      4.672 deg
      bus 812    0.9585 pu      4.728 deg
(warm start baked into buses.json from that solve: that start took 8 Newton iterations)
(the build pipeline reading of the pf result) angle spread 90.028 deg; branches over 100 %: 13, over 80 %: 34; highest: L1891 (Solum 132kV - T Solum #6 132kV) 194.9 %; L1998 (T Solum #6 132kV - T Klosterfoss power station #3 132kV) 171.5 %; L2202 (Fellesanlegget Kykkelsrud-Fossumfoss power station 132kV - Vammafossen 132kV) 170.6 %; L746 (Dokka Trsf.St 132kV - By 132kV) 143.4 %; L1599 (T Hasle #2 132kV - Vammafossen 132kV) 131.0 %; L1868 (T Hasle #2 132kV - Vammafossen 132kV) 131.0 %; L126 (Hamang 300kV - Baerum 300kV) 125.1 %; L1050 (T Hasle 132kV - T Hasle #2 132kV) 124.9 %
$ gridsim pf norway-spine-420-300-132-r6 (warm start)   (exit 0, 0.7 s)
Power flow - Norway 420/300/132 kV winter peak 2026-01-07 (UnvalidatedAtScale) (1349 buses)
  converged in 4 iteration(s), mismatch 4.44E-011 pu   losses 737.799 MW / -1508.343 MVAr
  voltage range 0.9499 - 1.0492 pu
  lowest voltages:
      bus 876    0.9499 pu    -19.293 deg
      bus 277    0.9511 pu    -20.998 deg
      bus 286    0.9511 pu    -21.059 deg
      bus 276    0.9519 pu    -23.082 deg
      bus 821    0.9533 pu      4.044 deg
      bus 360    0.9536 pu    -18.179 deg
      bus 287    0.9541 pu    -21.871 deg
      bus 359    0.9542 pu    -19.810 deg
      bus 811    0.9547 pu      4.290 deg
      bus 274    0.9568 pu    -20.498 deg
      bus 822    0.9580 pu      4.672 deg
      bus 812    0.9585 pu      4.728 deg
$ gridsim physics-check norway-spine-420-300-132-r6   (exit 0, 0.8 s)
Physics-law audit  -  norway-spine-420-300-132-r6  (1349 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.12E-009 | MW | independent dissipation 737.799205 MW (branch 737.7992 + shunt 0.0000) vs reported loss 737.799205 MW |
| 2 | Ohm's law | Holds | 3.76E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.12E-009 | MW | total network loss 737.799205 MW vs reported 737.799205 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.45E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 4.44E-009 | MVA | same residual as law 6, reactive component included at 1088 PQ bus(es), by the bus types the solve ended with; 2 of them declared PV and solved as PQ (2 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses norway-spine-420-300-132-r6   (exit 0, 12.2 s)
(full sweep in iec60909_all_buses.txt) 420 kV stations (88): Ik'' max 39.47 kA (Saurdal 420kV), min 3.53 kA (Hyggevatn 420kV), median 18.91 kA; 300 kV stations (139): Ik'' max 37.21 kA (Sauda 300kV), min 6.46 kA (Sogn 300kV), median 18.07 kA; 220 kV stations (2): Ik'' max 12.07 kA (Nedre Rossaga 220kV), min 1.90 kA (Varangerbotn 220kV), median 6.99 kA; 132 kV stations (462): Ik'' max 47.34 kA (Ringerike 132kV), min 2.09 kA (Raggovidda wind farm 132kV), median 11.40 kA; 110 kV stations (38): Ik'' max 40.99 kA (Feda 110kV), min 1.56 kA (8001 110kV), median 11.84 kA
```

## Inference round norway-spine-420-300-132-r7 (base norway-spine-420-300-132-r6, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 2 (3 circuits / units, 43.49 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 52 sites, 1840 MVAr capacitive / 2710 MVAr inductive, replacing the generic repair (66 shunts, 2150 / 2970 MVAr) (mode 'in place, base taps').
- Taps: 0 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 2; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 8 | 6 |
| iterations_warm | 4 | 1 |
| loss_mw | 737.799 | 719.232 |
| vmin_pu | 0.950 | 0.951 |
| vmax_pu | 1.049 | 1.050 |
| angle_spread_deg | 85.446 | 83.566 |
| over_100 | 13 | 10 |
| over_120 | 10 | 7 |
| over_140 | 4 | 2 |
| auto_cap_mvar | 2150.000 | 0 |
| auto_reactor_mvar | 2970.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 4550.000 |
| units_held_at_q_limit | 2 | None |
| cpf_lambda | 1.150 | 1.154 |
| physics_pass | True | True |

Worst after: 170.7 % L2202 (Fellesanlegget Kykkelsrud-Fossumfoss power station 132kV - Vammafossen 132kV); 143.4 % L746 (Dokka Trsf.St 132kV - By 132kV); 131.0 % L1599 (T Hasle #2 132kV - Vammafossen 132kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 112.3 % T68 (Hasle 300kV - Hasle 132kV)
- 111.2 % L2198 (Madla 300kV - Grannes 300kV)
- 108.6 % L1517 (NVE station 661 132kV - Svartisen 132kV)

Inferred feeds:

- inferred feed 1: 132 kV line x2 Porsgrunn 132kV - Solum 132kV 11.62 km; demanded by L1891 (Solum 132kV - T Solum #6 132kV) at 194.9 % (N-0 snapshot); after 72.6 %
- inferred feed 2: 300 kV line x1 Sylling 300kV - Baerum 300kV 20.25 km; demanded by L126 (Hamang 300kV - Baerum 300kV) at 125.1 % (N-0 snapshot, bridge: no alternative path); after 67.7 %

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: -600 MVAr at Sweden equivalent 4 (near Molnhusbekken power station) [SE] 420kV
- inferred compensation 2: -350 MVAr at Sweden equivalent 3 (near Vessingfoss power station) [SE] 420kV
- inferred compensation 3: -350 MVAr at Vessingfoss power station border [SE] 420kV
- inferred compensation 4: -290 MVAr at Nea 420kV
- inferred compensation 5: -200 MVAr at Ofoten 420kV
- inferred compensation 6: +190 MVAr at Smestad 300kV
- inferred compensation 7: +190 MVAr at Sogn 300kV
- inferred compensation 8: +170 MVAr at Frogner 300kV
- inferred compensation 9: +130 MVAr at Baerum 300kV
- inferred compensation 10: +120 MVAr at Ulven 300kV
- inferred compensation 11: +110 MVAr at Furuset 300kV
- inferred compensation 12: +110 MVAr at Hamang 300kV
- inferred compensation 13: -100 MVAr at Sweden equivalent 5 (near Ofoten) [SE] 420kV
- inferred compensation 14: -100 MVAr at Ofoten border [SE] 420kV
- inferred compensation 15: -90 MVAr at T Skarelva power station 420kV
