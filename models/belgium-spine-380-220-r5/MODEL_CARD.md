# MODEL CARD: Belgium transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Belgium study results. A solvable rough map of the Belgium 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, ELIA) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r5 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 11533.5 MW; interval {'public_power_interval_utc': '2025-11-19T16:00:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 3600}).
- Buses 165 (11 cross-border boundary buses, 65 generator / embedded buses), branches 275 (lines 189, transformers 86), generators 425.
- Buses by kV: 380 kV 54, 220 kV 46, 110 kV 54, 21 kV 11.
- Dispatch 10113.0 MW (Belgium plant) + boundary imports 2655.0 MW; demand 12533.6 MW (incl. boundary exports 1002.0 MW and storage charging).
- Slack: 1 reference: Seraing.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 165 | 0 (0.0%) | 0 (0.0%) | 89 (53.9%) | 76 (46.1%) |
| Branches | 275 | 30 (10.9%) | 10 (3.6%) | 235 (85.5%) | 0 (0.0%) |
| Generators | 425 | 0 (0.0%) | 0 (0.0%) | 425 (100.0%) | 0 (0.0%) |
| Demand points | 53 | 0 (0.0%) | 0 (0.0%) | 53 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 65 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 65 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, ELIA: 130 internal line rows (by class {'hv': 79, '220': 51}), 13 tie-line rows used, 12 JAO transformers placed.
- Positions: {'osm_whole_word': 62, 'jao_map': 20, 'pypsa_osm': 5, 'neighbour_mean': 2, 'boundary': 11} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: ['belval', 'y senonchamps']).
- PyPSA-Eur OSM gap lines (estimated): 41 circuits, 8 OSM-only stations, 4 chain duplicates of JAO lines skipped; per km (HV) R 0.0111 ohm, X 0.2238 ohm, B 76.700 uS, Imax 2127 A (medians of 5 JAO lines); 220 kV R 0.0374, X 0.1145, B 75.360, Imax 1001 A.
- Synthetic couplings (median JAO unit {'mva': 321.0, 'x_pct_own': 15.91, 'x_over_r': 98.4, 'how': 'median of 12 JAO Belgium 400(380)/220 kV units'}): ['gouy']; near-site ['centrale awirs / awirs (0.62 km)', 'aubange / belval (0.00 km)', 'brume / brume sncb (0.00 km)'].
- JAO transformers not modelled: ['TR AUBANGE PST 1: phase shifter 243/243 kV, not modelled', 'TR VAN EYCK PST 1: phase shifter 400/400 kV, not modelled', 'TR VAN EYCK PST 2: phase shifter 400/400 kV, not modelled', 'TR ZANDVLIET PST 2: phase shifter 400/400 kV, not modelled', 'TR MONCEAU PST 1: phase shifter 245/160 kV, not modelled', 'TR ZANDVLIET PST 3: phase shifter 400/400 kV, not modelled', 'TR ZANDVLIET PST 4: phase shifter 400/400 kV, not modelled'].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [100]).
- Shape check (crow-fly vs published length): 0 outliers [].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 291.2 | 53.6 |
| biomass | 296.1 | 253.8 |
| gas | 6431.2 | 3711.1 |
| hydro_ps | 1308.0 | 0.0 |
| hydro_res | 12.7 | 0.0 |
| hydro_ror | 59.3 | 5.6 |
| interconnector | 2655.0 | 2655.0 |
| nuclear | 4096.0 | 2507.1 |
| oil | 159.6 | 65.7 |
| other | 249.8 | 199.8 |
| solar | 942.1 | 0.0 |
| waste | 322.4 | 207.9 |
| wind_offshore | 2752.2 | 2162.9 |
| wind_onshore | 1724.0 | 945.5 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| FR | 134.6 | BE:mastaing [FR]:hv (AC boundary bus, share 0.262 of the FR border by tie rating) |
| FR | 134.6 | BE:lonny [FR]:hv (AC boundary bus, share 0.262 of the FR border by tie rating) |
| FR | 36.7 | BE:chooz [FR]:220 (AC boundary bus, share 0.071 of the FR border by tie rating) |
| FR | 134.6 | BE:avelin [FR]:hv (AC boundary bus, share 0.262 of the FR border by tie rating) |
| FR | 36.7 | BE:moulaine [FR]:220 (AC boundary bus, share 0.071 of the FR border by tie rating) |
| FR | 36.7 | BE:mt-saint-martin [FR]:220 (AC boundary bus, share 0.071 of the FR border by tie rating) |
| DE | -1002.0 | BE:alegro convertor station:hv (HVDC ALEGrO at its converter station, share 1.000) |
| LU | 0.0 | BE:y differdange [LU]:220 (AC boundary bus, share 0.437 of the LU border by tie rating) |
| LU | 0.0 | BE:oxylux [LU]:220 (AC boundary bus, share 0.563 of the LU border by tie rating) |
| NL | 971.5 | BE:maasbracht [NL]:hv (AC boundary bus, share 0.500 of the NL border by tie rating) |
| NL | 971.5 | BE:rilland [NL]:hv (AC boundary bus, share 0.500 of the NL border by tie rating) |
| GB | 198.0 | BE:nemo convertor station [GB]:hv (AC boundary bus, share 1.000 of the GB border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 11 lumped GSUs (11984 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 54 embedded buses behind lumped supply equivalents (8042 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 1 MW, type C 25 MW, type D 75 MW; Elia TSO proposal under RfG Art. 5(3) (public consultation 2017-05-19, submitted 2018-05-17), adopted in the Federal Grid Code (Royal Decree 22 April 2019) [VERIFY: the CWaPE copy also shows a 0.25 MW type B set]): 25 synchronous units (692.2 MW) of type B+ and 34 running converter units (3754.2 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 217 smaller units (1956.1 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; gas 9/23 units (1505 MW offline); oil 4/8 units (72 MW offline); biomass 55/55 units (-0 MW offline); waste 7/10 units (46 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): biomass register 113.0 MW vs energy-charts 253.8 MW; 183.1 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 0.0 MW vs energy-charts 199.8 MW; 249.8 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Seraing at Duval 220kV gen bus, reactive band +/-10000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (9 passes of a Newton solve without reactive limits): 65 reactors 5006 MVAr, 0 capacitors 0 MVAr (synthetic; JAO publishes no reactive compensation): Tihange 3 380kV gen bus -440, Doel 380kV gen bus -280, Osm Virtual_Way/161469069:0 380kV -210, Osm Virtual_Way/23141413:0 380kV -200, Centrale Coo 380kV gen bus -180, Champion 380kV -180, Centrale Awirs 380kV gen bus -170, Y Zuttendaal 380kV -160, Alegro Convertor Station 380kV -150, Lixhe 380kV -150, Aubange 380kV -140, Gouy 380kV gen bus -130, Osm Virtual_Way/161479351:0 380kV -130, Andre Dumont 380kV -120, Y St-Amand 380kV -110, Gramme 380kV -110, Verbrande Brug 380kV -110, Tergnee 380kV embedded bus -100, Rodenhuize 380kV -100, Y Rodenhuize 380kV -100, Gezelle 380kV gen bus -90, Rodenhuize 380kV embedded bus -90, Rodenhuize 380kV gen bus -80, Y Buggenhout 380kV -80, Meerhout 380kV embedded bus -70, Maerlant 380kV -70, Nemo Convertor Station [GB] 380kV -70, Gezelle 380kV -70, Stevin 380kV -70, Eeklo Noord 380kV -50, Horta 380kV -50, Tihange 1 380kV -50, Tihange 2 380kV -50, Rimiere 380kV -50, Offshore Switchyard 220kV -50, Houffalize 220kV -40, Y Houffalize 220kV -40, Offshore Windpark (Mermaid) 220kV -40, Offshore Windpark (Northwester Ii) 220kV -40, Offshore Windpark (Seastar) 220kV -40, Offshore Switchyard (Rentel) 220kV -40, Tihange Bis 380kV -30, Bruegel 380kV -30, Mercator 380kV -30, Tergnee 380kV -30, Villeroux 220kV -30, Y Senonchamps 220kV -30, Bastogne 220kV -30, Marcourt 220kV -30, Y Marcourt 220kV -30, Latour 220kV -30, Y Latour 220kV -30, Osm Virtual_Way/714613608:0 220kV -30, Champion 380kV embedded bus -20, Brume 220kV -20, Brume Sncb 220kV -20, Offshore Windpark 220kV -20, Osm Virtual_Way/713775507:0 220kV -20, Lixhe 220kV embedded bus -10, Stevin 220kV -10, St-Mard Sncb 220kV -10, St-Mard 220kV -10, Villeroux 220kV embedded bus -5, St-Mard 220kV embedded bus -0, Marcourt 220kV embedded bus -0

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: first build (build-first batch); reactive repair by fixed bus shunts only.
- r5: Reactive repair. Belgium r4 stopped at pass 7: the largest ask was 'St-Mard 220kV embedded bus' (a small embedded plant behind its lumped supply equivalent), and a -10 MVAr minimum step there alone took the no-limit solve to 0.597 pu, so all 7 damped retries failed and the Ardennes 220 kV group stayed at 1.065-1.069 pu. Repair algorithm only: no network, dispatch or demand value changed. Model tables as rebuilt at 06:58 with the JAO period-of-date rule; Belgium ratings compared in the README).

## Known gaps

- JAO lists only the elements relevant to flow-based capacity calculation; missing corridors were added from PyPSA-Eur OSM with median JAO per-km parameters (estimated), and some stations may still be missing.
- No reactive compensation from JAO; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per station and voltage class. Phase shifters are not modelled.
- Neighbouring grids are fixed boundary injections (energy-charts physical flows at the snapshot): no foreign network and no fault infeed from abroad.
- Generator fleet from powerplantmatching (merged registers): duplicates and retired capacity are possible; where the register is short of the snapshot output a register-gap aggregate is added (listed in the repairs).
- Demand is allocated by population only (no industrial load map).
- Snapshot: one common Core-region quarter-hour (2025-11-19 16:30 UTC) for the whole batch, not this country's own peak; an hourly energy-charts series uses the 16:00-17:00 UTC hour.
- IEC 60909 fault sweep not run in round 1 (build-first); refinement runs it.

## Sources

- Core Static Grid Model, 9th release (2026-03): ELIA lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (ELIA for Belgium)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Belgium (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Belgium units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Belgium 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Belgium, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries BEL ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf belgium-spine-380-220-r5   (flat start: vm 1, vaDeg 0; exit 0, 0.8 s)
Power flow - Belgium transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (165 buses)
  converged in 9 iteration(s), mismatch 7.31E-012 pu   losses 78.966 MW / -2365.802 MVAr
  voltage range 1.0051 - 1.0503 pu
  lowest voltages:
      bus 157    1.0051 pu      2.994 deg
      bus 163    1.0061 pu     -3.045 deg
      bus 64     1.0067 pu    -11.196 deg
      bus 165    1.0134 pu      0.506 deg
      bus 62     1.0178 pu     -9.505 deg
      bus 127    1.0180 pu     -0.143 deg
      bus 103    1.0200 pu      0.003 deg
      bus 106    1.0200 pu      1.791 deg
      bus 108    1.0200 pu     -4.341 deg
      bus 109    1.0200 pu     -0.093 deg
      bus 110    1.0200 pu      0.261 deg
      bus 112    1.0200 pu      1.424 deg
(warm start baked into buses.json: flat start took 9 Newton iterations)
(the build pipeline reading of the pf result) angle spread 27.525 deg; branches over 100 %: 0, over 80 %: 7; highest: jao:GRAMME - TIHANGE 3 380.18:101 (Gramme 380kV - Tihange 3 380kV) 97.9 %; jao:ALEGRO CONVERTOR STATION - LIXHE 380.115:122 (Alegro Convertor Station 380kV - Lixhe 380kV) 93.5 %; jao:HORTA - MAERLANT 380.104:42 (Horta 380kV - Maerlant 380kV) 82.3 %; jao:22T20211201AB--K:7 (Stevin 380kV - Stevin 220kV) 81.5 %; jao:22T20211201AE--8:10 (Stevin 380kV - Stevin 220kV) 81.5 %
$ gridsim pf belgium-spine-380-220-r5 (warm start)   (exit 0, 0.5 s)
Power flow - Belgium transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (165 buses)
  converged in 7 iteration(s), mismatch 4.08E-012 pu   losses 78.966 MW / -2365.802 MVAr
  voltage range 1.0051 - 1.0503 pu
  lowest voltages:
      bus 157    1.0051 pu      2.994 deg
      bus 163    1.0061 pu     -3.045 deg
      bus 64     1.0067 pu    -11.196 deg
      bus 165    1.0134 pu      0.506 deg
      bus 62     1.0178 pu     -9.505 deg
      bus 127    1.0180 pu     -0.143 deg
      bus 103    1.0200 pu      0.003 deg
      bus 106    1.0200 pu      1.791 deg
      bus 108    1.0200 pu     -4.341 deg
      bus 109    1.0200 pu     -0.093 deg
      bus 110    1.0200 pu      0.261 deg
      bus 112    1.0200 pu      1.424 deg
$ gridsim physics-check belgium-spine-380-220-r5   (exit 0, 0.5 s)
Physics-law audit  -  belgium-spine-380-220-r5  (165 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 7.69E-011 | MW | independent dissipation 78.965534 MW (branch 78.9655 + shunt 0.0000) vs reported loss 78.965534 MW |
| 2 | Ohm's law | Holds | 9.43E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 8.03E-011 | MW | total network loss 78.965534 MW vs reported 78.965534 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 6.01E-012 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 6.33E-011 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 9.79E-010 | MVA | same residual as law 6, reactive component included at 135 PQ bus(es), by the bus types the solve ended with; 6 of them declared PV and solved as PQ (6 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
