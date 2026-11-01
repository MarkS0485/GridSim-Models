# MODEL CARD: Canada Ontario 500-345-230-115 kV 2025-06-24 (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against operator study results. A solvable rough map of the Ontario grid (IESO / Hydro One, Eastern Interconnection: 500 / 230 / 115 kV) for one snapshot: OSM-mapped lines and stations (>= 100 kV), standard per-km parameters, NACEI / OSM plants, published system demand allocated by population. Use it to learn, compare and explore, not to plan or operate.

Round: r2. Frequency 60 Hz. Neighbouring systems are fixed boundary injections.

## What it is

- Snapshot: 2025-06-24 19:00 EST (hour ending 19), Ontario's 2025 peak hour (summer; the 2024-25 winter peak was 21,940 MW on 2025-01-22 hour 18) (published demand 24862.00 MW).
- Buses 1071 (54 generator terminal buses, 476 tee buses), branches 1563 (lines 1422, transformers 141), generators 87.
- Buses by kV: 500 kV 69, 345 kV 2, 230 kV 488, 115 kV 458, 13.8 kV 54.
- Dispatch 23298.0 MW (in-system plant) + boundary imports 1566.0 MW; demand 24864.0 MW (incl. boundary exports 1142.0 MW).
- Slack: 1 reference: Darlington.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1071 | 541 (50.5%) | 0 (0.0%) | 476 (44.4%) | 54 (5.0%) |
| Branches | 1563 | 0 (0.0%) | 1422 (91.0%) | 0 (0.0%) | 141 (9.0%) |
| Generators | 87 | 64 (73.6%) | 0 (0.0%) | 23 (26.4%) | 0 (0.0%) |
| Demand points | 317 | 0 (0.0%) | 0 (0.0%) | 317 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 268 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 268 (100.0%) |

