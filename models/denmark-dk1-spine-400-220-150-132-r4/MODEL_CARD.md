# MODEL CARD: Danish DK1 (Jutland and Funen, Continental Europe synchronous area) 400/220/150 kV grid winter peak 2026-01-12 (UnvalidatedAtScale)

**Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Danish DK1 (Jutland and Funen, Continental Europe synchronous area) 400/220/150 kV grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-12T16:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over dk; local time CET (UTC+1)).
- Buses 179 (6 boundary points), branches 248 (lines 207, transformers 41), generators 376.
- Buses by kV: 400 kV 28, 220 kV 5, 150 kV 128, 20 kV 18.
- Dispatch 4331.8 MW (plant in this system) + boundary imports 2559.7 MW; demand 6830.5 MW (incl. boundary exports 2822.6 MW).
- Slack: 1 reference: Nordjylland.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 179 | 94 (52.5%) | 0 (0.0%) | 67 (37.4%) | 18 (10.1%) |
| Branches | 248 | 0 (0.0%) | 31 (12.5%) | 217 (87.5%) | 0 (0.0%) |
| Generators | 376 | 273 (72.6%) | 0 (0.0%) | 103 (27.4%) | 0 (0.0%) |
| Demand points | 102 | 0 (0.0%) | 0 (0.0%) | 102 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 27 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 27 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of DK: 48 AC buses, 56 internal lines (135 underground / submarine in the model, given cable parameters), 4 transformers; 176 buses named from OSM.
- Systems: {'dk1': 161, 'dk2': 145}; components 2 [161, 145].
- Boundary points (cut ties, HVDC terminals, manual points): Germany ac x3; Germany hvdc x1; Netherlands hvdc x1; Norway hvdc x2; Sweden ac x2; Sweden hvdc x1; United Kingdom hvdc x1; internal hvdc x2.
- 110-150 kV class layer: {'osm_line_ways': 2254, 'ways_not_grid_frequency': {'frequency 0': 58}, 'traction_substations_dropped': 11, 'ways_without_hv_class': 672, 'segments': 2400, 't_junction_splits': 818, 'routes': 2269, 'routes_kept': 368, 'stub_routes_pruned': 13, 'ends_snapped_within_km': 0.5, 'ends_snapped': 15, 'foreign_hv_buses_dropped': 1, 'ends_snapped_to_tagged_substation': 8, 'tagged_snap_km': 2.0, 'tagged_snap_examples': ['way/32235977 150 kV Herning (0.37 km, 150 kV)', 'way/103575499 150 kV Sonderborg (0.70 km, 150 kV)', 'way/253817668 Estrupvej (0.57 km, 150 kV)', 'way/131443963 132kV Masnedo (0.49 km, 132 kV)', 'way/131339681 132/50 kV Teglstrupgard (0.80 km, 132 kV)', 'way/253817668 Estrupvej (0.58 km, 150 kV)', 'way/253817669 150kV Lykkegard (0.59 km, 150 kV)', 'way/198614550 132 kV Hedegard (0.34 km, 132 kV)'], 'pypsa_virtual_ehv_buses_sited': 1, 'virtual_site_examples': ['virtual_way/385384761:0-400 -> way/98212652 400 kV Vendsysselvaerket (1.47 km)'], 'hv_buses': 258, 'hv_buses_by_kv': {'132': 129, '150': 129}, 'tee_junctions': 88, 'couplings': 31, 'max_couplings_at_one_hv_bus': 2, 'uncoupled_components_left_out': {'buses': 6, 'routes': 5, 'km': 81.0}, 'route_km_kept': 3101.9}.
- Snapshot balance (energidataservice): generation by type 4331.8 MW, net import -262.9 MW, pumping 0.0 MW -> demand 4069.0 MW (the source's own load series: 4069.0 MW).
- Plants left out (islands, outside the boxes): {'rows': 7, 'mw': 90.1, 'by_fuel': {'battery': 39.1, 'biomass': 37.0, 'solar': 14.0}}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 78.0 | 0.0 |
| biomass | 712.0 | 247.7 |
| coal | 716.0 | 490.0 |
| gas | 1137.2 | 516.0 |
| hydro | 1.7 | 1.7 |
| interconnector | 2559.7 | 2559.7 |
| solar | 2529.5 | 5.5 |
| wind_offshore | 1762.6 | 1363.8 |
| wind_onshore | 1828.9 | 1707.2 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Norway | 465.2 | way/1271587272-400 (hvdc relation/3391931-350-DC, share 0.57 by rating) |
| Norway | 346.5 | way/1271587272-400 (hvdc relation/8184632-500-DC, share 0.43 by rating) |
| Sweden | -178.8 | way/98216482-400 (hvdc relation/8184629-300-DC, share 1.00 by rating) |
| Germany | -541.5 | way/95840891-400 (ac relation/12842815-400, share 0.25 by rating) |
| Germany | -541.5 | way/95840891-400 (ac relation/3732382:a-400, share 0.25 by rating) |
| Germany | -1083.1 | way/95840891-400 (ac way/907517160-400, share 0.50 by rating) |
| Netherlands | 683.3 | way/1284726676-400 (hvdc relation/8185420-320-DC, share 1.00 by rating) |
| United Kingdom | 1064.8 | way/1101832649-400 (hvdc relation/15781671-525-DC, share 1.00 by rating) |
| internal | -477.6 | way/1384028957-400 (hvdc relation/5487095-400-DC, share 1.00 by rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 144 overhead lines (every one), 63 cables kept static; per line in ambient_ratings.json
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 162 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- synchronous plant moved behind 18 lumped GSUs (3018 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; thermal 4/19 units; hydro 0/0 units. Offline units in the case: 15 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Nordjylland at 400 kV Vendsysselvaerket 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (4 passes of a Newton solve without reactive limits): 22 reactors 1030 MVAr, 5 capacitors 150 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 27 buses, 150 MVAr capacitors and 1030 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Nordjylland takes the balance (losses and the losses-allowance error); synthetic
- No demand is moved: the India radial-chain relief is not used in this batch.

Assumed (typical values or documented rules, not fitted; tagged estimated with [VERIFY]):

- losses allowance 1.5 % of the balance demand (the slack takes the rest)
- EHV transformers 2 x 400 MVA, x 12 %; EHV/HV couplings 2 x 250 MVA, x 12 % (one per EHV site and HV class); X/R 40
- HV lines single ACSR about 585 mm2: R 0.060, X 0.400 ohm/km, C 9 nF/km, 870 A; cables X 0.12-0.13 ohm/km, C 0.20-0.25 uF/km
- GSU x 14.5 % own rating, X/R 40; generator Q range -0.30 to +0.62 x MW; converter +/-0.33 x MW; load power factor 0.97
- unit commitment largest first to 0.8 loading (nuclear 0.95); listed fleet short -> embedded remainder by population
- plants >= 250 MW on the top EHV class; above one HV circuit (870 A, 0.85 pf) on EHV; < 100 MW on HV
- boundary flows split over a neighbour's tie points by tie rating
- HV layer (when built): OSM ways split at T-junctions; a dangling line end, or a PyPSA virtual EHV line end, within 2.0 km (TAGGED_SNAP_KM, assumed) of a substation whose OSM voltage tag carries that class ends there (mapping gap rule)
- HV layer (when built): EHV substations whose own OSM voltage tag lists a level below 100 kV take demand (attested supply to unmodelled distribution); plant under 100 MW on an HV bus only up to the bus's connected circuit capacity (rating x circuits of its lines and couplings), else the next HV bus within 40 km, else the nearest EHV bus (grid-access rule; RD 1183/2020 for Spain [VERIFY])
- load buses take the demand of the NUTS 3 region whose polygon contains them; r1: nearest label point)
- RfG rule (when rfg_area is set): Regulation (EU) 2016/631 Art. 5 Table 1 limits (CE type B 1 MW / C 50 MW; Nordic 1.5 / 10 MW): converters below type C and synchronous units below type B run pq at unity pf; the synchronous ones sit on the grid bus, not behind a GSU; national thresholds may be lower [VERIFY]
- reactive repair never on generator terminal buses (shunts belong on the grid bus)

## Known gaps

- No TSO impedances: EHV line R/X/B come from PyPSA-Eur's standard overhead types (400 / 380 kV 4 x 240/40, 220 kV 2 x 240/40) times the OSM length; real conductors differ; cables use typical XLPE values.
- EHV transformers: 2 x 400 MVA, x 12 % at every 400/220 kV site PyPSA marks; real unit counts unknown.
- 110-150 kV class from OSM only (no impedances published): standard conductor per km; ONE estimated EHV/HV coupling (2 x 250 MVA) per EHV substation and HV class rule), so real transformer counts and HV substations near an EHV site that OSM does not join by a line are missing.
- No reactive compensation is published; the bus shunts are fixed repairs.
- Busbar splits are not modelled: one bus per OSM substation and voltage.
- Neighbours are fixed boundary injections (snapshot flows split by tie rating): no foreign network and no fault infeed from abroad.
- Demand by NUTS 3 population (no TSO regional load map at the snapshot hour).
- Unit commitment by size, not the real schedule.

## Sources

- Prebuilt Electricity Network for PyPSA-Eur based on OpenStreetMap Data v0.7 (Zenodo 18619025, 2026-02-12): buses, lines (OSM length, circuits; PyPSA standard line types), transformers, HVDC links (PyPSA-Eur contributors / OpenStreetMap contributors), ODbL 1.0
- OpenStreetMap: names of the substations behind the PyPSA buses; 100-170 kV lines and substations (Overpass API, 2026-11-01) (OpenStreetMap contributors), ODbL 1.0
- powerplantmatching matched power plant list (master, fetched 2026-10-31) (PyPSA / FIAS powerplantmatching contributors), CC BY 4.0
- Energi Data Service: production, consumption and exchange per price area (DK1, DK2), 5-minute (snapshot hour) (Energinet), Energi Data Service terms (free reuse with source attribution) [VERIFY]
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- GISCO NUTS 2024 regions ((c) EuroGeographics) and Natural Earth (public domain): geography.json.

Licence: pending a licence check (see ATTRIBUTION.txt and LICENSING.md).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf denmark-dk1-spine-400-220-150-132-r4   (flat start: vm 1, vaDeg 0; exit 0, 0.4 s)
Power flow - Danish DK1 (Jutland and Funen, Continental Europe synchronous area) 400/220/150 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (179 buses)
  converged in 7 iteration(s), mismatch 3.10E-011 pu   losses 153.042 MW / -1726.879 MVAr
  voltage range 1.0126 - 1.0330 pu
  lowest voltages:
      bus 130    1.0126 pu    -14.382 deg
      bus 176    1.0126 pu    -14.382 deg
      bus 136    1.0134 pu    -11.653 deg
      bus 133    1.0136 pu    -12.385 deg
      bus 129    1.0151 pu    -13.825 deg
      bus 53     1.0151 pu    -13.819 deg
      bus 21     1.0157 pu    -11.753 deg
      bus 119    1.0158 pu    -13.599 deg
      bus 55     1.0158 pu    -13.597 deg
      bus 122    1.0161 pu    -18.294 deg
      bus 100    1.0162 pu    -13.420 deg
      bus 172    1.0162 pu    -13.420 deg
(warm start baked into buses.json from that solve: flat start took 7 Newton iterations)
$ gridsim pf denmark-dk1-spine-400-220-150-132-r4 (warm start)   (exit 0, 0.4 s)
Power flow - Danish DK1 (Jutland and Funen, Continental Europe synchronous area) 400/220/150 kV grid winter peak 2026-01-12 (UnvalidatedAtScale) (179 buses)
  converged in 4 iteration(s), mismatch 2.51E-011 pu   losses 153.042 MW / -1726.879 MVAr
  voltage range 1.0126 - 1.0330 pu
  lowest voltages:
      bus 130    1.0126 pu    -14.382 deg
      bus 176    1.0126 pu    -14.382 deg
      bus 136    1.0134 pu    -11.653 deg
      bus 133    1.0136 pu    -12.385 deg
      bus 129    1.0151 pu    -13.825 deg
      bus 53     1.0151 pu    -13.819 deg
      bus 21     1.0157 pu    -11.753 deg
      bus 119    1.0158 pu    -13.599 deg
      bus 55     1.0158 pu    -13.597 deg
      bus 122    1.0161 pu    -18.294 deg
      bus 100    1.0162 pu    -13.420 deg
      bus 172    1.0162 pu    -13.420 deg
$ gridsim physics-check denmark-dk1-spine-400-220-150-132-r4   (exit 0, 0.4 s)
Physics-law audit  -  denmark-dk1-spine-400-220-150-132-r4  (179 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 2.85E-010 | MW | independent dissipation 153.042196 MW (branch 153.0422 + shunt 0.0000) vs reported loss 153.042196 MW |
| 2 | Ohm's law | Holds | 4.62E-011 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 2.86E-010 | MW | total network loss 153.042196 MW vs reported 153.042196 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 6.71E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 1.78E-009 | MVA | same residual as law 6, reactive component included at 137 PQ bus(es), by the bus types the solve ended with; 6 of them declared PV and solved as PQ (6 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
