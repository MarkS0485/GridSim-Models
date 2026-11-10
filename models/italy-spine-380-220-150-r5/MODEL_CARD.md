# Italy Italian mainland and Sicily 380/220/150/132 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official Italian study results. A solvable rough map of the Italian mainland and Sicily 380/220/150/132 kV transmission grid (Messina link synchronous) for one summer peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur), register-based generation (powerplantmatching), Terna's published peak, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Round: r5. System: mainland.
- Snapshot: 2026-06-29 12:00-13:00 UTC (14:00-15:00 CEST), Terna June 2026 peak; Terna national demand 57434 MW.
- Buses 5006 (21 boundary points on Italian buses), branches 6523 (lines 5819, transformers 704), generators 7128.
- Buses by kV: 380 kV 240, 220 kV 332, 150 kV 1379, 132 kV 2666, 20 kV 389.
- Dispatch 49981.1 MW (plant in this system) + boundary imports 6222.0 MW; demand 55341.6 MW (incl. boundary exports 275.7 MW).
- Slack: 1 reference: Montalto Alessandro Volta.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 5006 | 3199 (63.9%) | 0 (0.0%) | 1418 (28.3%) | 389 (7.8%) |
| Branches | 6523 | 0 (0.0%) | 734 (11.3%) | 5783 (88.7%) | 6 (0.1%) |
| Generators | 7128 | 1027 (14.4%) | 0 (0.0%) | 6101 (85.6%) | 0 (0.0%) |
| Demand points | 3044 | 0 (0.0%) | 0 (0.0%) | 3044 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 197 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 197 (100.0%) |

Buses are 'attested' when OSM names the substation; lines 'derived' (OSM length x PyPSA standard type), cables 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, Italian rows: 590 AC buses, 802 internal lines (214 underground / submarine, given cable parameters), 66 transformers; 3324 buses named from OSM.
- Systems: {'mainland': 4617, 'sardinia': 151} (mainland includes Sicily through the Messina 380 kV link); islands 2 [4617, 151].
- Boundary points (cut ties and HVDC terminals): Austria ac x2; France ac x4; France hvdc x3; Greece hvdc x1; Italy hvdc x2; Malta ac x1; Montenegro hvdc x1; Slovenia ac x2; Switzerland ac x8.
- HV layer (150/132 kV): {'osm_line_ways': 11610, 'ways_without_hv_class': 0, 'segments': 11610, 'routes': 10775, 'routes_kept': 5207, 'stub_routes_pruned': 378, 'ends_snapped_within_km': 0.5, 'ends_snapped': 264, 'hv_buses': 4178, 'hv_buses_by_kv': {'132': 2666, '150': 1512}, 'tee_junctions': 1022, 'couplings': 260, 'uncoupled_components_left_out': {'buses': 127, 'routes': 96, 'km': 354.5}, 'route_km_kept': 39214.6, 'one_coupling_per_site': True}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 1047.4 | 0.0 |
| biomass | 697.7 | 694.4 |
| gas | 51461.4 | 22652.7 |
| geothermal | 834.0 | 544.3 |
| hydro_lake | 6361.4 | 296.5 |
| hydro_ror | 7609.2 | 2732.8 |
| interconnector | 6222.0 | 6222.0 |
| oil | 868.0 | 172.8 |
| pumped_storage | 8484.2 | 0.0 |
| solar | 42264.0 | 21008.9 |
| wind_offshore | 30.0 | 5.0 |
| wind_onshore | 9157.5 | 1873.7 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Austria | 175.5 | way/98787157-220 (ac merged_way/1004273735-220+1, share 0.50 by rating) |
| Austria | 175.5 | way/159821869-220 (ac relation/3948362-220, share 0.50 by rating) |
| France | 635.2 | virtual_relation/6359579:b:1-400 (ac merged_relation/6359579:a-400+1, share 0.25 by rating) |
| France | 178.6 | virtual_way/333332920:1-225 (ac merged_way/333332920-225+1, share 0.07 by rating) |
| France | 635.2 | virtual_relation/6359580:a:1-400 (ac relation/6359580:a-400, share 0.25 by rating) |
| France | 635.2 | virtual_relation/6359580:a:1-400 (ac relation/6359581:a-400, share 0.25 by rating) |
| France | 426.4 | way/98902899-380 (hvdc Piemonte-Savoie HVDC (not in PyPSA links), share 0.17 by rating) |
| Greece | 254.0 | way/103386958-380 (hvdc relation/8185664-400-DC, share 1.00 by rating) |
| Malta | -198.5 | way/57380344-220 (ac Malta-Sicily 220 kV cable (not in PyPSA), share 1.00 by rating) |
| Montenegro | 462.0 | relation/13844905-380 (hvdc relation/8185767-500-DC, share 1.00 by rating) |
| Slovenia | 499.2 | virtual_relation/13676255:0-400 (ac relation/13676255-400, share 0.78 by rating) |
| Slovenia | 137.3 | way/61038773-220 (ac way/375685106-220, share 0.22 by rating) |
| Switzerland | 326.1 | way/72570378-380 (ac merged_relation/5609696:a-380+3, share 0.16 by rating) |
| Switzerland | 94.4 | way/104114052-220 (ac merged_way/332890452-220+3, share 0.05 by rating) |
| Switzerland | 326.1 | virtual_way/581583151:1-380 (ac merged_way/339184905-380+1, share 0.16 by rating) |
| Switzerland | 652.2 | way/72466334-380 (ac relation/2798852-380, share 0.32 by rating) |
| Switzerland | 94.4 | way/103127417-220 (ac relation/5552941-220, share 0.05 by rating) |
| Switzerland | 94.4 | way/102675884-220 (ac relation/5552945-220, share 0.05 by rating) |
| Switzerland | 326.1 | way/42206116-380 (ac relation/5563323-380, share 0.16 by rating) |
| Switzerland | 94.4 | way/105462289-220 (ac way/104450944-220, share 0.05 by rating) |
| SAPEI (from Sardinia) | -59.4 | way/339704025-380 (hvdc relation/8185711-500-DC: Sardinian net export share) |
| SACOI (from Sardinia) | -17.8 | way/100253768-380 (hvdc relation/9982798-200-DC: Sardinian net export share) |

