# MODEL CARD: Iberian mainland (Spain + Portugal) 400/220/150/132/110 kV transmission grid winter peak 2026-01-07 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Iberian mainland (Spain + Portugal) 400/220/150/132/110 kV transmission grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-07T19:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over es, pt; local time CET (UTC+1) in Spain, WET (UTC+0) in Portugal).
- Buses 3688 (5 boundary points), branches 4793 (lines 4135, transformers 658), generators 5041.
- Buses by kV: 400 kV 339, 220 kV 923, 150 kV 117, 132 kV 1739, 110 kV 255, 20 kV 315.
- Dispatch 51514.2 MW (plant in this system) + boundary imports 1.0 MW; demand 50741.8 MW (incl. boundary exports 0.0 MW).
- Slack: 1 reference: Besos.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 3688 | 1790 (48.5%) | 0 (0.0%) | 1583 (42.9%) | 315 (8.5%) |
| Branches | 4793 | 0 (0.0%) | 1461 (30.5%) | 3330 (69.5%) | 2 (0.0%) |
| Generators | 5041 | 3522 (69.9%) | 0 (0.0%) | 1519 (30.1%) | 0 (0.0%) |
| Demand points | 1513 | 0 (0.0%) | 0 (0.0%) | 1513 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 144 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 144 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of ES, PT: 1272 AC buses, 1548 internal lines (118 underground / submarine in the model, given cable parameters), 117 transformers; 1800 buses named from OSM.
- Systems: {'main': 3373, 'island1': 12}; components 2 [3373, 12].
- Boundary points (cut ties, HVDC terminals, manual points): Andorra ac x1; France ac x4; France hvdc x2; Morocco ac x1; internal hvdc x2.
- 110-150 kV class layer: {'osm_line_ways': 12361, 'ways_not_grid_frequency': {'frequency 0': 13}, 'traction_substations_dropped': 202, 'coupling_units_osm': [{'tx': 'cpl:relation/8259893-220>osmhv:way/122814554-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/105579046-220>osmhv:way/1260546916-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/105579046-220>osmhv:way/1260546916-132', 'units': 3, 'unit_mva': 250.0, 'how': '3 OSM-mapped unit(s) with both voltages; units max(3, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1120397197-400>osmhv:way/1120397197-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1167713589-220>osmhv:way/1167713589-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1252514183-220>osmhv:way/1252514183-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1275359449-220>osmhv:way/1275359449-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1277630100-400>osmhv:way/1277630100-132', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/129055610-400>osmhv:way/129055610-150', 'units': 2, 'unit_mva': 450.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 450 MVA)'}, {'tx': 'cpl:virtual_way/137265337:1-400>osmhv:way/132865612-150', 'units': 2, 'unit_mva': 360.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 360 MVA)'}, {'tx': 'cpl:way/144487932-400>osmhv:way/216251164-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/144552378-220>osmhv:way/144552378-150', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 250 MVA)'}, {'tx': 'cpl:way/144599061-400>osmhv:way/144599061-150', 'units': 2, 'unit_mva': 450.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 450 MVA)'}, {'tx': 'cpl:virtual_way/148052303:0-400>osmhv:way/144622215-150', 'units': 2, 'unit_mva': 360.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 360 MVA)'}, {'tx': 'cpl:way/144635505-400>osmhv:way/144635505-150', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 250 MVA)'}, {'tx': 'cpl:way/144909709-400>osmhv:way/144909709-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/145171008-400>osmhv:way/1277780459-132', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/145312949-400>osmhv:way/1266109989-132', 'units': 3, 'unit_mva': 450.0, 'how': '3 OSM-mapped units, OSM rating tags (mean 450 MVA)'}, {'tx': 'cpl:way/145330286-220>osmhv:way/116504309-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/151061884-400>osmhv:way/151061884-150', 'units': 2, 'unit_mva': 450.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 450 MVA)'}, {'tx': 'cpl:way/163194137-400>osmhv:way/163194137-150', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/171251565-400>osmhv:way/171251565-132', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/171253574-400>osmhv:way/171253574-150', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/189184555-400>osmhv:way/191458480-132', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/196215046-400>osmhv:way/196215046-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/200253359-400>osmhv:way/1254557566-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:virtual_way/1323054981:0-400>osmhv:way/201459319-150', 'units': 2, 'unit_mva': 450.0, 'how': '2 OSM-mapped units, OSM rating tags (mean 450 MVA)'}, {'tx': 'cpl:way/226886241-400>osmhv:way/1358349622-132', 'units': 4, 'unit_mva': 177.5, 'how': '4 OSM-mapped units, OSM rating tags (mean 177.5 MVA)'}, {'tx': 'cpl:way/329277804-220>osmhv:way/329277804-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/33771314-400>osmhv:way/33771314-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/411107082-220>osmhv:way/411107082-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/43797051-220>osmhv:way/43797051-132', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/46106589-220>osmhv:way/46106589-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/51247251-400>osmhv:way/51247251-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/675714143-400>osmhv:way/229184275-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/75606778-400>osmhv:way/1251647548-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/772400244-400>osmhv:way/772400244-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/941947459-400>osmhv:way/1359377028-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:osmhv:way/151061884-150>osmhv:way/151061884-132', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}], 'untagged_voltage_inferred': {}, 'ways_without_hv_class': 7360, 'segments': 6263, 't_junction_splits': 1262, 'routes': 5823, 'routes_kept': 2602, 'stub_routes_pruned': 162, 'ends_snapped_within_km': 0.5, 'ends_snapped': 143, 'foreign_hv_buses_dropped': 4, 'ends_snapped_to_tagged_substation': 75, 'tagged_snap_km': 2.0, 'tagged_snap_examples': ['way/62047742 Subestacio de Salt (1.64 km, 132 kV)', 'way/1152631738  (0.94 km, 132 kV)', 'way/23882397 Subestacion de Majadahonda (0.80 km, 132 kV)', 'way/170156246 SET Parque Eolico Lezuza (0.72 km, 132 kV)', 'way/170671537 Subestacion Aceca (0.72 km, 132 kV)', 'way/1242344187 SE Castiello (1.51 km, 132 kV)', 'way/188781055 SET Parque Eolico Montemaior (1.41 km, 132 kV)', 'way/169883205 Subestacion de Boimente (0.70 km, 132 kV)'], 'pypsa_virtual_ehv_buses_sited': 25, 'virtual_site_examples': ['virtual_relation/4742657:b:1-220 -> way/91441017 Subestacion de Almaraz (1.80 km)', 'virtual_way/118758875:1-400 -> way/118758874 Central Termica de Velilla (1.55 km)', 'virtual_way/1232962947:0-400 -> way/1449716061 Subestacion Toro Renovables (0.07 km)', 'virtual_way/1323054981:0-400 -> way/201459319 Subestacao de Tavira (1.13 km)', "virtual_way/137265337:1-400 -> way/132865612 Subestacao de Riba d'Ave (1.08 km)", 'virtual_way/143483675:0-220 -> way/60354466 Subestacion Pazos de Borben (1.16 km)', 'virtual_way/144909704:d:1-400 -> way/144909722 Subestacion Litoral (1.06 km)', 'virtual_way/145431965:1-400 -> way/1237239896 Villanueva de los Escuderos II (1.16 km)'], 'hv_buses': 2113, 'hv_buses_by_kv': {'132': 1741, '110': 255, '150': 117}, 'tee_junctions': 960, 'couplings': 227, 'max_couplings_at_one_hv_bus': 2, 'uncoupled_components_left_out': {'buses': 72, 'routes': 55, 'km': 372.8}, 'route_km_kept': 19803.8}.
- Snapshot balance (energy-charts): generation by type 51514.2 MW, net import 1.0 MW, pumping 0.7 MW -> demand 51514.5 MW (the source's own load series: 51105.8 MW).
- Plants left out (islands, outside the boxes): {'rows': 102, 'mw': 2776.06, 'by_fuel': {'battery': 56.6, 'biomass': 45.0, 'coal': 510.0, 'gas': 678.0, 'geothermal': 24.0, 'hydro': 23.3, 'oil': 947.1, 'pumped_storage': 2.4, 'solar': 414.1, 'wind_onshore': 75.56}}.
- Not modelled: internal HVDC relation/17631956-250-DC at way/347643820-220 (island1 -> main): no flow published for it in the snapshot sources; not modelled (0 MW) [VERIFY]

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 294.4 | 0.0 |
| biomass | 1343.3 | 986.4 |
| coal | 672.0 | 0.0 |
| gas | 30755.4 | 13973.1 |
| hydro | 15071.2 | 9184.5 |
| interconnector | 6.0 | 1.0 |
| nuclear | 7408.0 | 7112.0 |
| oil | 602.0 | 36.0 |
| other | 35.1 | 33.3 |
| pumped_storage | 11561.5 | 5805.4 |
| solar | 47544.7 | 42.1 |
| wind_offshore | 45.0 | 2.0 |
| wind_onshore | 38806.3 | 14339.4 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| France | 0.1 | virtual_relation/8423568:a:0-225 (ac merged_relation/8423568:b-225+1, share 0.08 by rating) |
| France | 0.1 | virtual_relation/8481942:a:0-225 (ac merged_relation/8481942:e-225+4, share 0.08 by rating) |
| France | 0.3 | way/178294745-400 (ac relation/6530789-400, share 0.27 by rating) |
| France | 0.3 | virtual_relation/8481943:a:1-400 (ac relation/8481943:b-400, share 0.27 by rating) |
| France | 0.2 | way/340399370-400 (hvdc relation/9934065-320-DC, share 0.15 by rating) |
| France | 0.2 | way/340399370-400 (hvdc relation/9934066-320-DC, share 0.15 by rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 4019 overhead lines (every one), 116 cables kept static; per line in ambient_ratings.json
- components not joined to a modelled system left out: 12 buses in 1 components (largest 12 buses; e.g. ['virtual_way/137307524:1-220', 'virtual_way/137310061:0-220', 'way/139280545-220', 'way/139280769-220', 'way/143044526-220', 'way/143293789-220', 'way/148347794-220', 'way/347643820-220'])
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 2045 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- RfG rule (Regulation (EU) 2016/631 Art. 5, ES limits: type B 0.1 MW, type C 5 MW): 82 running units (189.7 MW) below their voltage-control threshold set pq at unity power factor (documented rule; national thresholds [VERIFY])
- synchronous plant moved behind 315 lumped GSUs (73676 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; nuclear 7/7 units; hydro 63/268 units; biomass 26/47 units; oil 1/7 units; gas 15/68 units; pumped_storage 9/37 units. Offline units in the case: 314 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Besos at Subestacio de Rubi 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- bus shunts placed where the snapshot needs reactive support (11 passes of a Newton solve without reactive limits): 45 reactors 4090 MVAr, 99 capacitors 4660 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 144 buses, 4660 MVAr capacitors and 4090 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Besos takes the balance (losses and the losses-allowance error); synthetic
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
- energy-charts public net generation by type and cross-border physical flows (snapshot hour) (Fraunhofer ISE (ENTSO-E based)), CC BY 4.0
- Population on 1 January 2024 by NUTS 3 region (demo_r_pjanaggr3) and GISCO NUTS 2024 label points (Eurostat / GISCO (EuroGeographics boundaries)), CC BY 4.0 (Eurostat); GISCO points (c) EuroGeographics
- Model assembly steps: voltage classes, cuts at the border, cable parameters, transformer units, couplings, placement, demand allocation, dispatch, slack, repairs (a private build pipeline using GridSim's solver), private
- GISCO NUTS 2024 regions ((c) EuroGeographics) and Natural Earth (public domain): geography.json.

Licence: ODbL 1.0 (see ATTRIBUTION.txt).

## Files beside the case

- Shipped here: the GridSim case files, geography.json, provenance.json, evidence_tags.json, ATTRIBUTION.txt and BUILD_README.md. Internal build records are not published.
## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf iberia-spine-400-220-132-r8   (flat start: vm 1, vaDeg 0; exit 0, 2.9 s)
Power flow - Iberian mainland (Spain + Portugal) 400/220/150/132/110 kV transmission grid winter peak 2026-01-07 (UnvalidatedAtScale) (3688 buses)
  converged in 10 iteration(s), mismatch 3.34E-011 pu   losses 1051.298 MW / -13807.311 MVAr
  voltage range 0.9513 - 1.0510 pu
  lowest voltages:
      bus 761    0.9513 pu    -15.721 deg
      bus 3287   0.9517 pu    -19.522 deg
      bus 1163   0.9518 pu    -15.646 deg
      bus 3314   0.9519 pu    -19.769 deg
      bus 3312   0.9520 pu    -20.078 deg
      bus 3209   0.9520 pu    -20.073 deg
      bus 3190   0.9527 pu    -19.749 deg
      bus 1201   0.9529 pu    -15.466 deg
      bus 3340   0.9533 pu    -20.410 deg
      bus 3210   0.9533 pu    -19.542 deg
      bus 1144   0.9534 pu    -15.404 deg
      bus 3215   0.9539 pu    -18.961 deg
(warm start baked into buses.json from that solve: flat start took 10 Newton iterations)
$ gridsim pf iberia-spine-400-220-132-r8 (warm start)   (exit 0, 1.0 s)
Power flow - Iberian mainland (Spain + Portugal) 400/220/150/132/110 kV transmission grid winter peak 2026-01-07 (UnvalidatedAtScale) (3688 buses)
  converged in 7 iteration(s), mismatch 2.60E-011 pu   losses 1051.298 MW / -13807.311 MVAr
  voltage range 0.9513 - 1.0510 pu
  lowest voltages:
      bus 761    0.9513 pu    -15.721 deg
      bus 3287   0.9517 pu    -19.522 deg
      bus 1163   0.9518 pu    -15.646 deg
      bus 3314   0.9519 pu    -19.769 deg
      bus 3312   0.9520 pu    -20.078 deg
      bus 3209   0.9520 pu    -20.073 deg
      bus 3190   0.9527 pu    -19.749 deg
      bus 1201   0.9529 pu    -15.466 deg
      bus 3340   0.9533 pu    -20.410 deg
      bus 3210   0.9533 pu    -19.542 deg
      bus 1144   0.9534 pu    -15.404 deg
      bus 3215   0.9539 pu    -18.961 deg
$ gridsim physics-check iberia-spine-400-220-132-r8   (exit 0, 1.0 s)
Physics-law audit  -  iberia-spine-400-220-132-r8  (3688 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 9.66E-011 | MW | independent dissipation 1051.297969 MW (branch 1051.2980 + shunt 0.0000) vs reported loss 1051.297969 MW |
| 2 | Ohm's law | Holds | 3.70E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 8.05E-011 | MW | total network loss 1051.297969 MW vs reported 1051.297969 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 9.21E-011 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 7.89E-010 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 3.30E-009 | MVA | same residual as law 6, reactive component included at 3143 PQ bus(es), by the bus types the solve ended with; 44 of them declared PV and solved as PQ (44 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
