# MODEL CARD: Czechia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Czechia study results. A solvable rough map of the Czechia 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, CEPS) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r3 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 9397.7 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 120 (12 cross-border boundary buses, 45 generator / embedded buses), branches 195 (lines 135, transformers 60), generators 875.
- Buses by kV: 400 kV 52, 220 kV 23, 110 kV 33, 21 kV 12.
- Dispatch 11186.1 MW (Czechia plant) + boundary imports 1807.0 MW; demand 12805.3 MW (incl. boundary exports 3602.0 MW and storage charging).
- Slack: 1 reference: Prunerov Phase.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 120 | 0 (0.0%) | 0 (0.0%) | 63 (52.5%) | 57 (47.5%) |
| Branches | 195 | 46 (23.6%) | 9 (4.6%) | 140 (71.8%) | 0 (0.0%) |
| Generators | 875 | 0 (0.0%) | 0 (0.0%) | 875 (100.0%) | 0 (0.0%) |
| Demand points | 39 | 0 (0.0%) | 0 (0.0%) | 39 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 7 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 7 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, CEPS: 64 internal line rows (by class {'hv': 46, '220': 18}), 18 tie-line rows used, 4 JAO transformers placed.
- Positions: {'osm_whole_word': 43, 'jao_map': 0, 'pypsa_osm': 20, 'neighbour_mean': 0, 'boundary': 12} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 51 circuits, 22 OSM-only stations, 2 chain duplicates of JAO lines skipped; per km (HV) R 0.0235 ohm, X 0.2800 ohm, B 3.970 uS, Imax 2000 A (medians of 27 JAO lines); 220 kV R 0.0430, X 0.3216, B 3.465, Imax 960 A.
- Synthetic couplings (median JAO unit {'mva': 500.2, 'x_pct_own': 12.21, 'x_over_r': 91.5, 'how': 'median of 4 JAO Czechia 400(380)/220 kV units'}): ['bezdecin', 'chotejovice', 'milin', 'prestice', 'vitkov', 'vyskov']; near-site [].
- JAO transformers not modelled: ['PST Hradec 1: phase shifter 400/400 kV, not modelled', 'PST Hradec 2: phase shifter 400/400 kV, not modelled', 'PST Hradec 3: phase shifter 400/400 kV, not modelled'].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [75]).
- Shape check (crow-fly vs published length): 2 outliers [{'line': 'Albrechtice - Detmarovice', 'crow_km': 12.9, 'len_km': 133.6}, {'line': 'Kocin - Dasny - V474', 'crow_km': 15.6, 'len_km': 42.9}].
- Note: line Reporyje - Milin: no impedance and no length; dropped
- Note: line Milin - Kocin: no impedance and no length; dropped

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 43.0 | 0.0 |
| biomass | 435.6 | 353.0 |
| coal | 639.0 | 110.5 |
| gas | 1819.0 | 601.3 |
| hydro_ps | 1167.0 | 457.7 |
| hydro_res | 661.4 | 502.7 |
| hydro_ror | 126.0 | 102.8 |
| interconnector | 1807.0 | 1807.0 |
| lignite | 8875.6 | 4557.4 |
| nuclear | 4220.6 | 4001.1 |
| other | 352.7 | 282.2 |
| solar | 2941.7 | 0.0 |
| waste | 30.2 | 28.7 |
| wind_onshore | 207.6 | 188.7 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| AT | -504.2 | CZ:zaya [AT]:220 (AC boundary bus, share 0.326 of the AT border by tie rating) |
| AT | -1041.8 | CZ:durnrohr [AT]:hv (AC boundary bus, share 0.674 of the AT border by tie rating) |
| DE | 577.5 | CZ:etzenricht [DE]:hv (AC boundary bus, share 0.500 of the DE border by tie rating) |
| DE | 577.5 | CZ:rohrsdorf [DE]:hv (AC boundary bus, share 0.500 of the DE border by tie rating) |
| PL | 253.0 | CZ:wielopole [PL]:hv (AC boundary bus, share 0.388 of the PL border by tie rating) |
| PL | 73.0 | CZ:bujakow [PL]:220 (AC boundary bus, share 0.112 of the PL border by tie rating) |
| PL | 73.0 | CZ:kopanina [PL]:220 (AC boundary bus, share 0.112 of the PL border by tie rating) |
| PL | 253.0 | CZ:xdt db1 [PL]:hv (AC boundary bus, share 0.388 of the PL border by tie rating) |
| SK | -121.8 | CZ:p. bystrica [SK]:220 (AC boundary bus, share 0.059 of the SK border by tie rating) |
| SK | -676.3 | CZ:stupava [SK]:hv (AC boundary bus, share 0.329 of the SK border by tie rating) |
| SK | -676.3 | CZ:senica [SK]:hv (AC boundary bus, share 0.329 of the SK border by tie rating) |
| SK | -581.6 | CZ:varin [SK]:hv (AC boundary bus, share 0.283 of the SK border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 12 lumped GSUs (16545 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 33 embedded buses behind lumped supply equivalents (5549 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.1 MW, type C 30 MW, type D 75 MW; ERU decision ref. 07261-3/2017 of 2017-11-23 as quoted in the ENCO distribution code RfG implementation (ERU consultation file) [VERIFY: that table also shows 50 MW in the type C row]): 10 synchronous units (596.8 MW) of type B+ and 1 running converter units (42.0 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 613 smaller units (3093.7 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 1/8 units (462 MW offline); lignite 5/21 units (2866 MW offline); gas 1/10 units (972 MW offline); biomass 34/34 units (0 MW offline); waste 35/35 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): nuclear register 4164.0 MW vs energy-charts 4001.1 MW; 56.6 MW added, embedded, spread by population
- register gap aggregate (estimated): hydro_ror register 13.2 MW vs energy-charts 102.8 MW; 112.8 MW added, embedded, spread by population
- register gap aggregate (estimated): biomass register 30.0 MW vs energy-charts 353.0 MW; 405.6 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 0.0 MW vs energy-charts 282.2 MW; 352.7 MW added, embedded, spread by population
- register gap aggregate (estimated): waste register 30.2 MW vs energy-charts 28.7 MW; 0.0 MW added, embedded, spread by population
- register gap aggregate (estimated): wind_onshore register 151.0 MW vs energy-charts 188.7 MW; 56.6 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Prunerov Phase at Vernerov 400kV gen bus, reactive band +/-13176 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (4 passes of a Newton solve without reactive limits): 0 reactors 0 MVAr, 7 capacitors 250 MVAr (synthetic; JAO publishes no reactive compensation): Chotejovice 220kV embedded bus +10, Opocinek 220kV embedded bus +20, Opocinek 220kV +20, Opocinek 220kV gen bus +20, Malesice 220kV embedded bus +20, Malesice 220kV +40, Sokolnice 220kV embedded bus +120

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: first build (build-first batch); reactive repair by fixed bus shunts only.
- r3: RfG voltage control with the NATIONAL type B / C thresholds: before this round every unit below the 300 MW EHV placement size and every converter unit ran at unity pf whatever its size (no RfG rule at all). Now a committed register UNIT of type B or more (synchronous) or type C or more (converter, running) regulates voltage on its embedded bus (synchronous Q -0.30..+0.62 x MW, converter +/- 0.33 x MW); smaller units and register-gap aggregates stay pq at Q = 0; idle converters never regulate.
- r3: Demand shares from the WorldPop 2020 1 km population grid (CC BY 4.0, doi:10.5258/SOTON/WP00647; a build step) instead of GeoNames points: every populated cell goes to its nearest demand station (Voronoi catchment), so a big city is shared by every station around it instead of landing on the station nearest its single GeoNames point (Vienna on Kledering, Prague on Malesice). The demand total (energy-charts balance) is unchanged; only its spread. GeoNames PPLX sections no longer used.

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

- Core Static Grid Model, 9th release (2026-03): CEPS lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (CEPS for Czechia)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Czechia (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Czechia units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Czechia 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Czechia, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries CZE ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf czechia-spine-400-220-r3   (flat start: vm 1, vaDeg 0; exit 0, 0.6 s)
Power flow - Czechia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (120 buses)
  converged in 7 iteration(s), mismatch 9.32E-011 pu   losses 222.679 MW / -390.093 MVAr
  voltage range 0.9511 - 1.0290 pu
  lowest voltages:
      bus 60     0.9511 pu    -24.364 deg
      bus 62     0.9542 pu    -30.260 deg
      bus 72     0.9573 pu    -25.813 deg
      bus 118    0.9583 pu    -24.332 deg
      bus 114    0.9608 pu    -30.270 deg
      bus 55     0.9656 pu    -21.341 deg
      bus 107    0.9667 pu    -17.646 deg
      bus 75     0.9686 pu    -36.559 deg
      bus 111    0.9724 pu    -20.375 deg
      bus 71     0.9753 pu    -34.564 deg
      bus 113    0.9828 pu    -25.164 deg
      bus 53     0.9841 pu    -16.848 deg
(warm start baked into buses.json: flat start took 7 Newton iterations)
(the build pipeline reading of the pf result) angle spread 38.404 deg; branches over 100 %: 3, over 80 %: 7; highest: jao:27T-TR-CSTT401-T:0 (C. Stred 400kV - C. Stred 220kV) 143.8 %; jao:27T-TR-SOKT401-H:3 (Sokolnice 400kV - Sokolnice 220kV) 137.2 %; jao:Malesice - C. Stred - V206:4 (Malesice 220kV - C. Stred 220kV) 133.1 %; jao:Hradec - Vernerov:6 (Hradec 400kV - Vernerov 400kV) 99.9 %; jao:27T-TR-PRNT401X5:2 (Prosenice 400kV - Prosenice 220kV) 93.4 %
$ gridsim pf czechia-spine-400-220-r3 (warm start)   (exit 0, 0.6 s)
Power flow - Czechia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (120 buses)
  converged in 4 iteration(s), mismatch 9.32E-011 pu   losses 222.679 MW / -390.093 MVAr
  voltage range 0.9511 - 1.0290 pu
  lowest voltages:
      bus 60     0.9511 pu    -24.364 deg
      bus 62     0.9542 pu    -30.260 deg
      bus 72     0.9573 pu    -25.813 deg
      bus 118    0.9583 pu    -24.332 deg
      bus 114    0.9608 pu    -30.270 deg
      bus 55     0.9656 pu    -21.341 deg
      bus 107    0.9667 pu    -17.646 deg
      bus 75     0.9686 pu    -36.559 deg
      bus 111    0.9724 pu    -20.375 deg
      bus 71     0.9753 pu    -34.564 deg
      bus 113    0.9828 pu    -25.164 deg
      bus 53     0.9841 pu    -16.848 deg
$ gridsim physics-check czechia-spine-400-220-r3   (exit 0, 0.6 s)
Physics-law audit  -  czechia-spine-400-220-r3  (120 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 4.18E-011 | MW | independent dissipation 222.678928 MW (branch 222.6789 + shunt -0.0000) vs reported loss 222.678928 MW |
| 2 | Ohm's law | Holds | 3.90E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 4.87E-011 | MW | total network loss 222.678928 MW vs reported 222.678928 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.32E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 9.32E-009 | MVA | same residual as law 6, reactive component included at 103 PQ bus(es), by the bus types the solve ended with; 1 of them declared PV and solved as PQ (1 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
