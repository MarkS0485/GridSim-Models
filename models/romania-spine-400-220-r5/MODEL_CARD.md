# MODEL CARD: Romania transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING JAO's written consent: this model uses JAO Static Grid Model data and is NOT cleared for public redistribution until that consent is held (see LICENSING.md). General-purpose fidelity, never planning grade.**

**PRIVATE - DO NOT SHARE OR PUBLISH. Built from the JAO Core Static Grid Model, which JAO licenses for research and internal use with attribution only; making it (or a database derived from it) available to third parties needs JAO's prior written authorisation (contact@jao.eu). This case stays in the build pipeline out/ and never goes to GridSim's public repository.**

**UnvalidatedAtScale.** Not checked against official Romania study results. A solvable rough map of the Romania 220 kV-and-above transmission grid for one winter-evening snapshot: real TSO impedances and ratings (JAO, TEL) where JAO lists the element, OSM corridors with median JAO parameters where it does not, register-based generation, population-allocated demand. Use it to learn, compare and explore, not to plan or operate.

Round: r5 (round 1 build-first; later rounds listed under Round history).

## What it is

- Snapshot: 2025-11-19 16:30 UTC (17:30 CET), common Core-region winter-evening snapshot of the JAO batch (energy-charts load 8213.0 MW; interval {'public_power_interval_utc': '2025-11-19T16:30:00+00:00', 'cbpf_interval_utc': '2025-11-19T16:30:00+00:00', 'resolution_s': 900}).
- Buses 260 (9 cross-border boundary buses, 103 generator / embedded buses), branches 413 (lines 282, transformers 131), generators 693.
- Buses by kV: 400 kV 62, 220 kV 95, 110 kV 92, 21 kV 11.
- Dispatch 6285.0 MW (Romania plant) + boundary imports 2451.0 MW; demand 8578.4 MW (incl. boundary exports 857.0 MW and storage charging).
- Slack: 1 reference: Turceni.
- Islands before selection 1; buses dropped 0.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 260 | 0 (0.0%) | 0 (0.0%) | 148 (56.9%) | 112 (43.1%) |
| Branches | 413 | 151 (36.6%) | 1 (0.2%) | 261 (63.2%) | 0 (0.0%) |
| Generators | 693 | 0 (0.0%) | 0 (0.0%) | 693 (100.0%) | 0 (0.0%) |
| Demand points | 92 | 0 (0.0%) | 0 (0.0%) | 92 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 20 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 20 (100.0%) |

Buses are 'estimated' because their POSITION is inferred (OSM / JAO map). Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- JAO 9th release, TEL: 138 internal line rows (by class {'220': 87, 'hv': 51}), 11 tie-line rows used, 22 JAO transformers placed.
- Positions: {'osm_whole_word': 102, 'jao_map': 6, 'pypsa_osm': 39, 'neighbour_mean': 1, 'boundary': 9} (OSM whole-word name match first, JAO map polyline ends second; JAO map points moved for line-length consistency: ['ratesti']).
- PyPSA-Eur OSM gap lines (estimated): 132 circuits, 51 OSM-only stations, 21 chain duplicates of JAO lines skipped; per km (HV) R 0.0354 ohm, X 0.3341 ohm, B 3.335 uS, Imax 1920 A (medians of 43 JAO lines); 220 kV R 0.0712, X 0.4203, B 2.709, Imax 960 A.
- Synthetic couplings (median JAO unit {'mva': 399.8, 'x_pct_own': 11.79, 'x_over_r': 90.4, 'how': 'median of 22 JAO Romania 400(380)/220 kV units'}): ['arad', 'd. mostistea', 'osm brazi vest', 'osm sibiu sud', 'suceava', 'urechesti']; near-site [].
- JAO transformers not modelled: ['PST Arad 400/220 3: phase shifter 400/231 kV, not modelled', 'PST Urechesti 400/220 1: phase shifter 400/231 kV, not modelled', 'TR Bucuresti Sud 400/110 3: 400/121 kV (not an HV/220 kV unit; no 110 kV layer)', 'TR Bucuresti Sud 400/110 4: nan/nan kV (not an HV/220 kV unit; no 110 kV layer)'].
- Tie rows dropped or re-read: [].
- Islands in the topology: 1 (sizes [157]).
- Shape check (crow-fly vs published length): 10 outliers [{'line': 'Sardanesti - Urechesti', 'crow_km': 23.7, 'len_km': 65.9}, {'line': 'Calea Aradului - Sacalaz', 'crow_km': 6.7, 'len_km': 47.6}, {'line': 'Bucuresti Sud - Domnesti', 'crow_km': 14.9, 'len_km': 44.0}, {'line': 'Nadab - Oradea Sud', 'crow_km': 69.7, 'len_km': 33.6}, {'line': 'Brazi Vest - Teleajen', 'crow_km': 12.9, 'len_km': 32.8}, {'line': 'Bucuresti Sud - Fundeni c1', 'crow_km': 6.1, 'len_km': 25.0}, {'line': 'Bucuresti Sud - Fundeni c2', 'crow_km': 6.1, 'len_km': 25.0}, {'line': 'Sacalaz - Timisoara', 'crow_km': 9.7, 'len_km': 25.0}, {'line': 'Slatina - Gradiste', 'crow_km': 4.5, 'len_km': 23.3}, {'line': 'Craiova Nord - Studina', 'crow_km': 93.5, 'len_km': 67.0}].

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 843.9 | 69.0 |
| biomass | 76.9 | 66.0 |
| coal | 150.0 | 65.0 |
| gas | 3924.8 | 1675.0 |
| hydro_res | 3529.0 | 1087.0 |
| hydro_ror | 4151.6 | 1045.0 |
| interconnector | 2451.0 | 2451.0 |
| lignite | 4760.0 | 932.0 |
| nuclear | 1411.0 | 1239.0 |
| oil | 210.0 | 0.0 |
| solar | 4239.0 | 0.0 |
| wind_onshore | 5723.2 | 107.0 |

