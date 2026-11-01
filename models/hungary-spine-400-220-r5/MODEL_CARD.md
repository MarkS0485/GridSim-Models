# MODEL CARD: Hungary transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Hungary study results. A solvable rough map of the Hungary 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, MAVIR) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r5 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 6868.9 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 110 (15 cross-border boundary buses, 40 generator / embedded buses), branches 153 (lines 104, transformers 49), generators 695.
- Buses by kV: 400 kV 45, 220 kV 25, 110 kV 35, 21 kV 5.
- Dispatch 3972.4 MW (Hungary plant) + boundary imports 3789.0 MW; demand 7622.9 MW (incl. boundary exports 834.0 MW and storage charging).
- Slack: 1 reference: Dunamenti #2.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 110 | 0 (0.0%) | 0 (0.0%) | 55 (50.0%) | 55 (50.0%) |
| Branches | 153 | 78 (51.0%) | 6 (3.9%) | 69 (45.1%) | 0 (0.0%) |
| Generators | 695 | 0 (0.0%) | 0 (0.0%) | 695 (100.0%) | 0 (0.0%) |
| Demand points | 40 | 0 (0.0%) | 0 (0.0%) | 40 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 7 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 7 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, MAVIR: 56 internal line rows (by class {'hv': 37, '220': 19}), 19 tie-line rows used, 3 JAO transformers placed.
- Positions: {'osm_whole_word': 41, 'jao_map': 3, 'pypsa_osm': 11, 'neighbour_mean': 0, 'boundary': 15} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 24 circuits, 13 OSM-only stations, 4 chain duplicates of JAO lines skipped; per km (HV) R 0.0284 ohm, X 0.3137 ohm, B 3.579 uS, Imax 2000 A (medians of 35 JAO lines); 220 kV R 0.0597, X 0.4151, B 2.726, Imax 730 A.
- Synthetic couplings (median JAO unit {'mva': 500.1, 'x_pct_own': 12.01, 'x_over_r': 59.5, 'how': 'median of 3 JAO Hungary 400(380)/220 kV units'}): ['god', 'god kelet', 'gyor', 'kerepes', 'szolnok']; near-site [].
- JAO transformers not modelled: [].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [70]).
- Shape check (crow-fly vs published length): 0 outliers [].
- Note: 750 kV tie rows not modelled (no 750 kV bus in round 1): ['Szabolcsbaka - Zahidno Ukrainska']

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 94.6 | 0.0 |
| biomass | 303.6 | 180.8 |
| coal | 46.4 | 37.1 |
| gas | 3113.5 | 1931.0 |
| hydro_res | 28.0 | 16.7 |
| hydro_ror | 19.7 | 17.4 |
| interconnector | 3789.0 | 3789.0 |
| lignite | 1134.0 | 186.9 |
| nuclear | 2027.0 | 1453.0 |
| oil | 451.0 | 0.0 |
| other | 81.9 | 66.0 |
| solar | 4068.3 | 3.3 |
| waste | 24.0 | 18.3 |
| wind_onshore | 319.0 | 61.9 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| AT | 987.1 | HU:zurndorf [AT]:hv (AC boundary bus, share 0.858 of the AT border by tie rating) |
| AT | 81.4 | HU:neusiedl [AT]:220 (AC boundary bus, share 0.071 of the AT border by tie rating) |
| AT | 81.4 | HU:wien [AT]:220 (AC boundary bus, share 0.071 of the AT border by tie rating) |
| HR | -54.0 | HU:zerjavinec [HR]:hv (AC boundary bus, share 0.333 of the HR border by tie rating) |
| HR | -108.0 | HU:ernestinovo [HR]:hv (AC boundary bus, share 0.667 of the HR border by tie rating) |
| RO | -282.7 | HU:arad [RO]:hv (AC boundary bus, share 0.444 of the RO border by tie rating) |
| RO | -353.3 | HU:nadab [RO]:hv (AC boundary bus, share 0.556 of the RO border by tie rating) |
| RS | 95.0 | HU:subotica [RS]:hv (AC boundary bus, share 1.000 of the RS border by tie rating) |
| SK | 486.2 | HU:levice [SK]:hv (AC boundary bus, share 0.200 of the SK border by tie rating) |
| SK | 972.4 | HU:gabcikovo [SK]:hv (AC boundary bus, share 0.400 of the SK border by tie rating) |
| SK | 486.2 | HU:rimavska sobota [SK]:hv (AC boundary bus, share 0.200 of the SK border by tie rating) |
| SK | 486.2 | HU:velky dur [SK]:hv (AC boundary bus, share 0.200 of the SK border by tie rating) |
| SI | 113.0 | HU:cirkovce [SI]:hv (AC boundary bus, share 1.000 of the SI border by tie rating) |
| UA | -10.3 | HU:mukachevo [UA]:220 (AC boundary bus, share 0.286 of the UA border by tie rating) |
| UA | -25.7 | HU:mukachevo [UA]:hv (AC boundary bus, share 0.714 of the UA border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 5 lumped GSUs (5927 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 35 embedded buses behind lumped supply equivalents (6162 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.2 MW, type C 5 MW, type D 25 MW; MAVIR thresholds as reported by Vokony (RE&PQJ paper, Hungarian RfG categories) [VERIFY against the MEKH-approved MAVIR Art. 5(3) proposal]): 11 synchronous units (630.7 MW) of type B+ and 10 running converter units (319.0 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 573 smaller units (4162.9 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 34/34 units (-0 MW offline); lignite 1/2 units (250 MW offline); gas 6/16 units (694 MW offline); oil 0/3 units (451 MW offline); biomass 3/4 units (40 MW offline); waste 1/1 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): coal register 0.0 MW vs energy-charts 37.1 MW; 46.4 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 3.4 MW vs energy-charts 66.0 MW; 78.5 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Dunamenti #2 at Dunamenti 220kV gen bus, reactive band +/-10000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 7 reactors 140 MVAr, 0 capacitors 0 MVAr (synthetic; JAO publishes no reactive compensation): Cirkovce [SI] 400kV -20, Osm Virtual_Relation/5203259:1 400kV -20, Heviz 400kV -20, Szombathely 400kV -20, Zerjavinec [HR] 400kV -20, Szombathely 1 400kV -20, Zurndorf [AT] 400kV -20

## Synthetic or fitted values

- Bus shunts (above) are synthetic reactive repairs. Boundary buses, GSU / embedded buses and the slack band are synthetic. No rating, impedance, coupling size or demand weight was changed to clear a solver symptom.

## Round history

- r1: first build (build-first batch); reactive repair by fixed bus shunts only.
- r5: SEASONAL RATINGS: JAO line / tie-line Imax is now the TSO's calendar period covering the snapshot date (2025-11-19; JAO Core SGM 9th release Handbook Annex 1: MAVIR Period 4 = 1 Sep - 30 Nov, PSE Period 4 = 1 Oct - 31 Dec, Transelectrica Period 2 = Mar - May / Sep - Nov), else the row's Fixed, else the largest period [VERIFY]. Earlier rounds took the largest period (the winter value). Applied to EVERY JAO row by the same rule; OSM-added corridors take the per-km median of the re-rated JAO rows. No other change from the previous round.

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

- Core Static Grid Model, 9th release (2026-03): MAVIR lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (MAVIR for Hungary)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Hungary (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Hungary units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Hungary 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Hungary, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries HUN ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf hungary-spine-400-220-r5   (flat start: vm 1, vaDeg 0; exit 0, 0.5 s)
Power flow - Hungary transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (110 buses)
  converged in 6 iteration(s), mismatch 1.60E-010 pu   losses 88.424 MW / -1201.502 MVAr
  voltage range 0.9618 - 1.0505 pu
  lowest voltages:
      bus 66     0.9618 pu    -22.260 deg
      bus 106    0.9621 pu    -21.902 deg
      bus 70     1.0019 pu    -12.265 deg
      bus 51     1.0078 pu    -11.101 deg
      bus 67     1.0128 pu    -13.547 deg
      bus 57     1.0155 pu     -7.187 deg
      bus 103    1.0159 pu     -6.647 deg
      bus 99     1.0171 pu     -9.774 deg
      bus 46     1.0184 pu    -10.276 deg
      bus 63     1.0184 pu    -10.276 deg
      bus 52     1.0186 pu    -15.281 deg
      bus 92     1.0186 pu    -10.061 deg
(warm start baked into buses.json: flat start took 6 Newton iterations)
(the build pipeline reading of the pf result) angle spread 28.211 deg; branches over 100 %: 0, over 80 %: 2; highest: jao:Levice - God:64 (God 400kV - Levice [SK] 400kV) 94.0 %; osm:zuglo - god kelet 220 (OSM relation/4744535:a-220) (Zuglo 220kV - God Kelet 220kV) 89.3 %; gsu:HU:gonyu:hv (Gonyu 400kV gen bus - Gonyu 400kV) 71.3 %; jao:Szolnok - Szeged:2 (Szolnok 220kV - Szeged 220kV) 69.7 %; gsu:HU:zuglo:220 (Zuglo 220kV gen bus - Zuglo 220kV) 69.3 %
$ gridsim pf hungary-spine-400-220-r5 (warm start)   (exit 0, 0.5 s)
Power flow - Hungary transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (110 buses)
  converged in 4 iteration(s), mismatch 1.60E-010 pu   losses 88.424 MW / -1201.502 MVAr
  voltage range 0.9618 - 1.0505 pu
  lowest voltages:
      bus 66     0.9618 pu    -22.260 deg
      bus 106    0.9621 pu    -21.902 deg
      bus 70     1.0019 pu    -12.265 deg
      bus 51     1.0078 pu    -11.101 deg
      bus 67     1.0128 pu    -13.547 deg
      bus 57     1.0155 pu     -7.187 deg
      bus 103    1.0159 pu     -6.647 deg
      bus 99     1.0171 pu     -9.774 deg
      bus 46     1.0184 pu    -10.276 deg
      bus 63     1.0184 pu    -10.276 deg
      bus 52     1.0186 pu    -15.281 deg
      bus 92     1.0186 pu    -10.061 deg
$ gridsim physics-check hungary-spine-400-220-r5   (exit 0, 0.5 s)
Physics-law audit  -  hungary-spine-400-220-r5  (110 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 3.41E-012 | MW | independent dissipation 88.424043 MW (branch 88.4240 + shunt 0.0000) vs reported loss 88.424043 MW |
| 2 | Ohm's law | Holds | 2.86E-012 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 3.45E-012 | MW | total network loss 88.424043 MW vs reported 88.424043 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.61E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.60E-008 | MVA | same residual as law 6, reactive component included at 96 PQ bus(es), by the bus types the solve ended with; 2 of them declared PV and solved as PQ (2 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