Tag mapping: attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- OSM via adapt_osm (CA_ON): CA_ON: 1095 sites, 1462 branches, 1060 buses, 44 couplings, 163 branches dropped at a free end, None HVDC ways left out.
- HVDC converter sites (OSM substation=converter): 0; their AC buses removed: [] (ties are boundary injections).
- Islands 11, sizes [1017, 12, 6, 5, 5, 4, 3, 2, 2, 2]; main island kept (1017 buses, 476 tees); by kV {'115': 458, '230': 488, '500': 69, '345': 2}; route km {'500': 3028.3, '345': 4.4, '230': 10631.8, '115': 6096.3}; 494 lines floored to 0.5 km.
- Largest dropped islands: 12 buses near 45.036, -74.719 (Substation 1339055382 115 kV); 6 buses near 52.279, -82.008 (Substation 179552340 115 kV); 5 buses near 43.427, -80.444 (OH-UG Junction Tower #162 115 kV); 5 buses near 42.947, -81.187 (London Highbury TS 115 kV); 4 buses near 44.147, -77.058 (Substation 687194357 230 kV); 3 buses near 46.628, -84.425 (Prince Wind Substation 1 230 kV).
- Per-km parameters: 735 kV R 0.0117 X 0.3273 ohm/km B 5.061 uS/km, 6620 MVA (Quad 1355 kcmil ACSR (HQ 735 kV, OPAL-RT HYPERSIM example)); 500 kV R 0.0242 X 0.3493 ohm/km B 4.604 uS/km, 2572 MVA (Triple Rail 954 kcmil 45/7 ACSR); 345 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1183 MVA (Twin Rail 954 kcmil 45/7 ACSR); 315 kV R 0.0364 X 0.3713 ohm/km B 4.361 uS/km, 1080 MVA (Twin Rail 954 kcmil 45/7 ACSR); 230 kV R 0.0432 X 0.3623 ohm/km B 4.462 uS/km, 723 MVA (Twin Drake 795 kcmil 26/7 ACSR); 161 kV R 0.0864 X 0.4761 ohm/km B 3.436 uS/km, 253 MVA (Drake 795 kcmil 26/7 ACSR); 138 kV R 0.0864 X 0.4647 ohm/km B 3.523 uS/km, 217 MVA (Drake 795 kcmil 26/7 ACSR); 115 kV R 0.0864 X 0.4593 ohm/km B 3.566 uS/km, 181 MVA (Drake 795 kcmil 26/7 ACSR).
- Couplings: 87 synthetic transformers at OSM sites with two voltages, 2 units by HV class (735: 1650, 500: 750, 345 / 315: 600, 230: 300, below: 150 MVA each), x 12 % own rating.

## Generation and dispatch by fuel (MW)

| Fuel | Generators | Capacity in case | Dispatch |
|---|---:|---:|---:|
| biomass | 2 | 350.0 | 187.0 |
| gas | 19 | 8477.2 | 7293.0 |
| hydro | 34 | 7750.0 | 5580.0 |
| interconnector | 2 | 1566.0 | 1566.0 |
| nuclear | 5 | 13594.0 | 9592.0 |
| solar | 5 | 283.4 | 39.0 |
| wind | 20 | 3171.4 | 607.0 |

## Boundary injections (MW, + import)

| Tie | MW | Bus | Source |
|---|---:|---|---|
| Quebec (Outaouais back-to-back, PQ.AT) | 1216.0 | Orleans TS 230 kV (19.3 km) | IESO PUB_IntertieScheduleFlowYear_2025 PQ.AT flow, sign reversed |
| Quebec (Beauharnois units on the Ontario system, PQ.B5D.B31L) | 350.0 | Substation 92197103 230 kV (5.9 km) | IESO PUB_IntertieScheduleFlowYear_2025 PQ.B5D.B31L flow, sign reversed (St Lawrence) |
| New York (Niagara and St Lawrence ties) | -734.0 | Substation 158460657 230 kV (4.7 km) | IESO PUB_IntertieScheduleFlowYear_2025 NEW-YORK flow, sign reversed; all placed at Niagara (estimated split) |
| Michigan (Lambton, Keith, Scott ties) | -326.0 | Lambton 345kV Substation 230 kV (0.8 km) | IESO PUB_IntertieScheduleFlowYear_2025 MICHIGAN flow, sign reversed; placed at Lambton (estimated split) |
| Manitoba (Whiteshell - Kenora ties) | -31.0 | Substation 309376427 230 kV (38.5 km) | IESO PUB_IntertieScheduleFlowYear_2025 MANITOBA flow, sign reversed |
| Minnesota (Fort Frances tie) | -51.0 | Hydro One 230 kV (1.2 km) | IESO PUB_IntertieScheduleFlowYear_2025 MINNESOTA flow, sign reversed |

## Repairs (every change made so the case solves)

- seasonal line ratings: all 1422 overhead lines x 0.9439 (seasonal factor 0.9439 = JAO ratio summer 1.0000 / base 'interseason' 1.0594 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- synchronous plants of 20 MW or more behind 54 lumped GSUs (33524 MVA, x 13 % own rating, X/R 40, terminal 13.8 kV; synthetic), role pv at 1.02 pu, Q range -0.3 to +0.48 x MW (estimated); wind, solar, small plants and boundary imports pq with Q = 0
- slack: largest dispatched unit within 150 km of the demand centre (44.04, -79.33): Darlington at Bowmanville SS 500 kV 500kV gen bus, reactive band +/-20778 MVAr (synthetic)
- no radial-chain demand relief (India routine not used:
- line-end shunt reactors on 115 lines at 500 kV and above: 70% of each line's charging, 3398 MVAr in all, as fixed bus shunts at the two ends (physical rule; sizes estimated, synthetic) [VERIFY]
- reactive repair staged by load scaling: shunts placed at 0.20, 0.22, 0.24, 0.26, 0.28, 0.30, 0.32, 0.34, 0.36, 0.38, 0.40, 0.42, 0.44, 0.46, 0.48, 0.50, 0.52, 0.54, 0.56, 0.58, 0.60, 0.62, 0.64, 0.66, 0.68, 0.70, 0.72, 0.74, 0.76, 0.78, 0.80, 0.82, 0.84, 0.86, 0.88, 0.90, 0.92, 0.94, 0.96, 0.98, 1.00 x demand and dispatch in turn (estimated)
- reactive repair stopped early at some stage(s): pass limit 60 reached; one-stage repair stalled: shunts discarded, staged route used instead; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass 4: no damped step solves; 20 buses still outside; pass 1: no damped step solves; 20 buses still outside; pass 2: no damped step solves; 20 buses still outside; pass 1: no damped step solves; 20 buses still outside; pass 1: no damped step solves; 20 buses still outside; pass 5: no damped step solves; 20 buses still outside; pass 1: no damped step solves; 20 buses still outside; pass 1: no damped step solves; 20 buses still outside; pass 2: no damped step solves; 20 buses still outside
- bus shunts placed where the snapshot needs reactive support (1829 passes of a Newton solve without reactive limits): 64 reactors 990 MVAr, 123 capacitors 5780 MVAr (synthetic; no open reactive compensation list; 735 kV systems run large shunt reactors and SVCs / synchronous condensers): Substation 709037739 230 kV 230kV gen bus -40, Marathon TS 230 kV 230kV -40, Tee 230 kV t230_6 230kV -30, Substation 412084297 230 kV 230kV -30, Substation 331747300 230 kV 230kV -30, Substation 1350987223 115 kV 115kV -20, Substation 75151343 115 kV 115kV gen bus -20, Tee 115 kV t115_29 115kV -20, Substation 1434841653 115 kV 115kV -20, Tee 115 kV t115_26 115kV -20, Tee 115 kV t115_27 115kV -20, Marathon TS 115 kV 115kV -20, Substation 753689047 230 kV 230kV gen bus -20, Tee 230 kV t230_7 230kV -20, Wawa TS 230 kV 230kV -20, Substation 1422197422 115 kV 115kV -20, Substation 379628560 115 kV 115kV -20, Wawa TS 115 kV 115kV -20, Tee 230 kV t230_5 230kV -20, Lakehead TS 230 kV 230kV -20, Henvey Inlet Wind farm Substation 230 kV 230kV -20, Lakehead TS 115 kV 115kV -20, Tee 115 kV t115_17 115kV -20, Tee 115 kV t115_18 115kV -20, Tee 115 kV t115_19 115kV -20, Tee 115 kV t115_15 115kV -20, Parry Sound Switching Station 230 kV 230kV -20, Substation 493154346 230 kV 230kV -20, Substation 383372829 230 kV 230kV -10, Tee 230 kV t230_4 230kV -10, Hydro One 230 kV 230kV -10, Tee 115 kV t115_1 115kV -10, Substation 610225468 115 kV 115kV -10, Tee 115 kV t115_2 115kV -10, Substation 274903376 230 kV 230kV -10, Mackenzie TS 230 kV 230kV -10, Tee 230 kV t230_3 230kV -10, Dryden TS 230 kV 230kV -10, Substation 429900289 115 kV 115kV -10, Substation 430616479 115 kV 115kV -10, Substation 384187105 115 kV 115kV -10, McLean's Mountain CSS 115 kV 115kV -10, Espanola TS 115 kV 115kV -10, Tee 115 kV t115_43 115kV -10, Wallace TS 230 kV 230kV -10, Tee 230 kV t230_222 230kV -10, Tee 230 kV t230_219 230kV -10, Tee 230 kV t230_218 230kV -10, Minden TS 230 kV 230kV -10, Muskoka Transmission Station 230 kV 230kV -10, Tee 230 kV t230_160 230kV -10, Severn TS 230 kV 230kV -10, Mazinaw DS 230 kV 230kV -10, Tee 230 kV t230_217 230kV -10, Tee 230 kV t230_13 230kV -10, Tee 230 kV t230_14 230kV -10, Algoma TS 230 kV 230kV -10, Substation 1434596534 115 kV 115kV -10, Tee 230 kV t230_15 230kV -10, Victoria Mine Substation 230 kV 230kV -10, Substation 523652420 230 kV 230kV -10, Blind River DS 115 kV 115kV -10, Elliot Lake TS 115 kV 115kV -10, Substation 551947105 115 kV 115kV -10, Substation 409636566 230 kV 230kV +0, Substation 409636566 115 kV 115kV +0, Substation 610225474 115 kV 115kV +0, Substation 1434902888 115 kV 115kV +0, Substation 1434902889 115 kV 115kV +0, Tee 230 kV t230_2 230kV +0, Substation 309376427 115 kV 115kV +0, Substation 475644088 115 kV 115kV +0, Substation 1453237710 115 kV 115kV +0, Substation 1434871425 115 kV 115kV +0, Tee 115 kV t115_30 115kV +0, Tee 115 kV t115_28 115kV +0, Substation 19670836 115 kV 115kV +0, Manitoulin TS 115 kV 115kV +0, Substation 1434893709 115 kV 115kV +0, Tee 115 kV t115_45 115kV +0, Tee 115 kV t115_47 115kV +0, Substation 709037738 115 kV 115kV +0, Tee 115 kV t115_44 115kV +0, Substation 1421452420 115 kV 115kV +0, Substation 334269646 115 kV 115kV +0, Tee 115 kV t115_85 115kV +0, Substation 523652420 115 kV 115kV +0, Onaping Area M&M CTS 115 kV 115kV +0, Tee 115 kV t115_56 115kV +0, Tee 115 kV t115_79 115kV +0, Tee 115 kV t115_81 115kV +0, Substation 309376427 230 kV 230kV +10, Substation 1434843402 115 kV 115kV +10, Substation 623239753 115 kV 115kV +10, Domtar Espanola CGS 115 kV 115kV +10, Eacom Nairn CTS 115 kV 115kV +10, Substation 244354346 115 kV 115kV +10, Whitefish DS 115 kV 115kV +10, Toyota Woodstock TS 115 kV 115kV +10, Tee 115 kV t115_80 115kV +10, Substation 395444447 115 kV 115kV gen bus +10, Wendover Distribution Station 115 kV 115kV +10, Substation 1419748476 115 kV 115kV +10, Substation 1363778234 230 kV 230kV +10, Frood Stobie CTS 230 kV 230kV +10, Hanmer TS 230 kV 230kV +10, Tee 230 kV t230_58 230kV +10, Bramalea TS 230 kV 230kV +10, Substation 60833397 115 kV 115kV +10, Substation 142557684 230 kV 230kV +10, Substation 205715568 115 kV 115kV +10, Tee 115 kV t115_108 115kV +10, Tee 115 kV t115_107 115kV +10, Eglinton LRT substation 115 kV 115kV +10, Substation 466412245 115 kV 115kV +10, Substation 562965091 230 kV 230kV +10, A.W Manby TS 115 kV 115kV +10, Substation 489599153 230 kV 230kV +10, Orangeville TS 230 kV 230kV +10, Substation 1284518614 230 kV 230kV +10, Substation 611322612 230 kV 230kV +10, Substation 387355845 230 kV 230kV +10, London Wonderland TS 230 kV 230kV +10, Cambrian MTS 115 kV 115kV +10, Tee 115 kV t115_159 115kV +10, Tee 230 kV t230_31 230kV +10, Nepean TS 230 kV 230kV +10, Tee 230 kV t230_255 230kV +10, Merivale TS 230 kV 230kV +10, Substation 1434903216 115 kV 115kV +20, Tee 230 kV t230_135 230kV +20, Tee 230 kV t230_134 230kV +20, Substation 535376458 115 kV 115kV +20, Hawthorne TS 230 kV 230kV +20, Substation 274193423 230 kV 230kV +20, Substation 1436145474 230 kV 230kV +20, Port Hope Transformer Station 115 kV 115kV +20, Tee 115 kV t115_133 115kV +20, Tee 230 kV t230_142 230kV +20, Tee 230 kV t230_140 230kV +20, Tee 230 kV t230_182 230kV +20, Meadowvale TS 230 kV 230kV +20, Substation 53064768 230 kV 230kV +20, Tee 230 kV t230_136 230kV +20, Tee 230 kV t230_129 230kV +20, Woodstock TS 115 kV 115kV +30, Tee 230 kV t230_259 230kV +30, Nanticoke TS 500 kV 500kV +30, Middleport TS 500 kV 500kV +30, Essa TS 500 kV 500kV +30, Trafalgar TS 500 kV 500kV +30, Tee 500 kV t500_13 500kV +30, Substation 558611075 115 kV 115kV +30, Tee 230 kV t230_131 230kV +30, Substation 558723583 230 kV 230kV +30, Tee 230 kV t230_144 230kV +30, Tee 230 kV t230_141 230kV +30, Tee 230 kV t230_145 230kV +30, Substation 555409065 230 kV 230kV +30, Tee 230 kV t230_181 230kV +30, Paris TS 115 kV 115kV +40, Elmira Transformer Station 115 kV 115kV +40, Substation 233182676 115 kV 115kV +40, Substation 551675500 500 kV 500kV +40, Detweiler TS 230 kV 230kV +40, Clarke TS 230 kV 230kV +40, Substation 1375492405 230 kV 230kV +40, Substation 1375492404 230 kV 230kV +40, Tee 230 kV t230_153 230kV +40, Dundas TS 230 kV 230kV +40, Substation 1426162400 230 kV 230kV +40, Cambrian MTS 230 kV 230kV +50, Arrester Station 500 kV 500kV +50, Bramalea TS 230 kV 230kV gen bus +60, Tee 230 kV t230_133 230kV +60, Oakville TS #2 230 kV 230kV +60, Hurontario SS 230 kV 230kV +60, Howard Scheifele Transformer Station 230 kV 230kV +60, Waterloo Municipal Transformer Station 3 230 kV 230kV +60, Richview Transformer Station 230 kV 230kV +60, Fairchild TS 230 kV 230kV +60, Tee 230 kV t230_150 230kV +60, Tee 230 kV t230_161 230kV +60, Finch TS 230 kV 230kV +60, Tee 230 kV t230_148 230kV +60, Terry Fox MTS 500 kV 500kV +70, Substation 551927697 500 kV 500kV +70, Nobel SS 500 kV 500kV +80, Substation 1334955030 230 kV 230kV +80, Tee 230 kV t230_137 230kV +80, Ellwood MTS 230 kV 230kV +90, Substation 161324804 230 kV 230kV +90, Bathurst TS 230 kV 230kV +90, London Talbot TS 230 kV 230kV +90, Porcupine TS 500 kV 500kV +100, Albion TS 230 kV 230kV +100, Goreway TS 230 kV 230kV +100, Cherrywood TS 500 kV 500kV gen bus +100, Preston TS 230 kV 230kV +110, A.W Manby TS 230 kV 230kV +110, York Energy Centre 230 kV 230kV gen bus +110, Merivale TS 500 kV 500kV +110, Tee 500 kV t500_40 500kV +110, Claireville TS 500 kV 500kV gen bus +120, Lorne Park TS 230 kV 230kV +130, Applewood Junction 230 kV 230kV +130, J 230 kV 230kV +130, Milton SS 500 kV 500kV gen bus +130, Hawthorne TS 500 kV 500kV +140, Hanmer TS 500 kV 500kV +150, Substation 233182676 230 kV 230kV +150, Mount Pleasant TS 230 kV 230kV +160, Substation 1335301762 230 kV 230kV +200, Leaside Transformer Station 230 kV 230kV gen bus +240

## Round history

- r1: first build (owner's build-first instruction: r1 only). Reactive repair by fixed bus shunts only; no radial-chain demand relief; no value changed after a solver symptom.
- r2: loss accounting. The snapshot demand figures (Hydro-Quebec hourly demand; AESO Alberta Internal Load; BC Hydro balancing-authority load) are generation plus net interchange, so they already CONTAIN the transmission losses; r1 put the whole figure on the buses and dispatched plant to it, so the slack alone met the solved losses (Quebec 2,352.329 MW: slack GSU at Chateauguay 195.5 %; West 913.327 MW). The population demand rows are now scaled by (D - L) / D with L the r1 gridsim pf loss of the same system (estimated; [VERIFY] that the HQ open-data series includes losses). West: the West-only build rules are now in the West fit register.
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
- Demand: allocated load 23722.0 MW = IESO fuel output in the case + net intertie import; published Ontario Demand 24862.0 MW (1140.0 MW not in the fuel report / intertie flows).

## Sources

- OpenStreetMap power layer (lines, substations, plants >= 100 kV), Geofabrik provincial extracts 2026-10-30, via the shared the build pipeline OSM ingest and adapt_osm (OpenStreetMap contributors), ODbL 1.0
- Power Plants, 100 MW or more, North America (2017-08) (North American Cooperation on Energy Information (Natural Resources Canada)), Open Government Licence - Canada
- IESO public reports: hourly demand, generator output by fuel, intertie schedule and flow (Independent Electricity System Operator (Ontario)), IESO public reports (terms of use, ieso.ca)
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
$ gridsim pf canada-ontario-spine-500-230-115-r2   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Canada Ontario 500-345-230-115 kV 2025-06-24 (UnvalidatedAtScale) (1071 buses)
  converged in 8 iteration(s), mismatch 2.54E-011 pu   losses 581.002 MW / -1095.894 MVAr
  voltage range 0.9499 - 1.0200 pu
  lowest voltages:
      bus 116    0.9499 pu    -16.521 deg
      bus 78     0.9500 pu    -16.449 deg
      bus 76     0.9502 pu    -16.461 deg
      bus 218    0.9503 pu    -17.262 deg
      bus 389    0.9504 pu    -16.432 deg
      bus 385    0.9504 pu    -16.389 deg
      bus 145    0.9505 pu    -16.375 deg
      bus 390    0.9505 pu    -16.397 deg
      bus 386    0.9505 pu    -16.359 deg
      bus 373    0.9506 pu    -16.369 deg
      bus 132    0.9506 pu    -16.726 deg
      bus 599    0.9507 pu    -16.499 deg
(warm start baked into buses.json from that solve: that start took 8 Newton iterations)
(the build pipeline reading of the pf result) angle spread 91.234 deg; branches over 100 %: 2, over 80 %: 25; highest: L01323 (Hawthorne TS 230 kV 230kV - Orleans TS 230 kV 230kV) 154.9 %; L00971 (Substation 175815236 230 kV 230kV - Tee 230 kV t230_125 230kV) 140.1 %; L01354 (Bruce B Switchyard 500 kV 500kV - Tee 500 kV t500_4 500kV) 99.2 %; L00473 (Arnprior TS 115 kV 115kV - Tee 115 kV t115_153 115kV) 96.4 %; gsu:sw43812935_230 (Leaside Transformer Station 230 kV 230kV gen bus - Leaside Transformer Station 230 kV 230kV) 95.2 %; gsu:sw43746409_230 (Bramalea TS 230 kV 230kV gen bus - Bramalea TS 230 kV 230kV) 94.7 %; gsu:sw762722931_230 (York Energy Centre 230 kV 230kV gen bus - York Energy Centre 230 kV 230kV) 91.5 %; gsu:sw395444447_115 (Substation 395444447 115 kV 115kV gen bus - Substation 395444447 115 kV 115kV) 89.1 %
$ gridsim pf canada-ontario-spine-500-230-115-r2 (warm start)   (exit 0, 0.6 s)
Power flow - Canada Ontario 500-345-230-115 kV 2025-06-24 (UnvalidatedAtScale) (1071 buses)
  converged in 4 iteration(s), mismatch 4.48E-011 pu   losses 581.002 MW / -1095.894 MVAr
  voltage range 0.9499 - 1.0200 pu
  lowest voltages:
      bus 116    0.9499 pu    -16.521 deg
      bus 78     0.9500 pu    -16.449 deg
      bus 76     0.9502 pu    -16.461 deg
      bus 218    0.9503 pu    -17.262 deg
      bus 389    0.9504 pu    -16.432 deg
      bus 385    0.9504 pu    -16.389 deg
      bus 145    0.9505 pu    -16.375 deg
      bus 390    0.9505 pu    -16.397 deg
      bus 386    0.9505 pu    -16.359 deg
      bus 373    0.9506 pu    -16.369 deg
      bus 132    0.9506 pu    -16.726 deg
      bus 599    0.9507 pu    -16.499 deg
$ gridsim physics-check canada-ontario-spine-500-230-115-r2   (exit 0, 0.5 s)
Physics-law audit  -  canada-ontario-spine-500-230-115-r2  (1071 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.13E-009 | MW | independent dissipation 581.001740 MW (branch 581.0017 + shunt 0.0000) vs reported loss 581.001740 MW |
| 2 | Ohm's law | Holds | 1.73E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.12E-009 | MW | total network loss 581.001740 MW vs reported 581.001740 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 1.85E-012 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.39E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 3.89E-009 | MVA | same residual as law 6, reactive component included at 1018 PQ bus(es), by the bus types the solve ended with; 1 of them declared PV and solved as PQ (1 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 60 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses canada-ontario-spine-500-230-115-r2   (exit 0, 8.8 s)
(full sweep in iec60909_all_buses.txt) 500 kV (29): Ik'' max 57.66 kA (Cherrywood TS 500 kV 500kV), min 5.95 kA (Porcupine TS 500 kV 500kV), median 21.80 kA; 345 kV (2): Ik'' max 18.21 kA (Lambton 345kV Substation 345 kV 345kV), min 17.53 kA (Substation 564807905 345 kV 345kV), median 17.87 kA; 230 kV (229): Ik'' max 85.39 kA (Cherrywood TS 230 kV 230kV), min 1.42 kA (Substation 383372829 230 kV 230kV), median 18.30 kA; 115 kV (281): Ik'' max 49.24 kA (Beach TS 115 kV 115kV), min 0.91 kA (Substation 1128248988 115 kV 115kV), median 8.81 kA
```
