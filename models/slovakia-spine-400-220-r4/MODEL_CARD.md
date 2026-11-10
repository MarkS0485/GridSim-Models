# Slovakia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**UnvalidatedAtScale.** Not checked against official Slovakia study results. A solvable rough map of the Slovakia 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, SEPS) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r4 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 3875.0 MW; interval {'public_power_interval_utc': '2025-11-19T16:00:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 3600}).
- Buses 83 (9 cross-border boundary buses, 33 generator / embedded buses), branches 121 (lines 79, transformers 42), generators 369.
- Buses by kV: 400 kV 40, 220 kV 10, 110 kV 29, 21 kV 4.
- Dispatch 4378.1 MW (Slovakia plant) + boundary imports 2495.0 MW; demand 6796.6 MW (incl. boundary exports 3050.0 MW and storage charging).
- Slack: 1 reference: Bohunice 3.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 83 | 0 (0.0%) | 0 (0.0%) | 41 (49.4%) | 42 (50.6%) |
| Branches | 121 | 54 (44.6%) | 9 (7.4%) | 58 (47.9%) | 0 (0.0%) |
| Generators | 369 | 0 (0.0%) | 0 (0.0%) | 369 (100.0%) | 0 (0.0%) |
| Demand points | 33 | 0 (0.0%) | 0 (0.0%) | 33 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 0 | - | - | - | - |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, SEPS: 42 internal line rows (by class {'hv': 34, '220': 8}), 12 tie-line rows used, 3 JAO transformers placed.
- Positions: {'osm_whole_word': 34, 'jao_map': 1, 'pypsa_osm': 6, 'neighbour_mean': 0, 'boundary': 9} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 18 circuits, 12 OSM-only stations, 13 chain duplicates of JAO lines skipped; per km (HV) R 0.0230 ohm, X 0.2835 ohm, B 3.949 uS, Imax 2000 A (medians of 34 JAO lines); 220 kV R 0.0659, X 0.4101, B 2.712, Imax 665 A.
- Synthetic couplings (median JAO unit {'mva': 249.4, 'x_pct_own': 12.35, 'x_over_r': 63.8, 'how': 'median of 3 JAO Slovakia 400(380)/220 kV units'}): ['lemesany', 'senica', 'sucany', 'vojany']; near-site [].
- JAO transformers not modelled: [].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [50]).
- Shape check (crow-fly vs published length): 0 outliers [].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 5.3 | 0.0 |
| biomass | 119.1 | 95.3 |
| coal | 329.0 | 0.0 |
| gas | 1076.0 | 627.8 |
| hydro_ps | 1004.0 | 302.4 |
| hydro_res | 157.4 | 80.2 |
| hydro_ror | 1295.1 | 560.4 |
| interconnector | 2495.0 | 2495.0 |
| lignite | 21.7 | 17.4 |
| nuclear | 2942.0 | 2467.0 |
| oil | 67.2 | 53.8 |
| other | 215.4 | 172.3 |
| solar | 900.4 | 0.2 |
| wind_onshore | 1.6 | 1.3 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| CZ | 1291.9 | SK:sokolnice [CZ]:hv (AC boundary bus, share 0.628 of the CZ border by tie rating) |
| CZ | 646.0 | SK:nosovice [CZ]:hv (AC boundary bus, share 0.314 of the CZ border by tie rating) |
| CZ | 118.1 | SK:liskovec [CZ]:220 (AC boundary bus, share 0.057 of the CZ border by tie rating) |
| HU | -972.4 | SK:gonyu [HU]:hv (AC boundary bus, share 0.400 of the HU border by tie rating) |
| HU | -486.2 | SK:god [HU]:hv (AC boundary bus, share 0.200 of the HU border by tie rating) |
| HU | -486.2 | SK:sajoivanka [HU]:hv (AC boundary bus, share 0.200 of the HU border by tie rating) |
| HU | -486.2 | SK:gyor [HU]:hv (AC boundary bus, share 0.200 of the HU border by tie rating) |
| PL | 439.0 | SK:krosno [PL]:hv (AC boundary bus, share 1.000 of the PL border by tie rating) |
| UA | -619.0 | SK:mukachevo [UA]:hv (AC boundary bus, share 1.000 of the UA border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 4 lumped GSUs (5685 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 29 embedded buses behind lumped supply equivalents (3193 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.1 MW, type C 5 MW, type D 20 MW; URSO decision 0005/2018/E-EU (SEPS 'Hranicne hodnoty maximalnej kapacity ... typu B, C a D')): 32 synchronous units (1383.5 MW) of type B+ and 0 running converter units (0.0 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 177 smaller units (905.7 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 0/2 units (329 MW offline); lignite 28/28 units (0 MW offline); gas 3/8 units (259 MW offline); oil 28/28 units (0 MW offline); biomass 28/28 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): biomass register 0.0 MW vs energy-charts 95.3 MW; 119.1 MW added, embedded, spread by population
- register gap aggregate (estimated): lignite register 0.0 MW vs energy-charts 17.4 MW; 21.7 MW added, embedded, spread by population
- register gap aggregate (estimated): oil register 0.0 MW vs energy-charts 53.8 MW; 67.2 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 0.0 MW vs energy-charts 172.3 MW; 215.4 MW added, embedded, spread by population
- register gap aggregate (estimated): wind_onshore register 0.0 MW vs energy-charts 1.3 MW; 1.6 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Bohunice 3 at J. Bohunice 400kV gen bus, reactive band +/-10000 MVAr (synthetic)
- no bus shunts needed: the no-limit Newton has every bus inside 0.95-1.05 pu and every unit inside its reactive range

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: first build (build-first batch); reactive repair by fixed bus shunts only.
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

- Core Static Grid Model, 9th release (2026-03): SEPS lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (SEPS for Slovakia)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Slovakia (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Slovakia units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Slovakia 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Slovakia, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries SVK ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Database licence: ODbL 1.0. See [source credits](ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf slovakia-spine-400-220-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.7 s)
Power flow - Slovakia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (83 buses)
  converged in 6 iteration(s), mismatch 1.51E-009 pu   losses 91.229 MW / -536.795 MVAr
  voltage range 0.9925 - 1.0361 pu
  lowest voltages:
      bus 46     0.9925 pu    -12.270 deg
      bus 79     0.9937 pu     -9.643 deg
      bus 42     1.0075 pu     -9.760 deg
      bus 76     1.0086 pu     -5.837 deg
      bus 43     1.0100 pu    -24.082 deg
      bus 48     1.0122 pu    -13.211 deg
      bus 47     1.0145 pu     -7.033 deg
      bus 49     1.0156 pu    -12.552 deg
      bus 80     1.0156 pu     -5.059 deg
      bus 5      1.0158 pu    -13.905 deg
      bus 45     1.0160 pu     -5.851 deg
      bus 7      1.0162 pu    -12.282 deg
(warm start baked into buses.json: flat start took 6 Newton iterations)
(the build pipeline reading of the pf result) angle spread 24.833 deg; branches over 100 %: 0, over 80 %: 2; highest: jao:J. Bohunice - Krizovany:28 (J. Bohunice 400kV - Krizovany 400kV) 99.6 %; synth:coupling:senica~senica (Senica 400kV - Senica 220kV) 81.0 %; jao:V. Dur - Mochovce:39 (V. Dur 400kV - Mochovce 400kV) 73.9 %; jao:Nosovice - Varin:47 (Varin 400kV - Nosovice [CZ] 400kV) 73.2 %; jao:V. Dur - Mochovce:38 (V. Dur 400kV - Mochovce 400kV) 72.8 %
$ gridsim pf slovakia-spine-400-220-r4 (warm start)   (exit 0, 0.7 s)
Power flow - Slovakia transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (83 buses)
  converged in 4 iteration(s), mismatch 1.51E-009 pu   losses 91.229 MW / -536.795 MVAr
  voltage range 0.9925 - 1.0361 pu
  lowest voltages:
      bus 46     0.9925 pu    -12.270 deg
      bus 79     0.9937 pu     -9.643 deg
      bus 42     1.0075 pu     -9.760 deg
      bus 76     1.0086 pu     -5.837 deg
      bus 43     1.0100 pu    -24.082 deg
      bus 48     1.0122 pu    -13.211 deg
      bus 47     1.0145 pu     -7.033 deg
      bus 49     1.0156 pu    -12.552 deg
      bus 80     1.0156 pu     -5.059 deg
      bus 5      1.0158 pu    -13.905 deg
      bus 45     1.0160 pu     -5.851 deg
      bus 7      1.0162 pu    -12.282 deg
$ gridsim physics-check slovakia-spine-400-220-r4   (exit 0, 0.7 s)
Physics-law audit  -  slovakia-spine-400-220-r4  (83 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 5.12E-013 | MW | independent dissipation 91.228943 MW (branch 91.2289 + shunt 0.0000) vs reported loss 91.228943 MW |
| 2 | Ohm's law | Holds | 5.77E-012 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 9.52E-013 | MW | total network loss 91.228943 MW vs reported 91.228943 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 3.06E-008 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.51E-007 | MVA | same residual as law 6, reactive component included at 67 PQ bus(es), by the bus types the solve ended with; 1 of them declared PV and solved as PQ (1 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