## Repairs (every change made so the case solves)

- synchronous plant moved behind 389 lumped GSUs (85869 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 covers the fuel's snapshot value; gas 23/109 units; coal 1/2 units; oil 1/11 units; biomass 16/16 units; hydro_lake 2/142 units. Offline units in the case: 245 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Montalto Alessandro Volta at Montalto centrale 380kV gen bus, reactive band +/-20271 MVAr (synthetic)
- reactive repair staged by load scaling: shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage from the previous stage's shunts (estimated)
- repair shunts moved from generator terminal buses to their grid bus: 1 (10 MVAr; estimated)
- reactive repair stopped early at some stage(s): pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached; pass limit 60 reached
- bus shunts placed where the snapshot needs reactive support (435 passes of a Newton solve without reactive limits): 42 reactors 1450 MVAr, 149 capacitors 6500 MVAr (synthetic; no open source lists Terna's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 197 buses, 6500 MVAr capacitors and 1450 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists Terna's compensation; synthetic)
- slack: Montalto Alessandro Volta takes the balance (losses and the losses-allowance error); synthetic
- Radial relief MW moved by round (mainland): r1 4,764 MW (380/220 kV only), r2 9,279 MW (HV layer, demand on the 3 nearest buses per province), this round 0.0 MW. r1 and r2 tagged the moved demand 'estimated'; from r3 it is 'synthetic'.: this India routine (_relieve_radial_chains, copied into a build step) should not be used; its removal is an open item.

Assumed (typical values or documented rules, not fitted; tagged estimated with [VERIFY]):

- losses allowance 1.5 % of Terna's demand (the slack takes the rest)
- 380/220 kV transformers 2 x 400 MVA, x 12 %; EHV/HV couplings 2 x 250 MVA, x 12 % (Terna standard unit sizes)
- HV lines single ACSR 585 mm2: R 0.060, X 0.400 ohm/km, C 9 nF/km, 870 A; cables X 0.12-0.13 ohm/km, C 0.20-0.25 uF/km
- GSU x 14.5 % own rating, X/R 40; generator Q range -0.30 to +0.62 x MW; load power factor 0.97
- unit commitment largest first to 0.8 loading; mainland coal off (closures by 2025) [VERIFY]
- embedded PV = Terna installed 43,846 MW (31 Jan 2026, press summary) less ppm utility PV, by population
- plants >= 169 MW on 380/220 kV (one 132 kV circuit at 870 A, 0.85 pf); < 100 MW on 150/132 kV

What the radial-chain relief does and why: where demand sits at the end of a radial chain (buses fed by one branch only), the builder adds up the demand behind each feeding branch and, if it exceeds 60 % of that branch's rating, scales that demand down and moves the removed MW to the bus where the chain meets the meshed grid. It exists only so the snapshot solves without hopeless overloads on antennas whose real parallel circuits, open points or local generation are missing from the open data. No source says the demand is elsewhere, so every changed demand point is tagged synthetic and the MW moved is the size of the open problem.


## Known gaps

- No TSO impedances: line R/X/B come from PyPSA-Eur's two standard overhead types (380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; Terna's real conductors (e.g. 3 x 585 mm2 at 380 kV) differ; cables use typical XLPE values. Terna publishes no grid model; the JAO Core SGM holds only foreign TSOs' halves of the AT / SI / FR ties (no Terna rows), and no Italy North static grid model is published.
- Transformers: 2 x 400 MVA, x 12 % at every 380/220 kV site OSM marks; real unit counts unknown.
- 150/132 kV from OSM only (no impedances published): standard conductor per km, couplings estimated.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (energy-charts cbpf per border, split by tie rating): no foreign network and no fault infeed from abroad. SAPEI / SACOI carry Sardinia's estimated net balance.
- Demand by province population (no Terna regional load map at the peak hour); embedded PV by population, though Italian PV is skewed to the south and to Lombardy / Veneto / Emilia [VERIFY].
- Unit commitment by size, not Terna's real schedule (MSD / MGP not used).

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): Italian buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- OpenStreetMap: names of the substations behind the PyPSA buses; 120-160 kV lines and substations (Overpass API, 2026-10-31) (OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31), Italian rows (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- energy-charts public net generation by type and cross-border physical flows, Italy, 2026-06-29 12:00-13:00 UTC (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
- Rapporto Mensile sul Sistema Elettrico, Giugno 2026: peak 57,434 MW on 29 June 2026 14:00-15:00, thermal 23,907 MW at the peak (Terna S.p.A.), Terna publication, facts reused with attribution
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- openpolis geojson-italy regions (ISTAT), CC BY 4.0, and Natural Earth (public domain): geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf italy-spine-380-220-150-r5   (flat start: vm 1, vaDeg 0; exit 0, 3.7 s)
Power flow - Italy Italian mainland and Sicily 380/220/150/132 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale) (5006 buses)
  converged in 16 iteration(s), mismatch 5.87E-011 pu   losses 734.181 MW / -10788.388 MVAr
  voltage range 0.9529 - 1.1206 pu
  lowest voltages:
      bus 3079   0.9529 pu      0.506 deg
      bus 4490   0.9529 pu     -3.791 deg
      bus 3582   0.9530 pu     -4.311 deg
      bus 3495   0.9536 pu     -1.353 deg
      bus 3833   0.9539 pu     -3.296 deg
      bus 4218   0.9542 pu      0.671 deg
      bus 3479   0.9549 pu     -1.040 deg
      bus 2738   0.9553 pu     -0.986 deg
      bus 4524   0.9554 pu     -0.940 deg
      bus 2734   0.9554 pu     -0.940 deg
      bus 4801   0.9554 pu     -0.940 deg
      bus 2735   0.9554 pu     -0.939 deg
(warm start baked into buses.json from that solve: flat start took 16 Newton iterations)
$ gridsim pf italy-spine-380-220-150-r5 (warm start)   (exit 0, 1.6 s)
Power flow - Italy Italian mainland and Sicily 380/220/150/132 kV transmission grid summer peak 2026-06-29 (UnvalidatedAtScale) (5006 buses)
  converged in 10 iteration(s), mismatch 3.95E-011 pu   losses 734.181 MW / -10788.388 MVAr
  voltage range 0.9529 - 1.1206 pu
  lowest voltages:
      bus 3079   0.9529 pu      0.506 deg
      bus 4490   0.9529 pu     -3.791 deg
      bus 3582   0.9530 pu     -4.311 deg
      bus 3495   0.9536 pu     -1.353 deg
      bus 3833   0.9539 pu     -3.296 deg
      bus 4218   0.9542 pu      0.671 deg
      bus 3479   0.9549 pu     -1.040 deg
      bus 2738   0.9553 pu     -0.986 deg
      bus 4524   0.9554 pu     -0.940 deg
      bus 2734   0.9554 pu     -0.940 deg
      bus 4801   0.9554 pu     -0.940 deg
      bus 2735   0.9554 pu     -0.939 deg
$ gridsim physics-check italy-spine-380-220-150-r5   (exit 0, 1.8 s)
Physics-law audit  -  italy-spine-380-220-150-r5  (5006 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 6.66E-010 | MW | independent dissipation 734.180730 MW (branch 734.1807 + shunt 0.0000) vs reported loss 734.180730 MW |
| 2 | Ohm's law | Holds | 3.26E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 6.37E-010 | MW | total network loss 734.180730 MW vs reported 734.180730 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 2.37E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 5.19E-009 | MVA | same residual as law 6, reactive component included at 4584 PQ bus(es), by the bus types the solve ended with; 129 of them declared PV and solved as PQ (129 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```

## r5 notes (added by hand 2026-11-01)

- Best Italy case. The r4 bug fixes are carried over:  idle converters set to pq,  transliterating to_ascii, 
  embed-above-fleet, and the #41 relief is off (no fitted values). r5 adds one EHV/HV coupling per PHYSICAL station
 (EHV sites joined by their own EHV/EHV transformer count as one: 64 pairs) and the filter (5 OSM 132 kV ways
  at 16.7 Hz dropped).
- Against r4: V 0.9568-1.1404 -> 0.9529-1.1206 pu, spread 70.629 -> 70.853 deg, over 100 % 7 -> 9 (worst
  174.7 -> 176.9 %), 132 kV Ik'' max 92.38 -> 81.59 kA (Cislago), 132 kV buses over 31.5 kA 815 -> 760 of 2,666,
  220 kV max 77.69 -> 73.18 kA. Against r3 (it moved 573.3 MW with the FITTED #41 relief): 4 overloads (worst
  161.2 %), spread 68.053 deg, 132 kV max 91.51 kA.
- The remaining 132 kV fault level comes from the meshed Milan / Varese 132 kV network. Terna runs it sectionalised,
  but the normal open points are not published. Couplings stay ASSUMED at 2 x 250 MVA, x 12 % [VERIFY].