## Boundary injections (MW, + import)

| Country | MW | Where |
|---|---:|---|
| BG | 221.7 | RO:varna [BG]:hv (AC boundary bus, share 0.255 of the BG border by tie rating) |
| BG | 221.7 | RO:dobrudja [BG]:hv (AC boundary bus, share 0.255 of the BG border by tie rating) |
| BG | 425.6 | RO:kozlodui [BG]:hv (AC boundary bus, share 0.490 of the BG border by tie rating) |
| HU | 311.5 | RO:sandorfalva [HU]:hv (AC boundary bus, share 0.490 of the HU border by tie rating) |
| HU | 324.5 | RO:bekescsaba [HU]:hv (AC boundary bus, share 0.510 of the HU border by tie rating) |
| MD | -857.0 | RO:vulcanesti [MD]:hv (AC boundary bus, share 1.000 of the MD border by tie rating) |
| RS | 171.6 | RO:djerdap [RS]:hv (AC boundary bus, share 0.324 of the RS border by tie rating) |
| RS | 357.4 | RO:pancevo [RS]:hv (AC boundary bus, share 0.676 of the RS border by tie rating) |
| UA | 417.0 | RO:mukacevo [UA]:hv (AC boundary bus, share 1.000 of the UA border by tie rating) |

## Repairs (every change made so the case solves)

- synchronous plant connected at extra-high voltage moved behind 11 lumped GSUs (14017 MVA, x 14.5 % own rating, X/R 40; estimated)
- embedded plant (units below 300 MW and the register-gap aggregates) on 92 embedded buses behind lumped supply equivalents (18009 MVA, x 20 % own rating; estimated), pq with Q = 0
- RfG voltage control (Regulation (EU) 2016/631 Art. 5, NATIONAL thresholds: type B 1 MW, type C 50 MW, type D 75 MW; national values not found (Transelectrica RfG decision gives only the EU caps 1 / 50 / 75 MW): EU Table 1 Continental Europe upper limits [VERIFY]): 118 synchronous units (4454.7 MW) of type B+ and 34 running converter units (5890.2 MW) of type C+ below the 300 MW EHV placement size (embedded units) now regulate voltage; 415 smaller units (4915.9 MW) stay pq at unity pf; register-gap aggregates stay pq
- unit commitment: per thermal fuel, register units committed largest first until committed capacity x 0.8 covers the energy-charts dispatch; coal 1/1 units (0 MW offline); lignite 1/5 units (2450 MW offline); gas 3/15 units (1762 MW offline); oil 0/2 units (210 MW offline); biomass 92/92 units (0 MW offline) (offline: 0 MW, pq, no inertia, no fault infeed)
- register gap aggregate (estimated): biomass register 30.0 MW vs energy-charts 66.0 MW; 46.9 MW added, embedded, spread by population
- slack: largest dispatched EHV synchronous unit Turceni at Tantareni 400kV gen bus, reactive band +/-13588 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (4 passes of a Newton solve without reactive limits): 19 reactors 620 MVAr, 0 capacitors 0 MVAr (synthetic; JAO publishes no reactive compensation): Pancevo [RS] 400kV -60, Resita 400kV -50, Sandorfalva [HU] 400kV -50, Osm Virtual_Way/852703146:1 400kV -50, Bekescsaba [HU] 400kV -50, Arad 400kV -50, Nadab 400kV -50, Oradea Sud 400kV embedded bus -30, Oradea Sud 400kV -30, Mukacevo [UA] 400kV -30, Mintia 400kV -30, Rosiori 400kV -30, Domnesti 400kV embedded bus -20, Osm Sibiu Sud 400kV -20, Arefu 400kV -20, Nadab 400kV embedded bus -20, Timisoara 220kV embedded bus -10, Osm Virtual_Way/312427087:0 220kV -10, Osm Virtual_Way/209262452:1 220kV -10, Resita 220kV embedded bus +0

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

