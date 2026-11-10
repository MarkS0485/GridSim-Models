# Croatia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official Croatia study results. A solvable rough map of the Croatia 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, HOPS) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r4 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 2672.0 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 55 (12 cross-border boundary buses, 20 generator / embedded buses), branches 77 (lines 46, transformers 31), generators 190.
- Buses by kV: 400 kV 14, 220 kV 21, 110 kV 16, 21 kV 4.
- Dispatch 1663.2 MW (Croatia plant) + boundary imports 1023.0 MW; demand 2633.0 MW (incl. boundary exports 24.0 MW and storage charging).
- Slack: 1 reference: Zakucac.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 55 | 0 (0.0%) | 0 (0.0%) | 23 (41.8%) | 32 (58.2%) |
| Branches | 77 | 42 (54.5%) | 10 (13.0%) | 25 (32.5%) | 0 (0.0%) |
| Generators | 190 | 0 (0.0%) | 0 (0.0%) | 178 (93.7%) | 12 (6.3%) |
| Demand points | 17 | 0 (0.0%) | 0 (0.0%) | 17 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 0 | - | - | - | - |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, HOPS: 22 internal line rows (by class {'220': 17, 'hv': 5}), 15 tie-line rows used, 5 JAO transformers placed.
- Positions: {'osm_whole_word': 17, 'jao_map': 2, 'pypsa_osm': 4, 'neighbour_mean': 0, 'boundary': 12} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 5 circuits, 7 OSM-only stations, 2 chain duplicates of JAO lines skipped; per km (HV) R 0.0312 ohm, X 0.3300 ohm, B 3.518 uS, Imax 1920 A (medians of 5 JAO lines); 220 kV R 0.0798, X 0.4158, B 2.730, Imax 815 A.
- Synthetic couplings (median JAO unit {'mva': 400.1, 'x_pct_own': 11.7, 'x_over_r': 80.0, 'how': 'median of 5 JAO Croatia 400(380)/220 kV units'}): []; near-site [].
- JAO transformers not modelled: [].
- Tie rows dropped or re-read: ['Gradacac - Dakovo (Gradacac - Dakovo): home end unclear (map end 27.9 km from a home station)', 'Tuzla - Dakovo (Tuzla - Dakovo): home end unclear (map end 27.9 km from a home station)', 'Trebinje - Plat 1 (Trebinje - Plat): home end unclear (map end 156.0 km from a home station)'].
- Islands in the topology: 1 (sizes [35]).
- Shape check (crow-fly vs published length): 0 outliers [].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 1.0 | 0.0 |
| biomass | 86.5 | 69.2 |
| coal | 342.0 | 0.0 |
| gas | 401.2 | 373.6 |
| hydro_ps | 335.7 | 257.2 |
| hydro_res | 1442.4 | 630.4 |
| hydro_ror | 375.9 | 255.6 |
| interconnector | 1023.0 | 1023.0 |
| oil | 1070.0 | 0.0 |
| other | 36.1 | 31.6 |
| solar | 391.6 | 0.0 |
| waste | 6.0 | 4.8 |
| wind_onshore | 1140.0 | 40.8 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| BA | 84.6 | HR:mostar [BA]:hv (AC boundary bus, share 0.374 of the BA border by tie rating) |
| BA | 37.8 | HR:prijedor [BA]:220 (AC boundary bus, share 0.167 of the BA border by tie rating) |
| BA | 84.6 | HR:ugljevik [BA]:hv (AC boundary bus, share 0.374 of the BA border by tie rating) |
| BA | 18.9 | HR:mostar [BA]:220 (AC boundary bus, share 0.084 of the BA border by tie rating) |
| HU | 54.0 | HR:heviz [HU]:hv (AC boundary bus, share 0.333 of the HU border by tie rating) |
| HU | 108.0 | HR:pecs [HU]:hv (AC boundary bus, share 0.667 of the HU border by tie rating) |
| RS | -24.0 | HR:s. mitrovica [RS]:hv (AC boundary bus, share 1.000 of the RS border by tie rating) |
| SI | 141.2 | HR:cirkovce [SI]:hv (AC boundary bus, share 0.222 of the SI border by tie rating) |
| SI | 31.5 | HR:podlog [SI]:220 (AC boundary bus, share 0.050 of the SI border by tie rating) |
| SI | 141.2 | HR:divaca [SI]:hv (AC boundary bus, share 0.222 of the SI border by tie rating) |
| SI | 38.8 | HR:divaca [SI]:220 (AC boundary bus, share 0.061 of the SI border by tie rating) |
| SI | 282.3 | HR:krsko [SI]:hv (AC boundary bus, share 0.445 of the SI border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 4 lumped GSUs (1906 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 16 embedded buses behind lumped supply equivalents (4328 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.5 MW, type C 5 MW, type D 10 MW; HOPS / HEP ODS proposal of national thresholds (public consultation 2017); HERA approved the national thresholds 2018-11-15 [VERIFY that the approved values equal the proposal]): 26 synchronous units (2002.9 MW) of type B+ and 28 running converter units (1140.0 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 59 smaller units (392.6 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 0/1 units (342 MW offline); gas 19/19 units (0 MW offline); oil 0/4 units (1070 MW offline); biomass 16/16 units (0 MW offline); waste 16/16 units (-0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): biomass register 0.0 MW vs energy-charts 69.2 MW; 86.5 MW added, embedded, spread by population
- register gap aggregate (estimated): gas register 350.8 MW vs energy-charts 373.6 MW; 50.4 MW added, embedded, spread by population
- register gap aggregate (estimated): waste register 0.0 MW vs energy-charts 4.8 MW; 6.0 MW added, embedded, spread by population
- boundary voltage support (synthetic external-grid equivalent): 12 AC boundary buses hold 1.0 pu with Q +/- 0.5 x tie rating, 0 MW (the neighbouring grids hold the border voltage)
- slack: largest dispatched EHV synchronous unit Zakucac at Zakucac 220kV gen bus, reactive band +/-10000 MVAr (synthetic)
- no bus shunts needed: the no-limit Newton has every bus inside 0.95-1.05 pu and every unit inside its reactive range

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: built and attempted 2026-11-01; did not solve: the copied no-limit Newton diverged at every load stage down to zero (only one voltage-controlling unit, Zakucac); gridsim pf of the r1 tables without shunts converged only to V min 0.7450 pu. No r1 case folder was kept.
- r2: AC boundary buses get external-grid voltage equivalents (0 MW, 1.0 pu, Q +/- 0.5 x tie rating; synthetic); otherwise identical to r1.
- r4: RfG voltage control with the NATIONAL type B / C thresholds: before this round every unit below the 300 MW EHV placement size and every converter unit ran at unity pf whatever its size (no RfG rule at all). Now a committed register UNIT of type B or more (synchronous) or type C or more (converter, running) regulates voltage on its embedded bus (synchronous Q -0.30..+0.62 x MW, converter +/- 0.33 x MW); smaller units and register-gap aggregates stay pq at Q = 0; idle converters never regulate.
- r4: Demand shares from the WorldPop 2020 1 km population grid (CC BY 4.0, doi:10.5258/SOTON/WP00647; a build step) instead of GeoNames points: every populated cell goes to its nearest demand station (Voronoi catchment), so a big city is shared by every station around it instead of landing on the station nearest its single GeoNames point (Vienna on Kledering, Prague on Malesice). The demand total (energy-charts balance) is unchanged; only its spread. GeoNames PPLX sections no longer used.

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

- Core Static Grid Model, 9th release (2026-03): HOPS lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (HOPS for Croatia)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Croatia (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Croatia units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Croatia 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Croatia, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries HRV ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf croatia-spine-400-220-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Croatia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (55 buses)
  converged in 4 iteration(s), mismatch 1.54E-013 pu   losses 26.418 MW / -547.982 MVAr
  voltage range 0.9887 - 1.0200 pu
  lowest voltages:
      bus 51     0.9887 pu    -14.278 deg
      bus 35     0.9899 pu    -19.479 deg
      bus 19     0.9908 pu    -24.376 deg
      bus 22     0.9915 pu    -20.387 deg
      bus 32     0.9921 pu    -22.712 deg
      bus 46     0.9924 pu    -16.188 deg
      bus 28     0.9940 pu    -14.410 deg
      bus 49     0.9940 pu    -14.410 deg
      bus 48     0.9952 pu    -11.818 deg
      bus 1      1.0000 pu    -13.025 deg
      bus 2      1.0000 pu    -11.675 deg
      bus 4      1.0000 pu    -14.181 deg
(warm start baked into buses.json: flat start took 4 Newton iterations)
(the build pipeline reading of the pf result) angle spread 24.535 deg; branches over 100 %: 0, over 80 %: 0; highest: emb:HR:tumbri:hv (Tumbri 400kV embedded bus - Tumbri 400kV) 77.5 %; emb:HR:te sisak:220 (Te Sisak 220kV embedded bus - Te Sisak 220kV) 72.2 %; jao:31T-0000-B-0001Y:4 (Zerjavinec 400kV - Zerjavinec 220kV) 68.7 %; emb:HR:melina:220 (Melina 220kV embedded bus - Melina 220kV) 66.0 %; emb:HR:pehlin:220 (Pehlin 220kV embedded bus - Pehlin 220kV) 60.8 %
$ gridsim pf croatia-spine-400-220-r4 (warm start)   (exit 0, 0.6 s)
Power flow - Croatia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (55 buses)
  converged in 1 iteration(s), mismatch 1.73E-013 pu   losses 26.418 MW / -547.982 MVAr
  voltage range 0.9887 - 1.0200 pu
  lowest voltages:
      bus 51     0.9887 pu    -14.278 deg
      bus 35     0.9899 pu    -19.479 deg
      bus 19     0.9908 pu    -24.376 deg
      bus 22     0.9915 pu    -20.387 deg
      bus 32     0.9921 pu    -22.712 deg
      bus 46     0.9924 pu    -16.188 deg
      bus 28     0.9940 pu    -14.410 deg
      bus 49     0.9940 pu    -14.410 deg
      bus 48     0.9952 pu    -11.818 deg
      bus 1      1.0000 pu    -13.025 deg
      bus 2      1.0000 pu    -11.675 deg
      bus 4      1.0000 pu    -14.181 deg
$ gridsim physics-check croatia-spine-400-220-r4   (exit 0, 0.6 s)
Physics-law audit  -  croatia-spine-400-220-r4  (55 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.88E-012 | MW | independent dissipation 26.417565 MW (branch 26.4176 + shunt 0.0000) vs reported loss 26.417565 MW |
| 2 | Ohm's law | Holds | 2.54E-012 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 2.03E-012 | MW | total network loss 26.417565 MW vs reported 26.417565 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 3.64E-012 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.35E-011 | MVA | same residual as law 6, reactive component included at 30 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
