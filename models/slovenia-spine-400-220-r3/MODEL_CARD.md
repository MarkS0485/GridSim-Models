# MODEL CARD: Slovenia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Slovenia study results. A solvable rough map of the Slovenia 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, ELES) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r3 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 2022.0 MW; interval {'public_power_interval_utc': '2025-11-19T16:00:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 3600}).
- Buses 36 (10 cross-border boundary buses, 11 generator / embedded buses), branches 54 (lines 34, transformers 20), generators 136.
- Buses by kV: 400 kV 14, 220 kV 11, 110 kV 9, 21 kV 2.
- Dispatch 2195.2 MW (Slovenia plant) + boundary imports 1201.0 MW; demand 3355.9 MW (incl. boundary exports 1383.0 MW and storage charging).
- Slack: 1 reference: Krsko 1.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 36 | 0 (0.0%) | 0 (0.0%) | 15 (41.7%) | 21 (58.3%) |
| Branches | 54 | 28 (51.9%) | 7 (13.0%) | 19 (35.2%) | 0 (0.0%) |
| Generators | 136 | 0 (0.0%) | 0 (0.0%) | 136 (100.0%) | 0 (0.0%) |
| Demand points | 17 | 0 (0.0%) | 0 (0.0%) | 17 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 0 | - | - | - | - |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, ELES: 14 internal line rows (by class {'hv': 11, '220': 3}), 12 tie-line rows used, 2 JAO transformers placed.
- Positions: {'osm_whole_word': 14, 'jao_map': 0, 'pypsa_osm': 1, 'neighbour_mean': 0, 'boundary': 10} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 5 circuits, 1 OSM-only stations, 0 chain duplicates of JAO lines skipped; per km (HV) R 0.0305 ohm, X 0.3201 ohm, B 3.543 uS, Imax 1920 A (medians of 11 JAO lines); 220 kV R 0.0592, X 0.4093, B 2.819, Imax 960 A.
- Synthetic couplings (median JAO unit {'mva': 400.1, 'x_pct_own': 11.83, 'x_over_r': 82.6, 'how': 'median of 2 JAO Slovenia 400(380)/220 kV units'}): ['cirkovce', 'divaca', 'sostanj']; near-site [].
- JAO transformers not modelled: ['TR Bericevo 411: 123/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Bericevo 211: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Bericevo 212: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Cirkovce 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Cirkovce 412: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Klece 211: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Klece 212: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Krsko 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Krsko 412: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Maribor 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Maribor 412: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Okroglo 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Okroglo 412: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Podlog 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Podlog 211: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Podlog 212: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'PST Divaca: phase shifter 400/400 kV, not modelled', 'TR Divaca 211: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Divaca 212: 115/220 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Divaca 411: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Divaca 412: 115/400 kV (not an HV/220 kV unit; no 110 kV layer)'].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [25]).
- Shape check (crow-fly vs published length): 0 outliers [].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 62.6 | 0.0 |
| biomass | 30.7 | 24.6 |
| coal | 124.0 | 0.0 |
| gas | 264.2 | 241.1 |
| hydro_ps | 181.9 | 172.5 |
| hydro_res | 188.7 | 0.0 |
| hydro_ror | 938.1 | 877.6 |
| interconnector | 1201.0 | 1201.0 |
| lignite | 1355.0 | 176.2 |
| nuclear | 742.1 | 702.7 |
| solar | 93.6 | 0.0 |
| waste | 0.2 | 0.2 |
| wind_onshore | 0.4 | 0.3 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| AT | 145.2 | SI:obersielach [AT]:220 (AC boundary bus, share 0.121 of the AT border by tie rating) |
| AT | 1055.8 | SI:kainachtal [AT]:hv (AC boundary bus, share 0.879 of the AT border by tie rating) |
| HR | -122.2 | SI:zerjavinec [HR]:hv (AC boundary bus, share 0.192 of the HR border by tie rating) |
| HR | -32.8 | SI:zerjavinec [HR]:220 (AC boundary bus, share 0.052 of the HR border by tie rating) |
| HR | -146.6 | SI:melina [HR]:hv (AC boundary bus, share 0.231 of the HR border by tie rating) |
| HR | -40.3 | SI:pehlin [HR]:220 (AC boundary bus, share 0.063 of the HR border by tie rating) |
| HR | -293.2 | SI:tumbri [HR]:hv (AC boundary bus, share 0.462 of the HR border by tie rating) |
| HU | -113.0 | SI:hevitz [HU]:hv (AC boundary bus, share 1.000 of the HU border by tie rating) |
| IT | -530.7 | SI:redipuglia [IT]:hv (AC boundary bus, share 0.836 of the IT border by tie rating) |
| IT | -104.3 | SI:padriciano [IT]:220 (AC boundary bus, share 0.164 of the IT border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 2 lumped GSUs (2449 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 9 embedded buses behind lumped supply equivalents (2089 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.15 MW, type C 5 MW, type D 25 MW; ELES proposal of national thresholds coordinated with SODO ('Predlog nacionalnih pragov', Agen-RS) [VERIFY the approval]): 27 synchronous units (1414.1 MW) of type B+ and 0 running converter units (0.0 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 41 smaller units (156.2 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 0/1 units (124 MW offline); lignite 1/1 units (0 MW offline); gas 11/11 units (0 MW offline); biomass 9/9 units (0 MW offline); waste 9/9 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): nuclear register 727.0 MW vs energy-charts 702.7 MW; 15.1 MW added, embedded, spread by population
- register gap aggregate (estimated): hydro_ror register 847.4 MW vs energy-charts 877.6 MW; 90.7 MW added, embedded, spread by population
- register gap aggregate (estimated): biomass register 0.0 MW vs energy-charts 24.6 MW; 30.8 MW added, embedded, spread by population
- register gap aggregate (estimated): gas register 198.0 MW vs energy-charts 241.1 MW; 66.2 MW added, embedded, spread by population
- register gap aggregate (estimated): hydro_ps register 180.0 MW vs energy-charts 172.5 MW; 1.9 MW added, embedded, spread by population
- register gap aggregate (estimated): waste register 0.0 MW vs energy-charts 0.2 MW; 0.2 MW added, embedded, spread by population
- register gap aggregate (estimated): wind_onshore register 0.0 MW vs energy-charts 0.3 MW; 0.4 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Krsko 1 at Krsko 400kV gen bus, reactive band +/-10000 MVAr (synthetic)
- no bus shunts needed: the no-limit Newton has every bus inside 0.95-1.05 pu and every unit inside its reactive range

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

- Core Static Grid Model, 9th release (2026-03): ELES lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (ELES for Slovenia)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Slovenia (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Slovenia units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Slovenia 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Slovenia, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries SVN ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf slovenia-spine-400-220-r3   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Slovenia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (36 buses)
  converged in 4 iteration(s), mismatch 1.56E-012 pu   losses 34.740 MW / -10.997 MVAr
  voltage range 0.9926 - 1.0200 pu
  lowest voltages:
      bus 18     0.9926 pu    -11.959 deg
      bus 20     0.9939 pu    -11.579 deg
      bus 15     0.9954 pu    -11.326 deg
      bus 21     0.9959 pu    -13.697 deg
      bus 17     0.9966 pu    -13.400 deg
      bus 22     0.9991 pu    -12.782 deg
      bus 11     1.0006 pu    -13.654 deg
      bus 3      1.0026 pu    -12.299 deg
      bus 8      1.0029 pu    -11.760 deg
      bus 35     1.0056 pu     -1.060 deg
      bus 23     1.0060 pu     -7.192 deg
      bus 24     1.0078 pu     -6.393 deg
(warm start baked into buses.json: flat start took 4 Newton iterations)
(the build pipeline reading of the pf result) angle spread 17.927 deg; branches over 100 %: 0, over 80 %: 1; highest: gsu:SI:krsko:hv (Krsko 400kV gen bus - Krsko 400kV) 80.2 %; emb:SI:sostanj:220 (Sostanj 220kV embedded bus - Sostanj 220kV) 78.4 %; emb:SI:cirkovce:220 (Cirkovce 220kV embedded bus - Cirkovce 220kV) 75.1 %; emb:SI:maribor:hv (Maribor 400kV embedded bus - Maribor 400kV) 73.3 %; emb:SI:krsko:hv (Krsko 400kV embedded bus - Krsko 400kV) 72.8 %
$ gridsim pf slovenia-spine-400-220-r3 (warm start)   (exit 0, 0.6 s)
Power flow - Slovenia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (36 buses)
  converged in 1 iteration(s), mismatch 2.37E-013 pu   losses 34.740 MW / -10.997 MVAr
  voltage range 0.9926 - 1.0200 pu
  lowest voltages:
      bus 18     0.9926 pu    -11.959 deg
      bus 20     0.9939 pu    -11.579 deg
      bus 15     0.9954 pu    -11.326 deg
      bus 21     0.9959 pu    -13.697 deg
      bus 17     0.9966 pu    -13.400 deg
      bus 22     0.9991 pu    -12.782 deg
      bus 11     1.0006 pu    -13.654 deg
      bus 3      1.0026 pu    -12.299 deg
      bus 8      1.0029 pu    -11.760 deg
      bus 35     1.0056 pu     -1.060 deg
      bus 23     1.0060 pu     -7.192 deg
      bus 24     1.0078 pu     -6.393 deg
$ gridsim physics-check slovenia-spine-400-220-r3   (exit 0, 0.7 s)
Physics-law audit  -  slovenia-spine-400-220-r3  (36 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 5.54E-012 | MW | independent dissipation 34.739690 MW (branch 34.7397 + shunt 0.0000) vs reported loss 34.739690 MW |
| 2 | Ohm's law | Holds | 1.36E-012 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 5.41E-012 | MW | total network loss 34.739690 MW vs reported 34.739690 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 4.41E-012 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.95E-011 | MVA | same residual as law 6, reactive component included at 26 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
