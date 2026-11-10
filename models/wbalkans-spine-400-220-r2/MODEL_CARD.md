# Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) 400/220 kV grid winter peak 2026-01-12 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) 400/220 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-12T16:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over rs, ba, me, mk, xk; local time CET (UTC+1)).
- Buses 198 (19 boundary points), branches 260 (lines 182, transformers 78), generators 532.
- Buses by kV: 400 kV 54, 220 kV 87, 20 kV 57.
- Dispatch 12860.1 MW (plant in this system) + boundary imports 1198.0 MW; demand 13860.8 MW (incl. boundary exports 899.0 MW).
- Slack: 1 reference: Nikola Tesla Phase #2.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 198 | 0 (0.0%) | 0 (0.0%) | 141 (71.2%) | 57 (28.8%) |
| Branches | 260 | 0 (0.0%) | 182 (70.0%) | 78 (30.0%) | 0 (0.0%) |
| Generators | 532 | 322 (60.5%) | 0 (0.0%) | 210 (39.5%) | 0 (0.0%) |
| Demand points | 141 | 0 (0.0%) | 0 (0.0%) | 141 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 4 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 4 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of RS, BA, ME, MK, AL, XK: 141 AC buses, 182 internal lines (0 underground / submarine in the model, given cable parameters), 21 transformers; 0 buses named from OSM.
- Systems: {'main': 141}; components 1 [141].
- Boundary points (cut ties, HVDC terminals, manual points): Bulgaria ac x2; Croatia ac x10; Greece ac x3; Hungary ac x1; Italy hvdc x1; Romania ac x3.
- 110-150 kV class layer: not in this round.
- Snapshot balance (energy-charts): generation by type 12860.1 MW, net import 299.0 MW, pumping 0.0 MW -> demand 13159.1 MW (the source's own load series: 11057.0 MW).
- Plants left out (islands, outside the boxes): {'rows': 0, 'mw': 0.0, 'by_fuel': {}}.
- Country RS: demand 5893.0 MW, generation targets 5534.0 MW, net import (all neighbours) 359.0 MW, external flows Bulgaria 66.0, Croatia 34.0, Hungary -120.0, Romania -510.0; source: energy-charts
- Country BA: demand 2027.9 MW, generation targets 2420.9 MW, net import (all neighbours) -393.0 MW, external flows Croatia -150.0; source: energy-charts
- Country ME: demand 596.9 MW, generation targets 706.9 MW, net import (all neighbours) -110.0 MW, external flows Italy 245.0; source: energy-charts
- Country MK: demand 1212.8 MW, generation targets 943.8 MW, net import (all neighbours) 269.0 MW, external flows Bulgaria -119.0, Greece 853.0; source: energy-charts
- Country XK: demand 1329.8 MW, generation targets 488.8 MW, net import (all neighbours) 841.0 MW, external flows none; source: energy-charts
- Country AL: demand 2098.7 MW, generation targets 2765.7 MW, net import (all neighbours) -667.0 MW, external flows Greece -0.0; source: missing-country rule (population x covered demand per head; covered load factors); rule detail {"population": 2859210.23456961, "covered_population": 15068072.042995935, "covered_demand_mw": 11060.4, "load_factors": {"biomass": 1.0, "hydro": 0.9188198366833144, "other": 0.0, "pumped_storage": 0.1676980198019802, "wind_onshore": 0.01863100403246389, "gas": 0.5909090909090909, "coal": 0.5786953242835596, "solar": 0.0}}
- GeoNames population in the modelled system by country: {'AL': 2859210.23456961, 'BA': 3309798.878859565, 'ME': 615661.5657123772, 'MK': 2114672.9969747216, 'RS': 7391650.618716651, 'XK': 1636287.9827326208}; places on unconnected islands left out: 0 (0 people).

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 64.0 | 0.0 |
| biomass | 39.1 | 39.0 |
| coal | 8470.5 | 4604.1 |
| gas | 822.4 | 481.0 |
| hydro | 8127.8 | 7259.2 |
| interconnector | 1199.0 | 1198.0 |
| oil | 198.0 | 0.0 |
| other | 32.6 | 31.0 |
| pumped_storage | 2424.0 | 406.5 |
| solar | 2094.8 | 0.0 |
| wind_onshore | 2109.1 | 39.3 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Bulgaria | 66.0 | way/152481174-400 (ac merged_way/237583897-400+1, share 1.00 by rating) |
| Croatia | 34.0 | way/236110936-400 (ac relation/13529848-400, share 1.00 by rating) |
| Hungary | -120.0 | way/89109496-400 (ac relation/5506699-400, share 1.00 by rating) |
| Romania | -255.0 | way/52456886-400 (ac merged_way/666492116-400+1, share 0.50 by rating) |
| Romania | -127.5 | way/174921474-400 (ac way/238952268-400, share 0.25 by rating) |
| Romania | -127.5 | way/238249884-400 (ac way/238952273-400, share 0.25 by rating) |
| Croatia | -10.5 | way/841600752-220 (ac relation/13529549-220, share 0.07 by rating) |
| Croatia | -10.5 | way/692824732-220 (ac relation/13529550-220, share 0.07 by rating) |
| Croatia | -38.2 | way/89827347-400 (ac relation/4743309-400, share 0.25 by rating) |
| Croatia | -10.5 | virtual_relation/4743310:a:1-220 (ac relation/4743310:a-220, share 0.07 by rating) |
| Croatia | -38.2 | way/222962996-400 (ac relation/8600944-400, share 0.25 by rating) |
| Croatia | -10.5 | virtual_way/156723492:1-220 (ac way/184198350-220, share 0.07 by rating) |
| Croatia | -10.5 | virtual_way/156723492:1-220 (ac way/776984102-220, share 0.07 by rating) |
| Croatia | -10.5 | way/79818891-220 (ac way/78593926-220, share 0.07 by rating) |
| Croatia | -10.5 | virtual_way/191212861:1-220 (ac way/793080812-220, share 0.07 by rating) |
| Italy | 245.0 | way/665827369-400 (hvdc relation/8185767-500-DC, share 1.00 by rating) |
| Bulgaria | -119.0 | way/196590421-400 (ac merged_relation/3517149-400+1, share 1.00 by rating) |
| Greece | 426.5 | way/196633567-400 (ac way/252077524-400, share 0.50 by rating) |
| Greece | 426.5 | way/196590422-400 (ac way/252077525-400, share 0.50 by rating) |
| Greece | -0.0 | way/249066440-400 (ac way/666594586-400, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal line ratings: 182 overhead lines x 1.1034, 0 cables static (seasonal factor 1.1034 = JAO ratio winter 1.1034 / base 'summer' 1.0000 (median JAO Core SGM 9th release seasonal ratios of the TSOs with calendar seasons (MAVIR, PSE, Transelectrica, TransnetBW, TenneT NL; handbook Annex 1): winter/summer 1.1034 (549 rows), interseason/summer 1.0594 (438 rows)); overhead lines only, cables static; derived)
- RfG thresholds used: type B 1 MW, type C 50 MW (Energy Community contracting parties (RfG adopted by Energy Community decision): national values not found; Continental Europe Table 1 upper limits 1 / 50 / 75 MW [VERIFY]); synchronous units below type B at unity pf
- RfG Art. 5 voltage control: 4 converter units at or above type C (50 MW) are pv with +/- 0.33 MVAr per MW; smaller converters below at unity pf; idle converters never control voltage; embedded aggregates at unity pf
- converter plant (PV, wind, batteries) at fixed unity power factor, no voltage control: 197 units pq at Q = 0 (batch 3 rule; estimated, [VERIFY] grid-code reactive mode)
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 21 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 57 lumped GSUs (19625 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value;. Offline units in the case: 22 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Nikola Tesla Phase #2 at OSM way/52564762 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (2 passes of a Newton solve without reactive limits): 0 reactors 0 MVAr, 4 capacitors 60 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 4 buses, 60 MVAr capacitors and 0 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Nikola Tesla Phase #2 takes the balance (losses and the losses-allowance error); synthetic
- No demand is moved: the India radial-chain relief is not used in this batch.

Assumed (typical values or documented rules, not fitted; tagged estimated with [VERIFY]):

- converter plant (PV, wind, batteries) at fixed unity power factor (pq, Q = 0); only synchronous units regulate voltage [VERIFY]
- losses allowance 1.5 % of the balance demand (the slack takes the rest)
- EHV transformers 2 x 400 MVA, x 12 %; EHV/HV couplings 2 x 250 MVA, x 12 % (one per EHV site and HV class); X/R 40
- HV lines single ACSR about 585 mm2: R 0.060, X 0.400 ohm/km, C 9 nF/km, 870 A; cables X 0.12-0.13 ohm/km, C 0.20-0.25 uF/km
- GSU x 14.5 % own rating, X/R 40; generator Q range -0.30 to +0.62 x MW; converter +/-0.33 x MW; load power factor 0.97
- unit commitment largest first to 0.8 loading (nuclear 0.95); listed fleet short -> embedded remainder by population
- plants >= 250 MW on the top EHV class; above one HV circuit (870 A, 0.85 pf) on EHV; < 100 MW on HV
- boundary flows split over a neighbour's tie points by tie rating

## Round history

- r1: first build (build-first batch).
- r2: Demand shares from the GHSL GHS-POP R2023A 2020 30 arc-second grid (JRC, CC BY 4.0), each populated cell inside a member's home polygons to its nearest load bus (Voronoi) instead of GeoNames points (Dublin was one point; GeoNames has no Dublin sections).
- r2: RfG with NATIONAL thresholds instead of the EU Table 1 limits; synchronous units below type B at unity pf.
- r2: Seasonal ratings: every overhead line x the TSO-practice seasonal factor for the snapshot month; cables static.

## Known gaps

- No TSO impedances: EHV line R/X/B come from PyPSA-Eur's standard overhead types (400 / 380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; real conductors differ; cables use typical XLPE values.
- EHV transformers: 2 x 400 MVA, x 12 % at every 400/220 kV site PyPSA marks; real unit counts unknown.
- 110-150 kV class not modelled in this round: demand and small plant sit on EHV buses.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by GeoNames population of populated places, per country (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31) (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- energy-charts public net generation by type and cross-border physical flows (snapshot hour) (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
- GeoNames per-country dumps: populated places with population and position (demand shares) (GeoNames), CC BY 4.0
- GHSL GHS-POP R2023A epoch 2020, 30 arc-second population grid (demand shares, from the round with pop_grid) (European Commission, Joint Research Centre (Schiavina et al. 2023, doi:10.2905/2FF68A52-5B5B-4A22-8F40-C41DA8332CFE)), CC BY 4.0
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- geoBoundaries gbOpen ADM1 (CC BY 4.0) and Natural Earth (public domain): geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf wbalkans-spine-400-220-r2   (flat start: vm 1, vaDeg 0; exit 0, 0.4 s)
Power flow - Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) 400/220 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (198 buses)
  converged in 4 iteration(s), mismatch 7.98E-011 pu   losses 182.465 MW / -1410.271 MVAr
  voltage range 0.9515 - 1.0328 pu
  lowest voltages:
      bus 96     0.9515 pu     -0.875 deg
      bus 63     0.9515 pu    -10.649 deg
      bus 108    0.9515 pu    -11.540 deg
      bus 79     0.9582 pu     -0.074 deg
      bus 78     0.9586 pu     -0.040 deg
      bus 129    0.9588 pu     -3.728 deg
      bus 137    0.9598 pu     -5.075 deg
      bus 126    0.9616 pu      0.310 deg
      bus 113    0.9652 pu    -11.376 deg
      bus 190    0.9652 pu    -11.376 deg
      bus 107    0.9654 pu     -9.890 deg
      bus 135    0.9655 pu     -0.251 deg
(warm start baked into buses.json from that solve: flat start took 4 Newton iterations)
$ gridsim pf wbalkans-spine-400-220-r2 (warm start)   (exit 0, 0.4 s)
Power flow - Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) 400/220 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (198 buses)
  converged in 1 iteration(s), mismatch 9.37E-013 pu   losses 182.465 MW / -1410.271 MVAr
  voltage range 0.9515 - 1.0328 pu
  lowest voltages:
      bus 96     0.9515 pu     -0.875 deg
      bus 63     0.9515 pu    -10.649 deg
      bus 108    0.9515 pu    -11.540 deg
      bus 79     0.9582 pu     -0.074 deg
      bus 78     0.9586 pu     -0.040 deg
      bus 129    0.9588 pu     -3.728 deg
      bus 137    0.9598 pu     -5.075 deg
      bus 126    0.9616 pu      0.310 deg
      bus 113    0.9652 pu    -11.376 deg
      bus 190    0.9652 pu    -11.376 deg
      bus 107    0.9654 pu     -9.890 deg
      bus 135    0.9655 pu     -0.251 deg
$ gridsim physics-check wbalkans-spine-400-220-r2   (exit 0, 0.4 s)
Physics-law audit  -  wbalkans-spine-400-220-r2  (198 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 3.04E-012 | MW | independent dissipation 182.464591 MW (branch 182.4646 + shunt -0.0000) vs reported loss 182.464591 MW |
| 2 | Ohm's law | Holds | 1.11E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 5.57E-012 | MW | total network loss 182.464591 MW vs reported 182.464591 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 9.45E-011 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 2.76E-010 | MVA | same residual as law 6, reactive component included at 148 PQ bus(es), by the bus types the solve ended with |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
