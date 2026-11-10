# India transmission spine 765/400 kV (UnvalidatedAtScale)

**UnvalidatedAtScale.** This case has not been checked against official Indian study results. It is a fair approximation of the Indian transmission spine assembled from public data. Demand is low fidelity (an allocated snapshot, not metered). Impedances are typical values per voltage class, not the real conductors. Use it to learn and to explore, not to plan or operate.

## What it is

- Voltage layers: 765, 400 kV, one synchronous grid (India), largest electrical island kept.
- Built from the `model` tables.
- Buses 1657 (321 are line junctions: OSM tee points and line ends), branches 2600 (lines 2082, transformers 518), generators 2640.
- Buses by kV: 765 kV 172, 400 kV 1069, 21 kV 416.
- Snapshot: Indian evening peak, no solar. Dispatch 279422 MW; net demand in demand.json 300335 MW (includes the HVDC sending converters and any cross-border export below).
- Slack: bus 1268 (1 reference: Sasan UMPP (6x660MW)).
- Islands before selection: 62; dropped 61 islands, 120 buses (42 of them substations); 91.7% of selected buses are in the kept island.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1657 | 0 (0.0%) | 1 (0.1%) | 1652 (99.7%) | 4 (0.2%) |
| Branches | 2600 | 0 (0.0%) | 129 (5.0%) | 2470 (95.0%) | 1 (0.0%) |
| Generators | 2674 | 426 (15.9%) | 0 (0.0%) | 1460 (54.6%) | 788 (29.5%) |
| Demand points | 797 | 0 (0.0%) | 0 (0.0%) | 797 (100.0%) | 0 (0.0%) |
| Shunt buses | 1237 | 2 (0.2%) | 0 (0.0%) | 0 (0.0%) | 1235 (99.8%) |

GridSim tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic. provenance.json maps every element to its sources (GridSim gridsim-provenance/1).

## HVDC

GridSim's v1 case has no HVDC element. Each link is a load at the sending converter bus and a fixed-output generator (type hvdc, role pq, no inertia, no fault infeed) at the receiving converter bus (lossless, fixed schedule). Round 2 used a negative load at the receiving end, which GridSim's live view counted once as generation and netted out of demand.

| Link | Kind | From bus | To bus | Rating MW | Schedule MW |
|---|---|---|---|---:|---:|
| Rihand - Dadri | LCC | 1186 Rihand Converter Station 400kV | 1134 Dadri Static Inverter Plant 400kV | 1500 | 1500 |
| Talcher - Kolar | LCC | 644 HVDC Talcher Converter Station 400kV | 485 HVDC Kolar Converter station 400kV | 2500 | 2010 |
| Mundra - Mahendragarh | LCC | 352 HVDC Mundra Converter Station 400kV | 423 HVDC Mahendragarh Converter Station 400kV | 2500 | 2006 |
| Champa - Kurukshetra | LCC | 10 Champa Converter Station 765kV | 432 Kurukshetra HVDC site 400kV | 6000 | 6000 |
| Raigarh - Pugalur | LCC | 12 Raigarh Converter Station 765kV | 1081 Pugalur HVDC Station 400kV | 6000 | 6000 |
| Pugalur - North Trichur | VSC | 1081 Pugalur HVDC Station 400kV | 516 Trichur HVDC Converter Station 400kV | 2000 | 2000 |
| Biswanath Chariali - Alipurduar | LCC | 229 Biswanath Charaili substation 400kV | 1206 Alipurduar Converter Station 400kV | 3000 | 600 |
| Alipurduar - Agra | LCC | 1206 Alipurduar Converter Station 400kV | 148 Agra 765kV | 6000 | 3008 |
| Ballia - Bhiwadi | LCC | 1128 Ballia Substation 400kV | 707 Bhiwadi Substation 400kV #2 | 2500 | 1002 |
| Chandrapur - Padghe | LCC | 529 Chandrapur HVDC Converter Station 400kV | 562 Padghe HVDC Converter Station 400kV | 1500 | 1404 |
| Vindhyachal back-to-back | back-to-back | 630 Vindhyachal Pooling Station 400kV | 1653 Vindhyachal Pooling Station 400kV NR side | 500 | 250 |
| Bhadravati back-to-back | back-to-back | 524 Bhadravati B2B HVDC 400kV | 1654 Bhadravati B2B HVDC 400kV SR side | 1000 | 1000 |
| Vizag (Gazuwaka) back-to-back | back-to-back | 217 Vizag B2B HVDC Station 400kV | 1655 Vizag B2B HVDC Station 400kV ER side | 1000 | -856 |
| Pusauli (Sasaram) back-to-back | back-to-back | 254 Pusauli Back2Back HVDC 400kV | 1656 Pusauli Back2Back HVDC 400kV NR side | 500 | 500 |

