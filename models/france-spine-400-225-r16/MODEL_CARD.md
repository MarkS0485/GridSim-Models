# MODEL CARD: France transmission 400/225 kV winter peak 2026-01-06 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official French study results. A solvable rough map of the French 225/400 kV transmission grid for one winter snapshot: real TSO impedances and ratings (JAO, RTE rows), register-based generation (ODRE), allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Round: r10.
- Snapshot: 2026-01-06 09:00 UTC (10:00 CET), the highest consolidated half-hour of French consumption in winter 2025-26 (eCO2mix: consumption 90236.0 MW; production 82828.0 MW; net physical import 7452.0 MW).
- Buses 2128 (3 tee junctions, 14 cross-border boundary buses, 888 generator / embedded buses), branches 3059 (lines 1929, transformers 1130), generators 6195.
- Buses by kV: 400 kV 190, 225 kV 1050, 63 kV 743, 21 kV 145.
- Dispatch 82828.0 MW (French plant) + boundary imports 7568.7 MW; demand 87982.7 MW (incl. boundary exports 116.7 MW and pumping 29.0 MW; consumption less a losses allowance of 2400 MW).
- Slack: 1 reference: CIVAUN01 - GROUPE 01 DE LA CENTRALE NUCLEAIRE DE CIVAUX.
- Islands before selection 2; buses dropped 3.
- Corsica is not modelled (not on the mainland 400 kV grid; outside the eCO2mix national perimeter); it appears only in the geography outline.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 2128 | 0 (0.0%) | 0 (0.0%) | 1222 (57.4%) | 906 (42.6%) |
| Branches | 3059 | 1160 (37.9%) | 0 (0.0%) | 1899 (62.1%) | 0 (0.0%) |
| Generators | 6195 | 361 (5.8%) | 0 (0.0%) | 5834 (94.2%) | 0 (0.0%) |
| Demand points | 770 | 0 (0.0%) | 0 (0.0%) | 770 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 142 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 142 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map); their existence and the branches between them are JAO's (RTE's). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, RTE: 917 internal lines (all with R, X, B, Imax; 335 at 400 kV, 582 at 225 kV), 19 tie-line rows (kept 17), 235 400/225 kV transformers (234 modelled).
- Ties dropped (French end has no internal JAO line): ['LIT 225KV N0 1 CAMPOROSSO - MENTO / .CAM: French end MENTON TRINITE VICTOR has no internal JAO line (would be an island)', 'LIT 225kV N0 1 AUBANGE - MT-SAINT-MARTIN: French end MT SAINT MARTIN has no internal JAO line (would be an island)'].
- Sites resolved by name: 527 (8 tee junctions); buses by kV {'225': 1048, '400': 181}; boundary buses 14.
- Coordinates (ODRE publishes none since RTE withdrew GPS data): OSM tag ref:FR:RTE_nom = RTE name 505, ODRE site code -> OSM ref:FR:RTE 9, OSM name 1, JAO map 9, neighbour centroid 3.
- Shape check (crow-fly vs JAO length): median ratio 0.891 over 898 lines; 56 lines whose crow-fly distance exceeds 1.3 x their JAO length + 5 km (both ends usually OSM-placed by exact RTE name, so JAO's length / impedance there is for a shorter section than the named end-to-end route; [VERIFY]).
- Transformers skipped (no 400 kV line bus at the site in JAO): ['TR 400/225kV 761 FEUILLANE: site has no 400 kV line bus in JAO']; 225 kV buses that exist only through a JAO transformer (no 225 kV line in JAO): 1.
- Synthetic 400/225 kV couplings (median JAO unit {'mva': 702.6, 'x_pct_own': 19.94, 'x_over_r': 202.2}): ['AYRES', 'BATHIE (LA)', 'CRUAS', 'GRAVELINES', 'MARTIGUES PONTEAU', 'PREGUILLAC', 'RENARDIERES (LES)', 'ST LAURENT DES EAUX B'].
- Islands in the topology: 2 (sizes [1240, 3]).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 2253.6 | 0.0 |
| biomass | 2624.8 | 1075.0 |
| coal | 1760.0 | 21.0 |
| gas | 13835.4 | 9091.9 |
| hydro_lake | 8741.6 | 6031.2 |
| hydro_ror | 11828.1 | 5427.3 |
| interconnector | 7568.7 | 7568.7 |
| nuclear | 62990.0 | 52852.0 |
| oil | 1411.4 | 1004.1 |
| other | 39.8 | 0.0 |
| pumped_storage | 5060.2 | 3573.5 |
| solar | 34233.7 | 1825.0 |
| wind_offshore | 2316.2 | 115.0 |
| wind_onshore | 24655.8 | 1812.0 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| GB | -58.4 | FR:MANDARINS:400 (IFA (Les Mandarins - Sellindge, HVDC), share 0.500 of GB rating) |
| GB | -29.2 | FR:MANDARINS:400 (ElecLink (Les Mandarins - Folkestone, HVDC in the Channel Tunnel), share 0.250 of GB rating) |
| GB | -29.2 | FR:TOURBE:400 (IFA2 (Tourbe - Chilling, HVDC), share 0.250 of GB rating) |
| ES | 228.2 | ES:ARKALE:225 (AC boundary bus (tie ES:ARKALE:225 - FR:ARGIA:225), share 0.078 of ES rating) |
| ES | 176.0 | ES:BIESCAS:225 (AC boundary bus (tie ES:BIESCAS:225 - FR:PRAGNERES:225), share 0.060 of ES rating) |
| ES | 789.9 | ES:HERNANI:400 (AC boundary bus (tie ES:HERNANI:400 - FR:ARGIA:400), share 0.269 of ES rating) |
| ES | 776.1 | ES:VICH:400 (AC boundary bus (tie ES:VICH:400 - FR:BAIXAS:400), share 0.264 of ES rating) |
| ES | 970.3 | FR:BAIXAS:400 (INELFE (Baixas - Santa Llogaia, HVDC 2 x 1000 MW), share 0.330 of ES rating) |
| IT | 1161.7 | IT:RONDISSONE:400 (AC boundary bus (tie IT:RONDISSONE:400 - FR:ALBERTVILLE:400), share 0.516 of IT rating) |
| IT | 665.4 | IT:VENAUS:400 (AC boundary bus (tie IT:VENAUS:400 - FR:VILLARODIN:400), share 0.296 of IT rating) |
| IT | 424.5 | FR:GRANDE ILE:400 (Savoie-Piemont (Grande-Ile - Piossasco, HVDC 2 x 600 MW), share 0.189 of IT rating) |
| CH | 317.6 | FR:BOIS TOLLOT:400 (FR-CH 400 kV ties at Bois-Tollot (Verbois), share 0.234 of CH rating) |
| CH | 317.6 | FR:CORNIER:400 (FR-CH 400 kV ties at Cornier (Riddes / Chamoson), share 0.234 of CH rating) |
| CH | 317.6 | FR:MAMBELIN:400 (FR-CH 400 kV tie at Mambelin (Bassecourt), share 0.234 of CH rating) |
| CH | 317.6 | FR:SIERENTZ:400 (FR-CH 400 kV tie at Sierentz (Asphard / Laufenburg), share 0.234 of CH rating) |
| CH | 84.7 | FR:GENISSIAT POSTE:225 (FR-CH 225 kV tie at Genissiat (Verbois), share 0.062 of CH rating) |
| BE | 105.4 | BE:ACHENE:400 (AC boundary bus (tie BE:ACHENE:400 - FR:LONNY:400), share 0.103 of DEBE rating) |
| BE | 34.4 | BE:AUBANGE:225 (AC boundary bus (tie BE:AUBANGE:225 - FR:MOULAINE:225), share 0.034 of DEBE rating) |
| BE | 203.5 | BE:AVELGEM:400 (AC boundary bus (tie BE:AVELGEM:400 - FR:AVELIN:400), share 0.199 of DEBE rating) |
| BE | 203.5 | BE:AVELGEM:400 (AC boundary bus (tie BE:AVELGEM:400 - FR:MASTAING:400), share 0.199 of DEBE rating) |
| BE | 31.3 | BE:MONCEAU:225 (AC boundary bus (tie BE:MONCEAU:225 - FR:CHOOZ:225), share 0.031 of DEBE rating) |
| DE | 33.9 | DE:EICHSTETTEN:225 (AC boundary bus (tie DE:EICHSTETTEN:225 - FR:VOGELGRUN:225), share 0.033 of DEBE rating) |
| DE | 134.1 | DE:EICHSTETTEN:400 (AC boundary bus (tie DE:EICHSTETTEN:400 - FR:MUHLBACH:400), share 0.131 of DEBE rating) |
| DE | 19.6 | DE:ENSDORF:225 (AC boundary bus (tie DE:ENSDORF:225 - FR:ST AVOLD:225), share 0.019 of DEBE rating) |
| DE | 255.9 | DE:ENSDORF:400 (AC boundary bus (tie DE:ENSDORF:400 - FR:VIGY:400), share 0.251 of DEBE rating) |

## Repairs (every change made so the case solves)

- islands dropped (not joined to the main grid in JAO): 1 with 3 buses: [['FR:BRODE:225', 'FR:DUVIGNEAU:225', 'FR:PIQUAGE A DUVIGNEAU:225']]
- open-ended tee stubs removed (a 'PIQUAGE' junction with one line: the rest of that tee is not in JAO): 4 line(s): ['LIT 225kV N0 1 GAVRELLE - TRAN5 / GAVRE PERTA 1', 'LIT 225kV N0 1 BREUIL (LE) - PIQUAGE A SAINT GERONS', 'LIT 225kV N0 1 CORDEMAIS-POSTE - PIQUAGE A BASTILLE', 'LIT 400kV N0 1 PRIONNET - T.SUP / PRION - TAVEL']
- unit commitment: for nuclear, gas, coal, oil, lake hydro and pumped storage, register units committed largest first (departement totals always run) until committed capacity x loading (0.95 nuclear, 0.8 others) covers the eCO2mix value; 11:gas 4/6 units; 11:oil 5/8 units; 11:pumped_storage 0/0 units; 24:gas 0/0 units; 24:hydro_lake 0/0 units; 24:nuclear 11/12 units; 24:pumped_storage 0/0 units; 27:gas 0/10 units; 27:hydro_lake 1/1 units; 28:gas 0/6 units; 28:nuclear 8/9 units; 32:gas 6/11 units; 32:nuclear 6/6 units; 44:coal 1/1 units; 44:gas 7/9 units; 44:hydro_lake 0/0 units; 44:nuclear 7/8 units; 44:oil 1/1 units; 44:pumped_storage 1/1 units; 52:coal 1/2 units; 52:gas 1/1 units; 52:hydro_lake 0/0 units; 53:gas 1/1 units; 53:hydro_lake 0/0 units; 53:oil 5/5 units; 75:gas 0/0 units; 75:hydro_lake 2/2 units; 75:nuclear 6/6 units; 75:pumped_storage 0/0 units; 76:gas 0/0 units; 76:hydro_lake 8/11 units; 76:nuclear 1/2 units; 76:pumped_storage 1/1 units; 84:gas 1/1 units; 84:hydro_lake 7/15 units; 84:nuclear 14/14 units; 84:pumped_storage 4/4 units; 93:gas 6/9 units; 93:hydro_lake 12/13 units; 93:oil 2/2 units; 93:pumped_storage 0/0 units. Offline units in the case: 48 (0 MW, pq, no inertia, no fault infeed; estimated, no outage list used)
- plant connection lines not in JAO added for 4 plant(s) more than 3 km from their JAO bus (estimated): GENTI 2x26.3 km to Cazaril 400kV; BUGEY 3x3.9 km to St Vulbas Ouest 400kV; GERVA 2x11.3 km to Cpbla B Mon Gampa 1 225kV; BXMON 2x5.9 km to Piquage A Greoux Les Bains 225kV
- synchronous plant connected at 225/400 kV moved behind 145 lumped GSUs (101344 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (register departement totals below 225 kV) on 743 embedded buses behind lumped supply equivalents (88884 MVA, x 20 % own rating; estimated), role pq with Q = 0
- slack: largest dispatched EHV synchronous unit CIVAUN01 - GROUPE 01 DE LA CENTRALE NUCLEAIRE DE CIVAUX at Civaux 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- reactive repair staged by load scaling (the no-limit Newton does not solve the full snapshot without support): shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage starting from the previous stage's shunts (estimated)
- repair shunts moved from generator / embedded / plant buses to their grid bus: 66 (770 MVAr; estimated)
- reactive repair stopped early at some stage(s): pass 3: no damped step solves; 40 buses still outside; pass 1: no damped step solves; 40 buses still outside
- bus shunts placed where the snapshot needs reactive support (40 passes of a Newton solve without reactive limits): 42 reactors 1400 MVAr, 100 capacitors 7130 MVAr (synthetic; JAO publishes no reactive compensation, real RTE stations run many reactors and capacitor banks)

## Fitted and assumed values (the brief's NO FITTING TO THE SOLVER rule)

- ATTESTED (not assumed): JAO RTE line and 400/225 kV transformer R / X / B / Imax. The 56 JAO lines whose listed length_km is far below the end-to-end distance were checked in r4: their JAO reactance implies a route of 1.048 x the crow-fly distance (median; 0.84 at the lowest) at 0.32 ohm/km (400 kV) / 0.40 ohm/km (225 kV), against 1.09 for the other lines, so the JAO IMPEDANCES are for the full route and only JAO's length_km field is short. Nothing was changed.
- ESTIMATED (rule): ODRE circuits JAO does not list: length 1.25 x crow-fly; overhead R/X/B/Imax = JAO RTE median per km by voltage; from r4, circuits listed only as underground in ODRE take typical XLPE cable R/X/B per km (ASSUMED, the build rules, [VERIFY]) and the JAO median Imax.
- ASSUMED: GSU x 14.5 % own rating, X/R 40; embedded supply equivalent x 20 %; unit Q range -0.3 to 0.62 MVAr per MW; setpoint 1.02 pu; inertia H by fuel {'coal': 4.0, 'gas': 4.0, 'oil': 1.0, 'nuclear': 5.0, 'hydro_ror': 3.0, 'hydro_lake': 3.0, 'pumped_storage': 3.0, 'biomass': 4.0, 'other': 2.0}.
- ASSUMED (set from an earlier round's solve, so treat as FITTED): electrify LOSS_ALLOW_MW 2,400 MW (set from the first build's slack) and LOAD_CAP_SHARE 0.25 (r2, tightened after r1's Nantes / Paris overloads: a demand-placement cap by branch rating).
- ASSUMED: HVDC link ratings used only to split each border's eCO2mix exchange over its sites: IFA 2,000 MW, ElecLink 1,000 MW, IFA2 1,000 MW, INELFE 2 x 1,000 MW, Savoie-Piemont 2 x 600 MW (GE Vernova case study: two 600 MW bipoles) - the published link capacities; the five Swiss tie sites' shares use recalled ratings (1,500 MW per 400 kV site, 400 MW Genissiat 225 kV) [VERIFY against Swissgrid].
- SYNTHETIC REPAIR: every bus shunt (staged placement, France copy of Italy's #38-fixed _place from r4).
- NOT USED: radial-chain demand relief.
- No other value was changed to clear a solver symptom in r4.

## Known gaps

- JAO lists only part of RTE's 225 kV grid (582 circuits against about 1,957 overhead 225 kV sections in ODRE): the rest of the 225 kV network, all 63/90/150 kV, and the plant connection lines (Cattenom - Vigy, Flamanville - Tollevast, Paluel, Gravelines, Chooz B) are not modelled. Plant sits on the nearest JAO bus of its voltage.
- ODRE's line lists (names and site codes, Licence Ouverte) could give an OPEN 225/400 kV topology with OSM positions, but no impedances; not used in this round.
- No reactive compensation published (JAO excludes it; ODRE has none); the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per site and voltage.
- Neighbouring grids are fixed boundary injections (eCO2mix commercial exchanges per border scaled to the net physical import): no foreign network and no fault infeed from abroad, so fault levels near borders are low. DE and BE are one eCO2mix border, split here by tie rating. Swiss ties are not in JAO (Swissgrid is not a Core TSO): injections at five French border sites, shares by recalled ratings [VERIFY].
- Unit commitment is by size (largest first), not by RTE's real outage list for 2026-01-06, so WHICH units are off is estimated.
- Embedded generation and demand are departement totals spread by commune population; no industrial load map.
- GridSim IEC 60909 feeds the fault from every machine in the file at its rating: idle inverters are flagged converterFaultCurrentPu 0; running wind feeds 1.0 x rated current.

## Sources

- Core Static Grid Model, 9th release (2026-03): RTE lines, tie-lines, transformers (R, X, B, Imax), and its publication map (JAO S.A. on behalf of the Core TSOs (RTE for France)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations (225/400 kV, tags ref:FR:RTE and ref:FR:RTE_nom), Overpass API 2026-10-31 (OpenStreetMap contributors), ODbL 1.0
- Sites electriques RTE et points de piquage (au 16 juin 2026): names, codes, departement (no positions) (RTE via ODRE), Licence Ouverte v2.0 (Etalab)
- Registre national des installations de production et de stockage d'electricite (au 31/08/2026) (RTE / ODRE), Licence Ouverte v2.0 (Etalab)
- eCO2mix national consolidated data, 2026-01-06 09:00 UTC: consumption, production by fuel, exchanges (RTE / ODRE), Licence Ouverte v2.0 (Etalab)
- API Geo communes: population, centre points, departement and region codes (DINUM (INSEE, IGN data)), Licence Ouverte v2.0 (Etalab)
- Model assembly steps: name resolution, coordinates, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- france-geojson regions (IGN Admin Express COG), Licence Ouverte: region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: France outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf france-spine-400-225-r15   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - France transmission 400/225 kV winter peak 2026-01-06 (UnvalidatedAtScale) (2128 buses)
  converged in 8 iteration(s), mismatch 6.07E-011 pu   losses 2380.744 MW / 4261.590 MVAr
  voltage range 0.9482 - 1.0228 pu
  lowest voltages:
      bus 1149   0.9482 pu     -8.648 deg
      bus 757    0.9482 pu     -8.632 deg
      bus 460    0.9490 pu    -21.302 deg
      bus 402    0.9493 pu    -18.802 deg
      bus 2059   0.9493 pu     -6.525 deg
      bus 593    0.9493 pu    -23.512 deg
      bus 1777   0.9494 pu     -6.123 deg
      bus 275    0.9496 pu    -33.323 deg
      bus 513    0.9496 pu    -29.773 deg
      bus 230    0.9496 pu    -29.794 deg
      bus 369    0.9497 pu     -5.081 deg
      bus 1505   0.9499 pu    -19.991 deg
(warm start baked into buses.json from that solve: flat start took 8 Newton iterations)
$ gridsim pf france-spine-400-225-r15 (warm start)   (exit 0, 0.5 s)
Power flow - France transmission 400/225 kV winter peak 2026-01-06 (UnvalidatedAtScale) (2128 buses)
  converged in 4 iteration(s), mismatch 6.07E-011 pu   losses 2380.744 MW / 4261.590 MVAr
  voltage range 0.9482 - 1.0228 pu
  lowest voltages:
      bus 1149   0.9482 pu     -8.648 deg
      bus 757    0.9482 pu     -8.632 deg
      bus 460    0.9490 pu    -21.302 deg
      bus 402    0.9493 pu    -18.802 deg
      bus 2059   0.9493 pu     -6.525 deg
      bus 593    0.9493 pu    -23.512 deg
      bus 1777   0.9494 pu     -6.123 deg
      bus 275    0.9496 pu    -33.323 deg
      bus 513    0.9496 pu    -29.773 deg
      bus 230    0.9496 pu    -29.794 deg
      bus 369    0.9497 pu     -5.081 deg
      bus 1505   0.9499 pu    -19.991 deg
$ gridsim physics-check france-spine-400-225-r15   (exit 0, 0.5 s)
Physics-law audit  -  france-spine-400-225-r15  (2128 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 5.12E-010 | MW | independent dissipation 2380.743719 MW (branch 2380.7437 + shunt 0.0000) vs reported loss 2380.743719 MW |
| 2 | Ohm's law | Holds | 1.28E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 5.05E-010 | MW | total network loss 2380.743719 MW vs reported 2380.743719 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 2.03E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 6.07E-009 | MVA | same residual as law 6, reactive component included at 1974 PQ bus(es), by the bus types the solve ended with; 6 of them declared PV and solved as PQ (6 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## Inference round france-spine-400-225-r16 (base france-spine-400-225-r15, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 5 (6 circuits / units, 62.6 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 140 sites, 6420 MVAr capacitive / 1190 MVAr inductive, replacing the generic repair (142 shunts, 7130 / 1400 MVAr) (mode 'consolidated').
- Taps: 522 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 6; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 8 | 11 |
| iterations_warm | 4 | 8 |
| loss_mw | 2380.744 | 2358.216 |
| vmin_pu | 0.948 | 0.953 |
| vmax_pu | 1.023 | 1.022 |
| angle_spread_deg | 99.530 | 99.184 |
| over_100 | 36 | 31 |
| over_120 | 17 | 14 |
| over_140 | 9 | 8 |
| auto_cap_mvar | 7130.000 | 0 |
| auto_reactor_mvar | 1400.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 7610.000 |
| units_held_at_q_limit | 6 | 6 |
| cpf_lambda | 1.043 | 1.043 |
| physics_pass | True | True |

Worst after: 226.5 % odre:HARCOURT-MENUS:225:1 (Harcourt 225kV - Menus 225kV); 180.5 % odre:GALOREAUX (LES)-MAUGES (LES):225:1 (Galoreaux (Les) 225kV - Mauges (Les) 225kV); 180.1 % odre:SAUMATY-SEPTEMES:225:1 (Saumaty 225kV - Septemes 225kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 113.2 % odre:CHOLET-RECOUVRANCE:225:1 (Cholet 225kV - Recouvrance 225kV)
- 112.1 % odre:LAVAL-OUDON:225:1 (Laval 225kV - Oudon 225kV)
- 112.0 % odre:ALOUETTES (LES)-PLAISANCE:225:1 (Alouettes (Les) 225kV - Plaisance 225kV)
- 110.8 % jao:17T000000021421O (Champagnole 225kV - Saone 225kV)
- 105.3 % jao:17T000000018159J (Bollene 225kV - Tricastin Poste (Le) 225kV)
- 104.9 % jao:17T0000000172226 (Barjac 225kV - Croisiere 225kV)
- 103.2 % odre:DOMLOUP-PIQUAGE A SAINT LAURENT:225:1 (Domloup 225kV - Piquage A Saint Laurent 225kV)
- 103.1 % odre:PIQUAGE A FRENOUVILLE-TOURBE:225:1 (Piquage A Frenouville 225kV - Tourbe 225kV)
- 102.3 % jao:17T000000021404O (Champagnier 225kV - Pariset 225kV)
- 102.0 % odre:ARENC-VIEUX PORT:225:1 (Arenc 225kV - Vieux Port 225kV)
- 101.9 % jao:17T0000000265589 (Mauges (Les) 225kV - Vertou 225kV)
- 101.6 % jao:17T000000019479X (Calan 225kV - Poteau Rouge 225kV)
- 101.2 % odre:MUR-PLAINE HAUTE:225:1 (Mur 225kV - Plaine Haute 225kV)

Inferred feeds:

- inferred feed 1: 225 kV line x2 Saucats 225kV - Barban 225kV 0.5 km; demanded by odre:BARBAN-SAUCATS:225:1 (Barban 225kV - Saucats 225kV) at 172.4 % (N-0 snapshot, bridge: no alternative path); after 77.0 %
- inferred feed 2: 225 kV line x1 Cergy 225kV - Perret 225kV 23.5 km; demanded by odre:NOVION-PERRET:225:1 (Novion 225kV - Perret 225kV) at 130.0 % (N-0 snapshot); after 119.1 %
- inferred feed 3: 225 kV line x1 Plessis Gassot 225kV - Perret 225kV 18.7 km; demanded by odre:NOVION-PERRET:225:1 (Novion 225kV - Perret 225kV) at 119.1 % (N-0 snapshot); after 83.7 %
- inferred feed 4: 225 kV line x1 Havre (Le) 225kV - Sainneville 225kV 12.34 km; demanded by jao:17T000000027876R (Pont Sept 225kV - Sainneville 225kV) at 117.8 % (N-0 snapshot); after 81.2 %
- inferred feed 5: 225 kV line x1 Argia 225kV - Mouguerre 225kV 7.06 km; demanded by jao:17T-FR-00000062X (Argia 225kV - Mouguerre 225kV) at 116.1 % (N-0 snapshot); after 67.6 %

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: +500 MVAr at Douvrin 225kV
- inferred compensation 2: +440 MVAr at Barban 225kV
- inferred compensation 3: +430 MVAr at Blenod 400kV
- inferred compensation 4: +270 MVAr at Verrerie (La) 225kV
- inferred compensation 5: +180 MVAr at Laveyrune 225kV
- inferred compensation 6: +170 MVAr at Boutre 225kV
- inferred compensation 7: -170 MVAr at Cazaril 400kV
- inferred compensation 8: +170 MVAr at Beaulieu 225kV
- inferred compensation 9: +160 MVAr at Doberie 225kV
- inferred compensation 10: +150 MVAr at Cressy Omencourt 225kV
- inferred compensation 11: +150 MVAr at Joux La Ville 225kV
- inferred compensation 12: +140 MVAr at Constantin 225kV
- inferred compensation 13: +130 MVAr at Piquage A Cessier (Le) 225kV
- inferred compensation 14: +130 MVAr at Brailly Cornehotte 225kV
- inferred compensation 15: +130 MVAr at Cernay 225kV
