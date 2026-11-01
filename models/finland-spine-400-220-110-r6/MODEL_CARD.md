# MODEL CARD: Finnish 400/220/110 kV transmission grid winter peak 2026-01-08 (UnvalidatedAtScale)

**Released as an open database under the Open Database Licence (ODbL) 1.0 in the GridSim-Models repository; credits in ATTRIBUTION.txt. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** Not checked against official study results. A solvable rough map of the Finnish 400/220/110 kV transmission grid for one winter peak snapshot: OpenStreetMap topology with standard line types (PyPSA-Eur) and the OSM 110-150 kV class layer where present, register-based generation (powerplantmatching), the snapshot hour's generation and border flows, allocated demand. Use it to learn, compare and explore, not to plan or operate.

## What it is

- Snapshot: 2026-01-08T15:00:00+00:00 (UTC hour start; hour (UTC, mean of its quarter-hours) of the highest summed energy-charts load in January 2026 over fi; local time EET (UTC+2)).
- Buses 1391 (7 boundary points), branches 1810 (lines 1597, transformers 213), generators 1128.
- Buses by kV: 400 kV 83, 220 kV 26, 110 kV 1135, 20 kV 147.
- Dispatch 14246.6 MW (plant in this system) + boundary imports 2229.2 MW; demand 16244.1 MW (incl. boundary exports 1025.0 MW).
- Slack: 1 reference: Olkiluoto 3.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 1391 | 562 (40.4%) | 0 (0.0%) | 682 (49.0%) | 147 (10.6%) |
| Branches | 1810 | 0 (0.0%) | 145 (8.0%) | 1665 (92.0%) | 0 (0.0%) |
| Generators | 1128 | 387 (34.3%) | 0 (0.0%) | 741 (65.7%) | 0 (0.0%) |
| Demand points | 737 | 0 (0.0%) | 0 (0.0%) | 737 (100.0%) | 0 (0.0%) |
| Shunts (repairs) | 277 | 0 (0.0%) | 0 (0.0%) | 0 (0.0%) | 277 (100.0%) |

Buses are 'attested' when OSM names the substation; EHV lines 'derived' (OSM length x PyPSA standard type), cables and HV lines 'estimated'. Tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic.

## Topology facts