- Core Static Grid Model, 9th release (2026-03): TEL lines, tie-lines, transformers (R, X, B, Imax) and its publication map (JAO S.A. on behalf of the Core TSOs (TEL for Romania)), JAO General Terms and Conditions: research / internal use with attribution; no redistribution without JAO's prior written consent
- OpenStreetMap substations of 110 kV and more in Romania (Overpass API, 2026-11-01): names and positions (OpenStreetMap contributors), ODbL 1.0
- PyPSA-Eur prebuilt OSM network v0.7: 220 kV-and-above lines and substations missing from JAO (PyPSA-Eur / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching powerplants.csv (Romania units: capacity, fuel, location) (PyPSA powerplantmatching (merging ENTSO-E, GEM, OPSD, JRC, OSM and others)), CC BY 4.0
- GHSL GHS-POP R2023A, epoch 2020, 30 arc-second tiles over Romania (demand shares where the WorldPop raster is defective: Romania) (European Commission, Joint Research Centre (Schiavina et al. 2023, doi:10.2905/2FF68A52-5B5B-4A22-8F40-C41DA8332CFE)), CC BY 4.0
- Public net generation by type, load and cross-border physical flows, Romania, 2025-11-19 16:30 UTC (Fraunhofer ISE, energy-charts.info (ENTSO-E based)), CC BY 4.0
- Model assembly steps: name resolution, coordinates, added corridors, couplings, GSUs, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries ROU ADM1 (gbOpen): region assignment and region shapes in geography.json.
- Natural Earth 1:10m admin-0, public domain: outline in geography.json.

Licence: PRIVATE (JAO terms). See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf romania-spine-400-220-r5   (flat start: vm 1, vaDeg 0; exit 0, 0.5 s)
Power flow - Romania transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (260 buses)
  converged in 7 iteration(s), mismatch 8.37E-009 pu   losses 152.206 MW / -2494.880 MVAr
  voltage range 0.9588 - 1.0478 pu
  lowest voltages:
      bus 81     0.9588 pu    -39.785 deg
      bus 144    0.9590 pu    -39.251 deg
      bus 174    0.9657 pu     -1.643 deg
      bus 99     0.9740 pu    -37.370 deg
      bus 56     0.9776 pu    -32.664 deg
      bus 87     0.9918 pu    -21.775 deg
      bus 48     0.9926 pu      7.330 deg
      bus 44     0.9935 pu      8.582 deg
      bus 157    0.9946 pu    -12.067 deg
      bus 260    0.9946 pu    -12.044 deg
      bus 136    0.9965 pu    -13.368 deg
      bus 239    0.9969 pu    -12.880 deg
(warm start baked into buses.json: flat start took 7 Newton iterations)
(the build pipeline reading of the pf result) angle spread 48.368 deg; branches over 100 %: 0, over 80 %: 4; highest: synth:coupling:suceava~suceava (Suceava 400kV - Suceava 220kV) 93.5 %; jao:30TRESI400AT3--U:20 (Resita 400kV - Resita 220kV) 91.1 %; jao:Isaccea - Vulcanesti:145 (Isaccea 400kV - Vulcanesti [MD] 400kV) 86.2 %; jao:30T-ROSI400AT--1:14 (Rosiori 400kV - Rosiori 220kV) 80.8 %; gsu:RO:cernavoda:hv (Cernavoda 400kV gen bus - Cernavoda 400kV) 76.9 %
$ gridsim pf romania-spine-400-220-r5 (warm start)   (exit 0, 0.5 s)
Power flow - Romania transmission 400/220 kV winter evening 2025-11-19 (UnvalidatedAtScale) (260 buses)
  converged in 4 iteration(s), mismatch 8.37E-009 pu   losses 152.206 MW / -2494.880 MVAr
  voltage range 0.9588 - 1.0478 pu
  lowest voltages:
      bus 81     0.9588 pu    -39.785 deg
      bus 144    0.9590 pu    -39.251 deg
      bus 174    0.9657 pu     -1.643 deg
      bus 99     0.9740 pu    -37.370 deg
      bus 56     0.9776 pu    -32.664 deg
      bus 87     0.9918 pu    -21.775 deg
      bus 48     0.9926 pu      7.330 deg
      bus 44     0.9935 pu      8.582 deg
      bus 157    0.9946 pu    -12.067 deg
      bus 260    0.9946 pu    -12.044 deg
      bus 136    0.9965 pu    -13.368 deg
      bus 239    0.9969 pu    -12.880 deg
$ gridsim physics-check romania-spine-400-220-r5   (exit 0, 0.4 s)
Physics-law audit  -  romania-spine-400-220-r5  (260 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.48E-011 | MW | independent dissipation 152.205509 MW (branch 152.2055 + shunt -0.0000) vs reported loss 152.205509 MW |
| 2 | Ohm's law | Holds | 2.24E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 2.17E-011 | MW | total network loss 152.205509 MW vs reported 152.205509 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.45E-007 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 8.37E-007 | MVA | same residual as law 6, reactive component included at 207 PQ bus(es), by the bus types the solve ended with; 1 of them declared PV and solved as PQ (1 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
