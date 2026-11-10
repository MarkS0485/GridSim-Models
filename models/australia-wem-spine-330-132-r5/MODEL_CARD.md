# Australia WEM SWIS transmission 330/220/132 kV winter peak 2025-07-28 18:50 AWST (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official Australian study results. A solvable rough map of the WEM South West Interconnected System (WA) (330, 220, 132 kV) for one snapshot: Geoscience Australia topology with typical per-km line parameters, synthetic transformers, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r4.

## What it is

- Snapshot: 2025-07-28 18:50 AWST (UTC+8; the 5-minute interval ending 18:50), the highest WEM operational demand of June-August 2025 (AEMO WA: 4,016.35 MW).
- Buses 188 (20 generator buses), branches 248 (lines 211, transformers 37), generators 61.
- Buses by kV: 330 kV 27, 220 kV 7, 132 kV 134, 20 kV 20.
- Dispatch 4004.0 MW (incl. HVDC imports 0.0 MW); demand 3971.0 MW (incl. HVDC sending ends 0.0 MW).
- Slack: 1 reference: COLLIE_G1 (coal).
- Tasmania / HVDC: no HVDC in the SWIS
- Islands before selection 4; buses dropped 7.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 188 | 0 (0.0%) | 0 (0.0%) | 168 (89.4%) | 20 (10.6%) |
| Branches | 248 | 0 (0.0%) | 0 (0.0%) | 231 (93.1%) | 17 (6.9%) |
| Generators | 61 | 61 (100.0%) | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) |
| Demand points | 126 | 0 (0.0%) | 0 (0.0%) | 126 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 83 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 83 (100.0%) |