## Repairs (every change made so the case solves)

- open-ended line stubs removed (a line junction with a single line, i.e. an OSM line whose far end reaches no substation): 84 line sections, 3536 route km (synthetic)
- circuit counts from the CEA ledger where OSM has fewer (unambiguous one-hop length_ok matches, no LILO, no parallel OSM line): 1 lines (Aurangabad (PG) - Padghe (PG) line 1 -> 2) (estimated)
- lines named by the CEA ledger and missing from OSM, added: North Karanpura - Gaya 400 kV D/C (North Karanpura TPP 400kV - Gaya 400kV, 98 km x2) (estimated: published length, default conductor)
- OSM loose ends of lines the CEA ledger names, joined (round 8): Babai - Bhiwani 400 kV (join) (D:12301435270:400 400kV - D:9247036553:400 400kV, 5.6 km x2) (estimated: ledger length less the OSM parts, default conductor)
- generators whose connection bus is not in this case re-attached to the nearest kept substation (400/765 kV for >= 500 MW): 2089 (estimated)
- generators dropped (no coordinates, or more than 100 km from any kept bus): 11
- generator step-up transformers: synchronous plant moved behind 416 lumped GSUs (385561 MVA in total), x 14.5 % on own rating, one generator bus per grid bus (estimated; CEA GT 14-15 %)
- slack: largest dispatched generator in the main island, Sasan UMPP (6x660MW) at Vindhyachal Pooling Station 765kV gen bus, reactive band widened to +/-23294 MVAr (synthetic)
- demand rows on buses outside this case moved to the nearest kept substation: 2549 rows, 250784 MW (estimated)
- dispatch scaled by 1.2137 to meet the demand table (271643 MW) plus 3% losses; 15 units capped at 90 % of nameplate; dispatch now 279422 MW (was 230743 MW) (estimated)
- demand scaled by 0.9978 so total demand = dispatch x (1 - 0.03) = 271039 MW (balanced snapshot; the slack takes the exact losses)
- back-to-back HVDC stations split into two converter buses: 4 (Vindhyachal back-to-back: 1 line(s), Bhadravati back-to-back: 1 line(s), Vizag (Gazuwaka) back-to-back: 1 line(s), Pusauli (Sasaram) back-to-back: 1 line(s)); the far region's AC lines no longer bypass the converter (synthetic bus, estimated)
- sourced bus splits; only where a source names the sections): Jhatikara: Bamnoli/Dwarka section (bus 321, ICT 2 x 1500 MVA, lines moved 0), Mundka section (bus 1657, ICT 2 x 1500 MVA, lines moved 1) [CTU ISTS Interim Rolling Plan 2031-32 p. 37] (derived; sectionaliser taken as open, because CTU reports ICT N-1 loading per section)
- cross-border exchanges as boundary injections (estimated; capacities and landing points checked against Druk Green / CTU, round 4): Bhutan generator 1091 MW at Alipurduar subtation 400kV; Bhutan generator 561 MW at Binaguri 400kV; Bhutan generator 185 MW at WB:w1265492410:400 400kV; Bhutan generator 33 MW at Bongaigaon PGCIL 400kV; Bangladesh load 1000 MW at Gorkana 400kV; Bangladesh load 160 MW at Surjamani Nagar 400kV
- ICTs at OSM sites with no voltage tag (layers inferred from lines only) and no CEA ledger ICT match removed as phantom couplings: 5 check; no ICT sat on a substation=transition site)
- yard ties between separately mapped yards of one station (<= 5 km, same station name, or a synthetic yard-tie repair) rated at the station's connected capacity instead of one line circuit: 35 ties, 44000 -> 140320 MVA (estimated)
- zero-dispatch converter plant (evening: solar) is a fixed zero injection, not a voltage controller: 1200 units, 201162 MVA set to role pq, Q 0 (estimated; inverters off at night)
- converter plant reactive rule, CEA Grid Connectivity Regulations Part II B2(1) (pf 0.95 lag to 0.95 lead capability) and B2(5) (stations of 500 MW and above take RLDC / SLDC reactive signals): 19 rows of 500 MW or more regulate voltage within +/-0.3287 x rated MW (23576 MW); 332 smaller rows at unity power factor (role pq, Q 0) (10805 MW dispatched) (estimated: a model row stands for a station; synthetic RE fill rows are lumps, not stations)
- fixed shunt reactors for 765 kV line charging: 70% of each line's charging, half at each end, 96783 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- fixed shunt reactors for 400 kV line charging: 50% of each line's charging, half at each end, 54890 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- line reactors named in the line table used as given on 86 lines, 13534 MVAr (not a repair: attested where the table says so); the blanket share skips those lines
- sourced STATCOMs / SVCs as zero-MW voltage-control units (role pv, published Q range): 16 devices, -7350 to +6000 MVAr (not a repair: CERC 2015 Annexure-XXXI / CTU; in-service status estimated)
- on-load tap changers on 92 ICTs (765/400 kV 92), each holding its LV bus inside the CEA 3.10.4 planning band (400 kV 0.97-1.03, 220 kV 0.92-1.09 pu); 765/400 kV +/-5.5 % in 0.5 % steps (POWERGRID 765 kV auto-transformer model specification Rev. 08 cl. 2.16), 400/220 kV +/-10 % in 1.25 % steps (CEA); estimated; 9 ICTs whose LV bus a generator / STATCOM / SVC regulates have none; GSUs have off-circuit taps (no OLTC)
- sourced bus reactors (CEA ledger / CTU text): 3 in this case, 0 switched in (0 MVAr) where the bus is above 1.02 pu before them, the rest available and out of service (not a repair)
- bus shunts placed where the snapshot still needs reactive support (12 passes of a Newton solve WITH the units' reactive limits, CEA 4.3(a) voltage limits): 1 reactors 40 MVAr, 77 capacitors 6770 MVAr (synthetic; stands in for compensation, lines, ICTs or plant the model lacks)
- converter plant with zero dispatch in this snapshot (evening: solar) feeds no fault current: 1200 units, 170988 MW (converterFaultCurrentPu 0; estimated)

## Known gaps

- HVDC Lower Sileru - Barsoor: not modelled (terminal not in the main island of this case, or no rating)
- HVDC Aarey - Kudus: not modelled (terminal not in the main island of this case, or no rating)
- Nepal exchange not modelled (monsoon export, dry-season import; direction for the evening snapshot unknown)
- Bhutan machines feed no fault current in this case (boundary injections behind 100-150 km of cross-border line; converterFaultCurrentPu 0)
- sourced compensation not in this case: Khavda 765 kV bus reactor: named substation not in this case; nearest 765 kV bus 31.9 km away (> 25 km); Khavda 420 kV bus reactor: named substation not in this case; nearest 400 kV bus 38.5 km away (> 25 km)
- Line impedances are per-km values x route length (official length where the line crosswalk matched, else OSM geometry x 1.03): 2082 of 2082 lines use CEA 2026 Annexure-II per-km values (130 with a published conductor, the rest the layer default: 765 kV Quad Bersimis, 400 kV Twin Moose, 220 kV Single Zebra). Minimum section length 0.50 km (93 sections floored, shorter yard and tee artefacts merged.
- Series compensation on 14 lines and line reactors on 86 lines, only where CERC Annexure-XXIV names them (no default compensation: CERC shows fixed series capacitors on only about one in five 400 kV lines over 250 km and on no 765 kV line); elsewhere a share of charging is cancelled at the line ends.
- Reactive compensation by origin: CERC-named line reactors -13534 MVAr; blanket line reactor share -151673 MVAr (synthetic); CEA Manual 2026 clause 5.4.2.1 load capacitors 0 MVAr (estimated rule); sourced bus reactors switched in 0 MVAr of -1290 available; 16 sourced STATCOMs / SVCs as zero-MW voltage-control units, -7350 to +6000 MVAr; auto-placed repair shunts -40 MVAr reactors and +6770 MVAr capacitors (synthetic). GridSim v1 has no switched-shunt or FACTS element: switchable devices are fixed for this snapshot.
- ICTs are inferred where one OSM site carries two voltage layers: 101 banks, 52 with a CEA ledger MVA, the rest a default bank; impedance is CEA typical. Bus sections are not modelled: every OSM substation is one bus, while CTU runs several stations (the Delhi ring among them) with bus sectionalisers open for fault-level control, so our fault levels there are an upper bound.
- Synchronous plants sit behind 416 lumped generator step-up transformers (385561 MVA, CEA GT 14-15 %, 14.5 % used), one per grid bus; inverter plant connects straight to the bus.
- Generation: WRI GPPD (2021) and CTU connectivity rows reconciled to CEA installed capacity 30.09.2026 by fuel; 29.8% of MW is synthetic 'unplaced' capacity (state-connected renewables with no public plant register), spread over the state's buses.
- Demand: loads table scenario 'evening_peak_2026_27' (CEA LGBR 2026-27 state peaks x coincidence factor), scaled to the dispatch.
- HVDC: 14 links, sending converter = load, receiving converter = fixed generator (type hvdc, role pq); schedules from CTU ISTS Rolling Plan 2030-31 HVDC table, scenario 8 Winter Evening Peak (a 2030-31 study used as a 2026-27 proxy); 4 back-to-back stations split into two converter buses.
- Cross-border exchanges are boundary injections (capacities and landing points checked against Druk Green and CTU Interim Rolling Plan 2031-32 p. 113 in round 4; output share estimated): Bhutan generator 1091 MW at Alipurduar subtation 400kV; Bhutan generator 561 MW at Binaguri 400kV; Bhutan generator 185 MW at WB:w1265492410:400 400kV; Bhutan generator 33 MW at Bongaigaon PGCIL 400kV; Bangladesh load 1000 MW at Gorkana 400kV; Bangladesh load 160 MW at Surjamani Nagar 400kV.
- Fault studies: 1200 converter units with zero output in this snapshot (evening solar) feed no fault current; every other unit feeds at its full rating whatever its dispatch (GridSim IEC 60909; synchronous X''d 0.20 pu default).
- Validation against the CTU Rolling Plan 2030-31, CEA installed capacity and LGBR 2026-27: the source record

## Sources

- OpenStreetMap power layer (India), via the Overpass API, fetched 2026-10-31 (OpenStreetMap contributors), ODbL 1.0
- Global Power Plant Database v1.3 (India rows) (World Resources Institute), CC BY 4.0
- Manual on Transmission Planning Criteria 2026, Annexure-II (Central Electricity Authority), no licence stated
- Monthly transmission completion reports (lines, substations, HVDC) (Central Electricity Authority), no licence stated
- Load Generation Balance Report / state peak demand (Central Electricity Authority), no licence stated
- Line loadability annexure (Annexure-XXIV) (Central Electricity Regulatory Commission), no licence stated
- ISTS Rolling Plan and connectivity lists (Central Transmission Utility of India Ltd), no licence stated
- List of SVC/STATCOMs planned by POWERGRID (2015 report, Annexure-XXXI) (Central Electricity Regulatory Commission), no licence stated
- Plant status records read 2026-11-01: KPCL Yelahanka CCPP 370.05 MW (udayavani.com, Sep 2024; BHEL 2016 release); CEA Yelahanka diesel retirement letter; Tata Power Trombay 930 MW (Free Press Journal, 7 Feb 2025; Wikipedia Trombay Thermal Power Station) (various (press, CEA, Wikipedia)), no licence stated (facts only)
- Model assembly steps: bus placement, ICT inference, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries India ADM1 (DataMeet), CC BY 2.5 IN: state assignment and state shapes in geography.json.
- Natural Earth 1:10m admin-0, India point of view, public domain: land outline in geography.json.

Licence: ODbL 1.0, (c) OpenStreetMap contributors. See ATTRIBUTION.txt.

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Island repairs in the model tables

Applied before this case was cut from the tables; each repair is a labelled row in the model tables (evidence_detail field 'repair'). Repairs whose buses are outside this case's layers are not listed.

| Repair | Evidence | Count in this case | Island buses joined |
|---|---|---:|---:|
| (a) 765 kV free line end joined to the nearest 765 kV substation (<= 10 km) | estimated | 2 | 4 |
| (b) separately mapped yard of one station tied to its partner (<= 1.5 km) | synthetic | 1 | 1 |
| (c) 400/220 kV ICT to a 220 kV yard with no ICT (400 kV yard <= 2 km) | estimated | 0 | 0 |
| (d) plant switchyard line end joined to the nearest same-kV substation (<= 3 km) | estimated | 0 | 0 |

| Repair | Island bus | Target bus | km |
|---|---|---|---:|
| (a) | D:14306510325:765 | RJ:ajmer:765 | 3.53 |
| (a) | D:14276624198:765 | GJ:halvad:765 | 4.56 |
| (b) | PB:w428212210:400 | PB:rajpura tpp:400 | 0.18 |

## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf india-spine-765-400-r8   (flat start: vm 1, vaDeg 0; exit 0, 1.5 s)
Power flow - India transmission spine 765/400 kV (UnvalidatedAtScale) (1657 buses)
  converged in 10 iteration(s), mismatch 3.29E-011 pu   losses 4480.746 MW / -33812.394 MVAr
  voltage range 0.9495 - 1.0491 pu
  lowest voltages:
      bus 210    0.9495 pu    -17.452 deg
      bus 1194   0.9498 pu    -38.163 deg
      bus 439    0.9501 pu    -34.178 deg
      bus 336    0.9502 pu    -26.583 deg
      bus 544    0.9504 pu    -20.774 deg
      bus 172    0.9504 pu     -0.026 deg
      bus 481    0.9506 pu    -17.270 deg
      bus 671    0.9507 pu    -39.380 deg
      bus 670    0.9508 pu    -35.021 deg
      bus 332    0.9508 pu    -28.101 deg
      bus 355    0.9512 pu    -23.643 deg
      bus 1018   0.9514 pu    -14.141 deg
(warm start baked into buses.json from that solve: flat start took 10 Newton iterations)
$ gridsim pf india-spine-765-400-r8 (warm start)   (exit 0, 1.2 s)
Power flow - India transmission spine 765/400 kV (UnvalidatedAtScale) (1657 buses)
  converged in 8 iteration(s), mismatch 3.30E-011 pu   losses 4480.746 MW / -33812.394 MVAr
  voltage range 0.9495 - 1.0491 pu
  lowest voltages:
      bus 210    0.9495 pu    -17.452 deg
      bus 1194   0.9498 pu    -38.163 deg
      bus 439    0.9501 pu    -34.178 deg
      bus 336    0.9502 pu    -26.583 deg
      bus 544    0.9504 pu    -20.774 deg
      bus 172    0.9504 pu     -0.026 deg
      bus 481    0.9506 pu    -17.270 deg
      bus 671    0.9507 pu    -39.380 deg
      bus 670    0.9508 pu    -35.021 deg
      bus 332    0.9508 pu    -28.101 deg
      bus 355    0.9512 pu    -23.643 deg
      bus 1018   0.9514 pu    -14.141 deg
$ gridsim physics-check india-spine-765-400-r8 (warm start)   (exit 0, 1.3 s)
Physics-law audit  -  india-spine-765-400-r8  (1657 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 5.60E-010 | MW | independent dissipation 4480.745634 MW (branch 4480.7456 + shunt 0.0000) vs reported loss 4480.745634 MW |
| 2 | Ohm's law | Holds | 3.64E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 8.99E-010 | MW | total network loss 4480.745634 MW vs reported 4480.745634 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.05E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 5.68E-009 | MVA | same residual as law 6, reactive component included at 1221 PQ bus(es), by the bus types the solve ended with; 18 of them declared PV and solved as PQ (18 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## Inference round india-spine-765-400-r10 (base india-spine-765-400-r8, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 4 (6 circuits / units, 138.57 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), with no new overload, no existing overload made worse by more than 1 point, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 65 sites, 6160 MVAr capacitive / 40 MVAr inductive, replacing the generic repair (78 shunts, 6770 / 40 MVAr).
- Taps: 1 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- Units at a reactive limit: base round 18; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 10 | 13 |
| iterations_warm | 8 | 11 |
| loss_mw | 4480.746 | 4390.792 |
| vmin_pu | 0.949 | 0.950 |
| vmax_pu | 1.049 | 1.049 |
| angle_spread_deg | 78.193 | 78.962 |
| over_100 | 18 | 13 |
| over_120 | 14 | 10 |
| over_140 | 6 | 5 |
| auto_cap_mvar | 6770.000 | 0 |
| auto_reactor_mvar | 40.000 | 0 |
| inferred_comp_mvar_abs | 0.000 | 6200.000 |
| units_held_at_q_limit | 18 | 16 |
| cpf_lambda | 1.059 | 1.059 |
| physics_pass | True | True |

Worst after: 180.5 % osm:400:w340479216:n3477127797 (Neyveli Thermal Station II 400kV - T:7029234666:400 400kV); 151.3 % osm:400:w196377929:n2067200078 (Singrauli STPS 400kV - Anpara TPS 400kV); 145.0 % osm:400:w513976170:n1435568494 (T:5022547393:400 400kV - 220 KV Substation Sector 32 400kV)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 112.9 % osm:400:w421884733:n4216294051 (Kayathar 400kV - Kanarpatti 400kV)
- 101.6 % osm:400:w166046200:n2199782592 (Bihar Sharif (PGCIL) 400kV - Koderma Thermal Power Station 400kV)
- 100.6 % osm:400:w206009231:n1777559899 (Maithon PGCIL 400kV - Parulia 400kV)

Inferred feeds:

- inferred feed 1: 400 kV line x2 PG_Shikrapur 765 KV _PUNE GIS 400kV - 400 KV Chakan MSETCL 400kV 34.15 km; demanded by osm:400:w294201887:n2977616853 (400 KV Chakan MSETCL 400kV - Talegaon PG 400/220 KV ss 400kV) at 159.4 % (N-0 snapshot); after 50.4 %
- inferred feed 2: transformer unit x2 Raigarh Converter Station 765kV / Raigarh Converter Station 400kV; demanded by ict:w311954709:765/400 at 138.8 % (N-0 snapshot); after 83.8 %
- inferred feed 3: transformer unit x1 Gaya 765kV / Gaya 400kV; demanded by ict:w209806624:765/400 at 134.5 % (N-0 snapshot); after 85.8 %
- inferred feed 4: 400 kV line x1 Thiruvalam 400kV - Sungavarchatram 400kV 70.27 km; demanded by osm:400:w245726111:n340440793 (Sungavarchatram 400kV - Sriperumbudur 400kV) at 123.0 % (N-0 snapshot); after 96.5 %

Inferred compensation (largest 15; full list in inferred_elements.json):

- inferred compensation 1: +400 MVAr at Areekode 400kV
- inferred compensation 2: +340 MVAr at 220 KV Substation Sector 32 400kV
- inferred compensation 3: +320 MVAr at Virudhunagar 765kV
- inferred compensation 4: +300 MVAr at Karjat 400kV
- inferred compensation 5: +250 MVAr at Dhanansu 400kV
- inferred compensation 6: +230 MVAr at New Jeerat 765 kV Substation 765kV
- inferred compensation 7: +200 MVAr at KL:w1448459844:400 400kV
- inferred compensation 8: +180 MVAr at Alipurduar Converter Station 400kV
- inferred compensation 9: +180 MVAr at Alipurduar subtation 400kV
- inferred compensation 10: +180 MVAr at WB:w1265492410:400 400kV
- inferred compensation 11: +180 MVAr at WB:w1265492411:400 400kV
- inferred compensation 12: +160 MVAr at Mapusa Sub Station 400kV
- inferred compensation 13: +140 MVAr at Talaricheruvu 400kV
- inferred compensation 14: +140 MVAr at Panchkula 400kV
- inferred compensation 15: +130 MVAr at Lonikand S/S 400kV
