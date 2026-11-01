# MODEL CARD: Austria transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Austria study results. A solvable rough map of the Austria 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, APG) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r4 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 9969.2 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 189 (19 cross-border boundary buses, 56 generator / embedded buses), branches 350 (lines 266, transformers 84), generators 567.
- Buses by kV: 380 kV 57, 220 kV 76, 110 kV 44, 21 kV 12.
- Dispatch 8609.3 MW (Austria plant) + boundary imports 3776.0 MW; demand 12187.2 MW (incl. boundary exports 2478.0 MW and storage charging).
- Slack: 1 reference: Simmering.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 189 | 0 (0.0%) | 0 (0.0%) | 114 (60.3%) | 75 (39.7%) |
| Branches | 350 | 115 (32.9%) | 12 (3.4%) | 223 (63.7%) | 0 (0.0%) |
| Generators | 567 | 0 (0.0%) | 0 (0.0%) | 567 (100.0%) | 0 (0.0%) |
| Demand points | 50 | 0 (0.0%) | 0 (0.0%) | 50 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 1 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 1 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, APG: 73 internal line rows (by class {'220': 38, 'hv': 35}), 29 tie-line rows used, 17 JAO transformers placed.
- Positions: {'osm_whole_word': 42, 'jao_map': 15, 'pypsa_osm': 57, 'neighbour_mean': 0, 'boundary': 19} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: []).
- PyPSA-Eur OSM gap lines (estimated): 157 circuits, 61 OSM-only stations, 10 chain duplicates of JAO lines skipped; per km (HV) R 0.0216 ohm, X 0.3059 ohm, B 3.782 uS, Imax 2300 A (medians of 33 JAO lines); 220 kV R 0.0790, X 0.4086, B 2.845, Imax 810 A.
- Synthetic couplings (median JAO unit {'mva': 1076.6, 'x_pct_own': 10.4, 'x_over_r': 72.3, 'how': 'median of 17 JAO Austria 400(380)/220 kV units'}): ['bisamberg', 'duernrohr', 'kledering', 'osm way/291703253', 'pongau', 'salzburg']; near-site [].
- JAO transformers not modelled: ['PST Ernsthofen EHPST: phase shifter 220/220 kV, not modelled', 'PST Lienz LIPST: phase shifter 220/220 kV, not modelled', 'PST Tauern TAPST: phase shifter 220/220 kV, not modelled', 'PST Ternitz TEPST: phase shifter 220/220 kV, not modelled', 'TR Tauern TARHU43: no station with both voltage classes named in it', 'TR Nauders NRPST21: phase shifter 220/220 kV, not modelled', 'TR Nauders NRPST22: phase shifter 220/220 kV, not modelled'].
- Tie rows dropped or re-read: ['Meiningen - Buers 406A (Meiningen - Buers): home end unclear (map end 61.4 km from a home station)', 'Meiningen - Ruethi 407 (Meiningen - Ruethi): home end unclear and no map line', 'Meiningen - Ruethi 408 (Meiningen - Ruethi): home end unclear and no map line', 'Walgauwerk - Buers 405A (Walgauwerk - Buers): home end unclear (map end 61.4 km from a home station)'].
- Islands in the topology: 1 (sizes [133]).
- Shape check (crow-fly vs published length): 3 outliers [{'line': 'Bisamberg - Wien Suedost 436B', 'crow_km': 25.8, 'len_km': 76.0}, {'line': 'Duernrohr - Wien Suedost 435A', 'crow_km': 45.5, 'len_km': 127.0}, {'line': 'Etzersdorf - Kronstorf 434A', 'crow_km': 95.5, 'len_km': 0.7}].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 73.9 | 0.0 |
| biomass | 220.3 | 196.0 |
| gas | 4746.0 | 1334.8 |
| hydro_ps | 5958.0 | 1537.2 |
| hydro_res | 6418.6 | 746.8 |
| hydro_ror | 3406.3 | 2732.4 |
| interconnector | 3776.0 | 3776.0 |
| oil | 170.0 | 0.0 |
| other | 27.6 | 22.1 |
| solar | 926.4 | 0.0 |
| waste | 123.0 | 100.0 |
| wind_onshore | 2839.6 | 1940.0 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| CZ | 1093.1 | AT:slavetice [CZ]:hv (AC boundary bus, share 0.707 of the CZ border by tie rating) |
| CZ | 452.9 | AT:sokolnice [CZ]:220 (AC boundary bus, share 0.293 of the CZ border by tie rating) |
| DE | 80.1 | AT:pirach [DE]:220 (AC boundary bus, share 0.053 of the DE border by tie rating) |
| DE | 80.1 | AT:pleinting [DE]:220 (AC boundary bus, share 0.053 of the DE border by tie rating) |
| DE | 78.3 | AT:altheim [DE]:220 (AC boundary bus, share 0.052 of the DE border by tie rating) |
| DE | 78.3 | AT:simbach [DE]:220 (AC boundary bus, share 0.052 of the DE border by tie rating) |
| DE | 235.7 | AT:buers [DE]:hv (AC boundary bus, share 0.157 of the DE border by tie rating) |
| DE | 245.1 | AT:leupolz [DE]:hv (AC boundary bus, share 0.164 of the DE border by tie rating) |
| DE | 106.5 | AT:voehringen [DE]:220 (AC boundary bus, share 0.071 of the DE border by tie rating) |
| DE | 127.8 | AT:buers [DE]:220 (AC boundary bus, share 0.085 of the DE border by tie rating) |
| DE | 370.1 | AT:silz [DE]:220 (AC boundary bus, share 0.247 of the DE border by tie rating) |
| DE | 96.1 | AT:y simbach [DE]:220 (AC boundary bus, share 0.064 of the DE border by tie rating) |
| HU | -218.4 | AT:gyoer [HU]:220 (AC boundary bus, share 0.190 of the HU border by tie rating) |
| HU | -465.8 | AT:gyoer [HU]:hv (AC boundary bus, share 0.405 of the HU border by tie rating) |
| HU | -465.8 | AT:szombathely [HU]:hv (AC boundary bus, share 0.405 of the HU border by tie rating) |
| IT | -127.0 | AT:auronzo [IT]:220 (AC boundary bus, share 1.000 of the IT border by tie rating) |
| SI | -146.3 | AT:podlog [SI]:220 (AC boundary bus, share 0.122 of the SI border by tie rating) |
| SI | -1054.7 | AT:maribor [SI]:hv (AC boundary bus, share 0.878 of the SI border by tie rating) |
| CH | 732.0 | AT:pradella [CH]:hv (AC boundary bus, share 1.000 of the CH border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 12 lumped GSUs (11844 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 44 embedded buses behind lumped supply equivalents (15389 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 0.25 MW, type C 35 MW, type D 50 MW; E-Control RfG-Schwellenwerteverordnung (RfG Schwellenwert-V) Par. 2, BGBl. II Nr. 55/2019): 174 synchronous units (9124.9 MW) of type B+ and 33 running converter units (1770.6 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 228 smaller units (2069.3 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; gas 2/16 units (2482 MW offline); oil 0/1 units (170 MW offline); biomass 51/51 units (0 MW offline); waste 5/5 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): biomass register 132.0 MW vs energy-charts 196.0 MW; 88.2 MW added, embedded, spread by population
- register gap aggregate (estimated): other register 0.0 MW vs energy-charts 22.1 MW; 27.6 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Simmering at Kledering 380kV gen bus, reactive band +/-10000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 0 reactors 0 MVAr, 1 capacitors 10 MVAr (synthetic; JAO publishes no reactive compensation): Ternitz 220kV embedded bus +10

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

- Core Static Grid Model, 9th release (2026-03): APG lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (APG for Austria)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Austria (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Austria units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- WorldPop Global 2000-2020 1 km population grid, Austria 2020 (ppp_2020_1km_Aggregated): demand shares, each cell to its nearest demand station (from the round with pop_grid) (WorldPop, University of Southampton (doi:10.5258/SOTON/WP00647)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Austria, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries AUT ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf austria-spine-380-220-r4   (flat start: vm 1, vaDeg 0; exit 0, 2.8 s)
Power flow - Austria transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (189 buses)
  converged in 8 iteration(s), mismatch 5.77E-011 pu   losses 332.830 MW / 583.421 MVAr
  voltage range 0.9792 - 1.0208 pu
  lowest voltages:
      bus 92     0.9792 pu     38.219 deg
      bus 80     0.9797 pu     32.418 deg
      bus 84     0.9801 pu     32.414 deg
      bus 93     0.9804 pu     39.707 deg
      bus 76     0.9820 pu      1.197 deg
      bus 97     0.9825 pu      3.650 deg
      bus 105    0.9827 pu     -0.699 deg
      bus 74     0.9827 pu     -0.699 deg
      bus 132    0.9833 pu     29.196 deg
      bus 83     0.9837 pu      5.448 deg
      bus 71     0.9866 pu     29.111 deg
      bus 98     0.9867 pu     29.111 deg
(warm start baked into buses.json: flat start took 8 Newton iterations)
(the build pipeline reading of the pf result) angle spread 71.686 deg; branches over 100 %: 12, over 80 %: 24; highest: jao:St.Peter - Pleinting 258:76 (St. Peter 220kV - Pleinting [DE] 220kV) 114.5 %; osm:osm umspannwerk vill - osm virtual_way/26971631:0 220 (OSM merged_way/25359793:b-220+1 c2) (Osm Umspannwerk Vill 220kV - Osm Virtual_Way/26971631:0 220kV) 110.5 %; osm:osm umspannwerk vill - osm virtual_way/26971631:0 220 (OSM merged_way/25359793:b-220+1 c1) (Osm Umspannwerk Vill 220kV - Osm Virtual_Way/26971631:0 220kV) 110.5 %; osm:osm umspannwerk thaur - osm umspannwerk vill 220 (OSM way/25359793:a-220 c2) (Osm Umspannwerk Thaur 220kV - Osm Umspannwerk Vill 220kV) 109.6 %; osm:osm umspannwerk thaur - osm umspannwerk vill 220 (OSM way/25359793:a-220 c1) (Osm Umspannwerk Thaur 220kV - Osm Umspannwerk Vill 220kV) 109.6 %
$ gridsim pf austria-spine-380-220-r4 (warm start)   (exit 0, 0.7 s)
Power flow - Austria transmission 380/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (189 buses)
  converged in 4 iteration(s), mismatch 5.77E-011 pu   losses 332.830 MW / 583.421 MVAr
  voltage range 0.9792 - 1.0208 pu
  lowest voltages:
      bus 92     0.9792 pu     38.219 deg
      bus 80     0.9797 pu     32.418 deg
      bus 84     0.9801 pu     32.414 deg
      bus 93     0.9804 pu     39.707 deg
      bus 76     0.9820 pu      1.197 deg
      bus 97     0.9825 pu      3.650 deg
      bus 105    0.9827 pu     -0.699 deg
      bus 74     0.9827 pu     -0.699 deg
      bus 132    0.9833 pu     29.196 deg
      bus 83     0.9837 pu      5.448 deg
      bus 71     0.9866 pu     29.111 deg
      bus 98     0.9867 pu     29.111 deg
$ gridsim physics-check austria-spine-380-220-r4   (exit 0, 0.7 s)
Physics-law audit  -  austria-spine-380-220-r4  (189 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.31E-011 | MW | independent dissipation 332.830357 MW (branch 332.8304 + shunt -0.0000) vs reported loss 332.830357 MW |
| 2 | Ohm's law | Holds | 1.08E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 8.70E-012 | MW | total network loss 332.830357 MW vs reported 332.830357 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.36E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 5.77E-009 | MVA | same residual as law 6, reactive component included at 141 PQ bus(es), by the bus types the solve ended with; 1 of them declared PV and solved as PQ (1 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