- PyPSA-Eur OSM prebuilt network v0.7, rows of FI: 109 AC buses, 145 internal lines (24 underground / submarine in the model, given cable parameters), 5 transformers; 562 buses named from OSM.
- Systems: {'main': 1244}; components 1 [1244].
- Boundary points (cut ties, HVDC terminals, manual points): Estonia hvdc x2; Norway ac x1; Sweden ac x4; Sweden hvdc x2.
- 110-150 kV class layer: {'osm_line_ways': 2962, 'ways_not_grid_frequency': {'frequency 0': 11}, 'traction_substations_dropped': 0, 'coupling_units_osm': [{'tx': 'cpl:relation/15436115-220>osmhv:relation/15436115-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1107461441-400>osmhv:way/1107461441-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1137690029-400>osmhv:way/1137690029-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1155254820-400>osmhv:way/1155254820-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1159141282-220>osmhv:way/1159141282-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/123462491-400>osmhv:way/123462491-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/128463750-400>osmhv:way/128463750-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/1286130176-400>osmhv:way/1286130176-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/136068907-400>osmhv:way/136068907-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/144383819-400>osmhv:way/144383819-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/144832705-400>osmhv:way/144832705-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/149965733-400>osmhv:way/149965733-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/149965739-400>osmhv:way/149965739-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/150209972-400>osmhv:way/150209972-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/151818544-400>osmhv:way/151818544-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/159532385-400>osmhv:way/159532385-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/167705754-400>osmhv:way/167705754-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/238856422-400>osmhv:way/238856422-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/26501426-400>osmhv:way/26501426-110', 'units': 3, 'unit_mva': 250.0, 'how': '3 OSM-mapped unit(s) with both voltages; units max(3, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/26619335-400>osmhv:way/26619335-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/27674611-400>osmhv:way/27674611-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/28820749-400>osmhv:way/28820749-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/30601175-400>osmhv:way/25594007-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/34623113-400>osmhv:way/34623113-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/348003562-400>osmhv:way/348003562-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/351960012-400>osmhv:way/351960012-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/35281467-400>osmhv:way/35281467-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/391142388-220>osmhv:way/391142388-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/391145068-220>osmhv:way/391145068-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/43143343-400>osmhv:way/43143343-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/47317827-400>osmhv:way/47317827-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/544156119-400>osmhv:way/544156119-110', 'units': 2, 'unit_mva': 250.0, 'how': '1 OSM-mapped unit(s) with both voltages; units max(1, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/551596913-400>osmhv:way/551596913-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/590767557-400>osmhv:way/590767557-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/881741424-400>osmhv:way/881741424-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:way/98561229-400>osmhv:way/98561229-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}, {'tx': 'cpl:virtual_way/98614435:1-400>osmhv:way/98613134-110', 'units': 2, 'unit_mva': 250.0, 'how': '2 OSM-mapped unit(s) with both voltages; units max(2, 2); 250 MVA each (estimated)'}], 'untagged_voltage_inferred': {'untagged_ways': 1782, 'an end outside every HV substation': 1663, 'inferred 110 kV': 119}, 'ways_without_hv_class': 567, 'segments': 2767, 't_junction_splits': 372, 'routes': 2446, 'routes_kept': 1452, 'stub_routes_pruned': 237, 'ends_snapped_within_km': 0.5, 'ends_snapped': 155, 'foreign_hv_buses_dropped': 5, 'ends_snapped_to_tagged_substation': 108, 'tagged_snap_km': 2.0, 'tagged_snap_examples': ['way/155157360 Nivala sahkoasema (0.30 km, 110 kV)', 'way/192143731  (1.08 km, 110 kV)', 'way/174398894 Ruotsinkylan sahkoasema (1.97 km, 110 kV)', 'way/27013095 Hakkilan sahkoasema (1.27 km, 110 kV)', 'way/87670542 Tourulan sahkoasema (1.07 km, 110 kV)', 'way/88020737 Kyminlinna sahkoasema (1.26 km, 110 kV)', 'way/27013095 Hakkilan sahkoasema (1.27 km, 110 kV)', 'way/94018261  (1.59 km, 110 kV)'], 'pypsa_virtual_ehv_buses_sited': 2, 'virtual_site_examples': ['virtual_way/166777663:0-220 -> way/149965738 Pyhakoski sahkoasema (1.39 km)', 'virtual_way/98614435:1-400 -> way/98613134 Ulvila sahkoasema (1.67 km)'], 'hv_buses': 1135, 'hv_buses_by_kv': {'110': 1135}, 'tee_junctions': 403, 'couplings': 61, 'max_couplings_at_one_hv_bus': 2, 'uncoupled_components_left_out': {'buses': 63, 'routes': 46, 'km': 276.0}, 'route_km_kept': 14036.3}.
- Snapshot balance (energy-charts): generation by type 14246.6 MW, net import 1204.2 MW, pumping 0.0 MW -> demand 15450.9 MW (the source's own load series: 15458.8 MW).
- Plants left out (islands, outside the boxes): {'rows': 0, 'mw': 0.0, 'by_fuel': {}}.

## Generation and dispatch by fuel (MW)

| Fuel | Capacity in case | Dispatch |
|---|---:|---:|
| battery | 300.6 | 0.0 |
| biomass | 3897.2 | 1088.9 |
| coal | 1186.2 | 495.3 |
| gas | 1624.8 | 530.2 |
| hydro | 3172.6 | 1785.1 |
| interconnector | 2229.2 | 2229.2 |
| nuclear | 4622.0 | 4231.9 |
| oil | 1301.2 | 0.0 |
| other | 432.7 | 411.1 |
| pumped_storage | 26.0 | 0.0 |
| solar | 631.9 | 1.1 |
| wind_offshore | 42.0 | 0.0 |
| wind_onshore | 9278.0 | 5703.1 |

## Boundary injections (MW, + import)

| Country / link | MW | Where |
|---|---:|---|
| Estonia | -666.3 | way/26619335-400 (hvdc relation/6886400-450-DC, share 0.65 by rating) |
| Estonia | -358.8 | way/27674611-400 (hvdc relation/8184630-150-DC, share 0.35 by rating) |
| Norway | 32.0 | virtual_way/336507649:1-220 (ac merged_way/400415359-220+1, share 1.00 by rating) |
| Sweden | 442.4 | way/47317827-400 (ac merged_way/1025530506-400+1, share 0.20 SvK measured AC/HVDC share x rating) |
| Sweden | 442.4 | way/286955409-400 (ac merged_way/71375664-400+1, share 0.20 SvK measured AC/HVDC share x rating) |
| Sweden | 442.4 | way/1348464438-400 (ac way/1348774144-400, share 0.20 SvK measured AC/HVDC share x rating) |
| Sweden | 442.4 | way/47317827-400 (ac way/80342200-400, share 0.20 SvK measured AC/HVDC share x rating) |
| Sweden | 263.2 | way/26501426-400 (hvdc relation/3391954-500-DC, share 0.12 SvK measured AC/HVDC share x rating) |
| Sweden | 164.5 | way/26501426-400 (hvdc relation/8184631-400-DC, share 0.07 SvK measured AC/HVDC share x rating) |

## Repairs (every change made so the case solves)

- seasonal overhead-line ratings (tightened rule rung 2, evidence derived): snapshot season winter; factor = median over six JAO Core TSOs (MAVIR, PSE, TEL, TransnetBW, TenneT NL, RTE) of each TSO's median winter/summer seasonal Imax ratio (JAO Core Static Grid Model 9th release (2026-03), Lines + Tielines): 380 kV class 1.047, 220 kV class (and 110-150 kV, [VERIFY]) 1.199; static base = EN 50182 summer design rating (35 C, 900 W/m2, 0.6 m/s); cables static: 1573 overhead lines (every one), 24 cables kept static; per line in ambient_ratings.json
- idle converter units (output under 1% of capacity: PV at night, becalmed wind, batteries): 50 set pq at 0 MVAr, no voltage control and no fault infeed (estimated)
- RfG rule (Regulation (EU) 2016/631 Art. 5, Nordic limits: type B 1.5 MW, type C 10 MW): 10 running units (18.0 MW) below their voltage-control threshold set pq at unity power factor (documented rule; national thresholds [VERIFY])
- synchronous plant moved behind 147 lumped GSUs (18521 MVA, x 14.5 % own rating, X/R 40; estimated)
- unit commitment: dispatchable units committed largest first until committed capacity x 0.8 (nuclear 0.95) covers the fuel's snapshot value; nuclear 5/5 units; hydro 25/109 units; biomass 7/51 units; coal 2/4 units; gas 2/12 units. Offline units in the case: 158 (0 MW, pq, no inertia, no fault infeed; estimated)
- slack: largest dispatched synchronous unit Olkiluoto 3 at OSM way/98609844 400kV gen bus, reactive band +/-20000 MVAr (synthetic)
- reactive repair staged by load scaling: shunts placed at 0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00 x demand and dispatch in turn, each stage from the previous stage's shunts (estimated)
- bus shunts placed where the snapshot needs reactive support (51 passes of a Newton solve without reactive limits): 20 reactors 500 MVAr, 247 capacitors 6650 MVAr (synthetic; no open source lists the TSO's reactors, capacitor banks, STATCOMs or synchronous compensators)

## Fitted and assumed values

Fitted (adjusted only so the case solves; no source; tagged synthetic):

- bus shunt repairs: 277 buses, 6650 MVAr capacitors and 500 MVAr reactors, sized by the solver to hold 0.95-1.05 pu (no source lists the compensation; synthetic)
- slack: Olkiluoto 3 takes the balance (losses and the losses-allowance error); synthetic
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
$ gridsim pf finland-spine-400-220-110-r6   (flat start: vm 1, vaDeg 0; exit 0, 0.8 s)
Power flow - Finnish 400/220/110 kV transmission grid winter peak 2026-01-08 (UnvalidatedAtScale) (1391 buses)
  converged in 10 iteration(s), mismatch 2.97E-011 pu   losses 910.801 MW / -1737.240 MVAr
  voltage range 0.9535 - 1.0354 pu
  lowest voltages:
      bus 886    0.9535 pu    -30.333 deg
      bus 1087   0.9538 pu    -31.322 deg
      bus 1366   0.9538 pu    -31.322 deg
      bus 1020   0.9543 pu    -39.515 deg
      bus 1070   0.9544 pu    -29.936 deg
      bus 1362   0.9544 pu    -29.936 deg
      bus 1126   0.9545 pu    -30.027 deg
      bus 1374   0.9545 pu    -30.027 deg
      bus 711    0.9548 pu    -30.276 deg
      bus 1108   0.9550 pu    -18.048 deg
      bus 835    0.9552 pu    -28.219 deg
      bus 836    0.9554 pu    -31.531 deg
(warm start baked into buses.json from that solve: flat start took 10 Newton iterations)
$ gridsim pf finland-spine-400-220-110-r6 (warm start)   (exit 0, 0.7 s)
Power flow - Finnish 400/220/110 kV transmission grid winter peak 2026-01-08 (UnvalidatedAtScale) (1391 buses)
  converged in 7 iteration(s), mismatch 3.52E-011 pu   losses 910.801 MW / -1737.240 MVAr
  voltage range 0.9535 - 1.0354 pu
  lowest voltages:
      bus 886    0.9535 pu    -30.333 deg
      bus 1087   0.9538 pu    -31.322 deg
      bus 1366   0.9538 pu    -31.322 deg
      bus 1020   0.9543 pu    -39.515 deg
      bus 1070   0.9544 pu    -29.936 deg
      bus 1362   0.9544 pu    -29.936 deg
      bus 1126   0.9545 pu    -30.027 deg
      bus 1374   0.9545 pu    -30.027 deg
      bus 711    0.9548 pu    -30.276 deg
      bus 1108   0.9550 pu    -18.048 deg
      bus 835    0.9552 pu    -28.219 deg
      bus 836    0.9554 pu    -31.531 deg
$ gridsim physics-check finland-spine-400-220-110-r6   (exit 0, 0.7 s)
Physics-law audit  -  finland-spine-400-220-110-r6  (1391 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 1.27E-009 | MW | independent dissipation 910.801398 MW (branch 910.8014 + shunt 0.0000) vs reported loss 910.801398 MW |
| 2 | Ohm's law | Holds | 2.04E-009 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.27E-009 | MW | total network loss 910.801398 MW vs reported 910.801398 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 4.88E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 4.88E-009 | MVA | same residual as law 6, reactive component included at 1260 PQ bus(es), by the bus types the solve ended with; 14 of them declared PV and solved as PQ (14 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