Buses are 'estimated' (positions and connectivity inferred from GA drawings); lines are 'estimated' (drawn route length is GA's, the per-km parameters are typical values); transformers are 'synthetic'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- Geoscience Australia power lines: 3147 features; kept 258 operational features at 500, 330, 275, 220, 132, 110 kV in the grid's states; left out: {'other grid': 1641, 'voltage 66': 1230, 'voltage 400': 1, 'status Non-Operational': 11, 'status Under Construction': 5, 'voltage 88': 1}.
- HVDC cables left out of the AC network: []
- 195 GA substations -> 166 sites (18 sites merge 2+ GA points closer than 0.5 km)
- line ends resolved: {'exact': 421, 'name': 56, 'near': 10, 'tee-to-site': 3, 'tee': 18, 'far': 6, 'dangling': 2}
- junction buses merged out (series drawing breaks): 3; self-loop lines dropped: 40 (all no longer than 1.0 km); line ends reopened as end buses (both ends on one site, line longer than 1.0 km): 16
- circuit counts from OSM (ODbL): 224 of 258 GA features matched; 48 model lines raised above 1 circuit (by kV {330: 20, 132: 28})
- Line kinds (count by kV and construction): {'132 cable': 10, '132 overhead': 163, '220 overhead': 6, '330 cable': 1, '330 overhead': 31}.
- Line route km by kV (topology, before island selection): {'330': 1566.9, '220': 655.9, '132': 4487.2}.
- End snaps beyond 1 km (estimated): 6; self-loop features dropped: 40; ends reopened as end buses: 16.
- Islands in the topology: 4 (sizes [168, 3, 2, 2]).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 1650.0 | 394.7 |
| biomass | 49.2 | 11.5 |
| coal | 1177.5 | 1098.7 |
| gas_ocgt | 1950.0 | 1176.3 |
| gas_other | 1399.0 | 940.1 |
| other | 40.0 | 9.4 |
| solar | 249.8 | 46.0 |
| wind | 1091.6 | 327.3 |

## Regions (MW)

| Region | Operational demand | Modelled demand | Dispatch in region |
|---|---:|---:|---:|
| WEM | 4016.35 | 3971.0 | 4004.0 |

## Fitted and assumed values (the brief's NO FITTING TO THE SOLVER rule)

- ASSUMED (no source): line R / X / B and thermal ratings per circuit by voltage and construction (overhead {500: (0.017, 0.28, 4.1, 2600.0), 400: (0.02, 0.3, 3.8, 1500.0), 330: (0.03, 0.32, 3.55, 1200.0), 275: (0.04, 0.32, 3.55, 950.0), 220: (0.07, 0.4, 2.85, 450.0), 132: (0.11, 0.4, 2.85, 180.0), 110: (0.13, 0.4, 2.85, 140.0)}; cable {330: (0.02, 0.13, 70.0, 700.0), 275: (0.02, 0.13, 65.0, 550.0), 220: (0.025, 0.13, 60.0, 400.0), 132: (0.035, 0.13, 55.0, 200.0), 110: (0.04, 0.13, 50.0, 150.0)}; R ohm/km, X ohm/km, B uS/km, MVA).
- ASSUMED: coupling transformers x 12 % on own rating, X/R 40; size by a physical rule: 0.6 x the smaller side's line ratings, and at least 1.5 x the demand on the LV bus (the unit must carry it); clipped to 200-3000 MVA (assumed).
- ASSUMED: GSU x 14.5 %, X/R 40; unit Q range -0.3 to 0.62 MVAr per MW (synchronous), +/-0.33 (inverter).
- PHYSICAL RULE: station export cap 0.85 x the station's network branch ratings (plant cannot export more than its connection carries); the excess goes to the region's other synchronous units.
- SYNTHETIC REPAIR: every bus shunt (seed step, copied staged repair, reactive-limit trim).
- SOURCED: circuit counts above 1 from OpenStreetMap 'circuits' / 'cables' tags (ODbL).

## Repairs (every change made so the case solves)

- islands dropped: 3 with 7 buses (largest 3): Emu Downs, End Emu Downs Wind Farm to Tee, End Emu Downs Wind Farm to Tee (North); End Parkeston to Tee, Parkeston; End Leinster to Mount Keith Mine
- winter line ratings (owner seasonal rule, tightened): 200 overhead lines x 1.0595 (rung 2: median winter/summer of Ausgrid's 233 published 132 kV feeder ratings, DTAPR 2025; OH base taken as summer [VERIFY]; 220-500 kV same factor [VERIFY]); 0 132 kV lines take Ausgrid's published winter 2026 feeder rating (rung 1, matched by end names); cables otherwise static; transformers untouched; per line in ambient_ratings.json
- coupling transformers (synthetic): 17 units at sites with lines at two voltages, rating 0.6 x the smaller side's summed line ratings clipped to 200-3000 MVA (median 270 MVA), x 12 % own rating, X/R 40
- synchronous plant moved behind 20 lumped GSUs (5430 MVA, x 14.5 % own rating, X/R 40; estimated)
- slack: largest dispatched coal station COLLIE_G1 (coal) at Shotts 330kV gen bus, reactive band +/-10000 MVAr (synthetic)
- seed reactive step (build._seed_shunts): fixed shunts equal to the reactive power of a fictitious 1.02 pu voltage controller at every bus without a generator, where at least 10 MVAr: 59 capacitors 1860 MVAr, 23 reactors 1320 MVAr (synthetic)
- reactive trim with reactive limits (build._trim_qlim, 1 passes, ended: inside 0.95-1.05 pu): 0 reactor steps 0 MVAr, 0 capacitor steps 0 MVAr (synthetic): 
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 23 reactors 1320 MVAr, 60 capacitors 1880 MVAr (synthetic; GA publishes no reactive compensation). Largest 40: Landwehr 330kV -230, Southern Terminal 132kV -160, Northern Terminal 132kV -130, Kwinana Bess 132kV -110, Yandin Terminal 330kV -90, Pinjar 132kV -80, Eneabba Terminal 330kV -70, Riverton 132kV +70, Three Springs Terminal 330kV -60, Bunbury Harbour 132kV +60, Mandurah 132kV +60, Amherst 132kV +60, Landsdale 132kV +60, North Beach 132kV +60, End Neerabup to Neerabup Power Station 330kV -50, Kemerton 330kV -50, Muja 330kV -50, Bentley 132kV +50, Ellenbrook 132kV +50, Guildford 132kV -50, Padbury 132kV +50, Canningvale 132kV +50, Yokine 132kV +50, Gosnells 132kV +50, Arkana 132kV +50, Karara Mine 330kV -40, Southern Terminal 330kV +40, Edgewater 132kV +40, Cockburn Cement Limited 132kV +40, Joondalup 132kV +40, Murdoch 132kV +40, Medina 132kV +40, Busselton 132kV +40, Byford 132kV +40, Southern River 132kV +40, Beechboro 132kV +40, Tee Kemerton Terminal Station to Tee 330kV -30, End Western Terminal to Amherst (North) 132kV +30, Clarkson 132kV +30, Midland Junction 132kV +30

## Round history (the solver's findings that drove each round)

- r1: first build; reactive repair by seed shunts (fictitious voltage control) and the copied staged repair.
- r1 solve (NEM): pf flat 14 iterations, warm 11, physics-check PASS; V 0.9456-1.1479 pu (Endevour Mine 132 kV high, units at reactive limits), losses 1278.178 MW, angle spread 82.545 deg, 34 branches over 100 % (Sydney and Brisbane 132 / 110 kV, Adelaide Para 132 kV, worst Bankstown - Sydney South 216.3 %), 9 synthetic couplings over 100 %; IEC 60909 132 kV max 61.20 kA (Sydney West), 220 kV max 53.55 kA (Keilor).
- r2 changes: (1) synthetic couplings loaded above 90 % in r1 resized to carry that flow at 80 %; (2) 132 / 110 kV cable ratings 250 / 200 MVA (were 200 / 150); (3) a final reactive trim with reactive limits.
- r2 solve (NEM): pf flat 12 iterations, warm 9, physics-check PASS; V 0.9694-1.0470 pu, losses 1242.775 MW, angle spread 83.472 deg, 17 branches over 100 % (worst Millbrook - Para 132 kV 214.7 %, Vineyard - Rouse Hill 200.0 %, Potts Hill - Rookwood Road 196.0 %).
- r3 changes (NO FITTING rule from here on): r2's two unsourced changes WITHDRAWN (the 10 couplings sized to r1 flow; the 250 / 200 MVA cable ratings): back to the r1 assumptions. Demand: each metropolitan total spread over its GeoNames suburbs (PPLX, by population) instead of in equal parts over every bus within reach (a topology / demand-placement fix). The reactive-limit trim stays (synthetic repair).

## Known gaps

- Line impedances and ratings are TYPICAL per-km values by voltage, not the TNSPs' own: circuit counts are taken as one per GA feature (double-circuit towers drawn once would be under-counted) [VERIFY].
- Transformers are synthetic (one coupling per voltage pair per site); real 500/330/275/220/132/110 kV transformer fleets, taps and OLTCs are not modelled.
- No reactive compensation is published in the GA data; the bus shunts are fixed repairs.
- Mid-span tees whose GA end lies on another line's interior are not split, so a few small 132 kV pieces fall off as islands (listed in the repairs).
- Plant register: AEMO Generation Information July 2025 placed by name on GA points; 12 sites (43.6 MW) could not be placed by name and are left out.
- Dispatch is a merit rule by fuel (solar 0 after dark, wind 30 %, batteries 25 %, coal to 85 %, hydro to 60 %, gas to 85 %), not AEMO's unit dispatch for the interval [VERIFY].
- Demand is AEMO regional operational demand spread by GeoNames population, with four large industrial loads placed by hand ([VERIFY] figures); no load map below 110 kV.

## Sources

- Electricity Infrastructure (Power Lines, Substations, Major Power Stations), MapServer query of 2026-10-31 (Geoscience Australia (Commonwealth of Australia)), CC BY 4.0
- Aggregated price and demand data, 5-minute TOTALDEMAND per NEM region, June-August 2025 (Australian Energy Market Operator (AEMO)), AEMO copyright permissions: reuse with attribution
- WEM operational demand / generation data (AEMO WA) (Australian Energy Market Operator (AEMO)), AEMO copyright permissions: reuse with attribution
- GeoNames Australia populated places (AU.zip: population, position) (GeoNames), CC BY 4.0
- OpenStreetMap power lines and cables 110 kV and above in Australia (Overpass API, 2026-10-31): circuit counts ('circuits', else cables / 3) matched onto GA features (OpenStreetMap contributors), ODbL 1.0
- Model assembly steps: site grouping, end resolution, per-km parameters, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- ABS ASGS 2021 States and Territories (generalised), CC BY 4.0: outlines in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf australia-wem-spine-330-132-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.4 s)
Power flow - Australia WEM SWIS transmission 330/220/132 kV winter peak 2025-07-28 18:50 AWST (UnvalidatedAtScale) (188 buses)
  converged in 6 iteration(s), mismatch 3.70E-012 pu   losses 109.606 MW / -1118.245 MVAr
  voltage range 1.0054 - 1.0465 pu
  lowest voltages:
      bus 100    1.0054 pu     -3.508 deg
      bus 79     1.0155 pu     -2.018 deg
      bus 80     1.0166 pu     -1.473 deg
      bus 113    1.0174 pu     -6.356 deg
      bus 42     1.0176 pu     -1.375 deg
      bus 53     1.0188 pu    -10.107 deg
      bus 51     1.0189 pu    -20.265 deg
      bus 55     1.0192 pu    -20.640 deg
      bus 152    1.0192 pu    -19.979 deg
      bus 104    1.0193 pu    -20.493 deg
      bus 98     1.0193 pu    -19.442 deg
      bus 46     1.0193 pu    -21.151 deg
(warm start baked into buses.json from that solve: flat start took 6 Newton iterations)
(the build pipeline reading of the pf result) angle spread 36.531 deg; branches over 100 %: 3, over 80 %: 13; highest: L130 (South Fremantle 132kV - Amherst 132kV) 103.2 %; L185 (Southern Terminal 132kV - Murdoch 132kV) 100.9 %; L203 (Landsdale 132kV - Northern Terminal 132kV) 100.7 %; L187 (Southern Terminal 132kV - Willetton 132kV) 90.9 %; L145 (Willetton 132kV - Canningvale 132kV) 90.8 %; gsu:S643:330 (Shotts 330kV gen bus - Shotts 330kV) 87.3 %; gsu:S704:220 (Yilgarn 220kV gen bus - Yilgarn 220kV) 86.2 %; gsu:S641:132 (Muja 132kV gen bus - Muja 132kV) 84.5 %
$ gridsim pf australia-wem-spine-330-132-r4 (warm start)   (exit 0, 0.4 s)
Power flow - Australia WEM SWIS transmission 330/220/132 kV winter peak 2025-07-28 18:50 AWST (UnvalidatedAtScale) (188 buses)
  converged in 4 iteration(s), mismatch 3.70E-012 pu   losses 109.606 MW / -1118.245 MVAr
  voltage range 1.0054 - 1.0465 pu
  lowest voltages:
      bus 100    1.0054 pu     -3.508 deg
      bus 79     1.0155 pu     -2.018 deg
      bus 80     1.0166 pu     -1.473 deg
      bus 113    1.0174 pu     -6.356 deg
      bus 42     1.0176 pu     -1.375 deg
      bus 53     1.0188 pu    -10.107 deg
      bus 51     1.0189 pu    -20.265 deg
      bus 55     1.0192 pu    -20.640 deg
      bus 152    1.0192 pu    -19.979 deg
      bus 104    1.0193 pu    -20.493 deg
      bus 98     1.0193 pu    -19.442 deg
      bus 46     1.0193 pu    -21.151 deg
$ gridsim physics-check australia-wem-spine-330-132-r4   (exit 0, 0.4 s)
Physics-law audit  -  australia-wem-spine-330-132-r4  (188 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.54E-011 | MW | independent dissipation 109.605640 MW (branch 109.6056 + shunt 0.0000) vs reported loss 109.605640 MW |
| 2 | Ohm's law | Holds | 3.94E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 2.50E-011 | MW | total network loss 109.605640 MW vs reported 109.605640 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.21E-011 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 3.70E-010 | MVA | same residual as law 6, reactive component included at 160 PQ bus(es), by the bus types the solve ended with; 2 of them declared PV and solved as PQ (2 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
$ gridsim iec60909 --all-buses australia-wem-spine-330-132-r4   (exit 0, 0.8 s)
(full sweep in iec60909_all_buses.txt) 330 kV (27): Ik'' max 24.14 kA (Kwinana Bess 330kV), min 3.93 kA (Karara Mine 330kV), median 17.79 kA; 220 kV (7): Ik'' max 10.15 kA (Muja 220kV), min 2.34 kA (West Kalgoorlie 220kV), median 3.47 kA; 132 kV (134): Ik'' max 45.11 kA (Southern Terminal 132kV), min 1.15 kA (Bounty Gold Mine 132kV), median 17.62 kA
```

## Inference round australia-wem-spine-330-132-r5 (base australia-wem-spine-330-132-r4, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 0 (0 circuits / units, 0 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 66 sites, 1560 MVAr capacitive / 670 MVAr inductive, replacing the generic repair (83 shunts, 1880 / 1320 MVAr) (mode 'consolidated').
- Taps: 14 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 2; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 6 | 6 |
| iterations_warm | 4 | 3 |
| loss_mw | 109.606 | 109.397 |
| vmin_pu | 1.005 | 0.967 |
| vmax_pu | 1.046 | 1.041 |
| angle_spread_deg | 30.925 | 31.026 |
| over_100 | 3 | 2 |
| over_120 | 0 | 0 |
| over_140 | 0 | 0 |
| auto_cap_mvar | 1880.000 | 0 |
| auto_reactor_mvar | 1320.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 2230.000 |
| units_held_at_q_limit | 2 | 1 |
| cpf_lambda | 1.369 | 1.387 |
| physics_pass | True | True |

Worst after: 103.3 % L130 (South Fremantle 132kV - Amherst 132kV); 100.2 % L203 (Landsdale 132kV - Northern Terminal 132kV); 97.5 % L185 (Southern Terminal 132kV - Murdoch 132kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 103.3 % L130 (South Fremantle 132kV - Amherst 132kV)
- 100.2 % L203 (Landsdale 132kV - Northern Terminal 132kV)

Inferred feeds:

- none

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: -110 MVAr at Landwehr 330kV
- inferred compensation 2: -70 MVAr at Eneabba Terminal 330kV
- inferred compensation 3: -70 MVAr at Northern Terminal 132kV
- inferred compensation 4: -70 MVAr at Southern Terminal 132kV
- inferred compensation 5: -60 MVAr at Three Springs Terminal 330kV
- inferred compensation 6: -60 MVAr at Yandin Terminal 330kV
- inferred compensation 7: +60 MVAr at Bunbury Harbour 132kV
- inferred compensation 8: -60 MVAr at Kwinana Bess 132kV
- inferred compensation 9: +60 MVAr at Amherst 132kV
- inferred compensation 10: +60 MVAr at Riverton 132kV
- inferred compensation 11: +60 MVAr at Landsdale 132kV
- inferred compensation 12: +60 MVAr at North Beach 132kV
- inferred compensation 13: +50 MVAr at Ellenbrook 132kV
- inferred compensation 14: +50 MVAr at Padbury 132kV
- inferred compensation 15: +50 MVAr at Yokine 132kV
