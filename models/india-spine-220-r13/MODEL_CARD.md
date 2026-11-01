# MODEL CARD: India transmission spine 765/400/220 kV (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** This case has not been checked against official Indian study results. It is a fair approximation of the Indian transmission spine assembled from public data. Demand is low fidelity (an allocated snapshot, not metered). Impedances are typical values per voltage class, not the real conductors. Use it to learn and to explore, not to plan or operate.

## What it is

- Voltage layers: 765, 400, 220 kV, one synchronous grid (India), largest electrical island kept.
- Built from the `model` tables.
- Buses 5318 (1044 are line junctions: OSM tee points and line ends), branches 7757 (lines 6558, transformers 1199), generators 2651.
- Buses by kV: 765 kV 172, 400 kV 1078, 230 kV 52, 220 kV 3381, 21 kV 635.
- Snapshot: Indian evening peak, no solar. Dispatch 279432 MW; net demand in demand.json 301345 MW (includes the HVDC sending converters and any cross-border export below).
- Slack: bus 4696 (1 reference: Sasan UMPP (6x660MW)).
- Islands before selection: 317; dropped 316 islands, 479 buses (322 of them substations); 91.1% of selected buses are in the kept island.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 5318 | 0 (0.0%) | 1 (0.0%) | 5313 (99.9%) | 4 (0.1%) |
| Branches | 7757 | 0 (0.0%) | 129 (1.7%) | 7595 (97.9%) | 33 (0.4%) |
| Generators | 2686 | 426 (15.9%) | 0 (0.0%) | 1472 (54.8%) | 788 (29.3%) |
| Demand points | 2765 | 0 (0.0%) | 0 (0.0%) | 2765 (100.0%) | 0 (0.0%) |
| Shunt buses | 1308 | 1 (0.1%) | 0 (0.0%) | 0 (0.0%) | 1307 (99.9%) |

GridSim tag mapping (evidence_tags.json): attested = Recorded, derived = DerivedFromRecorded, estimated = CuratedPlaceholder [VERIFY], synthetic = Synthetic. provenance.json maps every element to its sources (GridSim gridsim-provenance/1).

## HVDC

GridSim's v1 case has no HVDC element. Each link is a load at the sending converter bus and a fixed-output generator (type hvdc, role pq, no inertia, no fault infeed) at the receiving converter bus (lossless, fixed schedule). Round 2 used a negative load at the receiving end, which GridSim's live view counted once as generation and netted out of demand.

| Link | Kind | From bus | To bus | Rating MW | Schedule MW |
|---|---|---|---|---:|---:|
| Rihand - Dadri | LCC | 1193 Rihand Converter Station 400kV | 1139 Dadri Static Inverter Plant 400kV | 1500 | 1500 |
| Talcher - Kolar | LCC | 646 HVDC Talcher Converter Station 400kV | 486 HVDC Kolar Converter station 400kV | 2500 | 2010 |
| Mundra - Mahendragarh | LCC | 353 HVDC Mundra Converter Station 400kV | 424 HVDC Mahendragarh Converter Station 400kV | 2500 | 2006 |
| Champa - Kurukshetra | LCC | 10 Champa Converter Station 765kV | 433 Kurukshetra HVDC site 400kV | 6000 | 6000 |
| Raigarh - Pugalur | LCC | 12 Raigarh Converter Station 765kV | 1086 Pugalur HVDC Station 400kV | 6000 | 6000 |
| Pugalur - North Trichur | VSC | 1086 Pugalur HVDC Station 400kV | 518 Trichur HVDC Converter Station 400kV | 2000 | 2000 |
| Biswanath Chariali - Alipurduar | LCC | 229 Biswanath Charaili substation 400kV | 1214 Alipurduar Converter Station 400kV | 3000 | 600 |
| Alipurduar - Agra | LCC | 1214 Alipurduar Converter Station 400kV | 148 Agra 765kV | 6000 | 3008 |
| Ballia - Bhiwadi | LCC | 1133 Ballia Substation 400kV | 709 Bhiwadi Substation 400kV #2 | 2500 | 1002 |
| Chandrapur - Padghe | LCC | 531 Chandrapur HVDC Converter Station 400kV | 564 Padghe HVDC Converter Station 400kV | 1500 | 1404 |
| Lower Sileru - Barsoor | LCC | 1367 Sileru Static Inverter Plant 220kV | 1505 Barsoor Static Inverter Plant 220kV | 100 | 0 |
| Aarey - Kudus | VSC | 554 Kudus 400 KV SS 400kV | 2669 MH:w1187675513:220 220kV | 1000 | 1000 |
| Vindhyachal back-to-back | back-to-back | 632 Vindhyachal Pooling Station 400kV | 5314 Vindhyachal Pooling Station 400kV NR side | 500 | 250 |
| Bhadravati back-to-back | back-to-back | 526 Bhadravati B2B HVDC 400kV | 5315 Bhadravati B2B HVDC 400kV SR side | 1000 | 1000 |
| Vizag (Gazuwaka) back-to-back | back-to-back | 217 Vizag B2B HVDC Station 400kV | 5316 Vizag B2B HVDC Station 400kV ER side | 1000 | -856 |
| Pusauli (Sasaram) back-to-back | back-to-back | 254 Pusauli Back2Back HVDC 400kV | 5317 Pusauli Back2Back HVDC 400kV NR side | 500 | 500 |

## Repairs (every change made so the case solves)

- sourced 400/220 kV station missing from the OSM-built model added: Karjat 220 kV bus and 2 x 500 MVA ICT [CEA substation ledger ss_year_2022-03.pdf p3 sl53: 'Karjat S/S' 400/220 kV, MSETCL, JAN-22, 1000 MVA (round 9; units 2 x 500 MVA estimated from the total)] (estimated; rating attested)
- sourced 400/220 kV station missing from the OSM-built model added: Bongaigaon ICT between its separately mapped 400 and 220 kV yards 2 x 315 MVA ICT [CEA substation ledger ss_year_2020-01.pdf p1 sl8: 'Bongaigaon (2nd ICT) S/s.' 400/220 kV 315 MVA, APR-19 (round 10; ICT-1 taken as the same 315 MVA, estimated)] (estimated; rating attested)
- sourced LILO: one circuit of Bhigwan - Kurkumb (osm:220:w221640155:n2306724596) looped into MH:karjat:220: MH:bhigwan:220 - station 20.2 km, station - T:2306724673:220 23.8 km [CEA line ledger tl_year_2025-03.pdf row 72: 'LILO on 220kV Bhigwan Kurkumb line at 400kV Karjat s/s', 17 km D/C; one circuit looped at the point of the Bhigwan - T:2306724673 section nearest Karjat (0.32 of 10.0 km from Bhigwan) (round 9)] (estimated)
- open-ended line stubs removed (a line junction with a single line, i.e. an OSM line whose far end reaches no substation): 255 line sections, 6913 route km (synthetic)
- circuit counts from the CEA ledger where OSM has fewer (unambiguous one-hop length_ok matches, no LILO, no parallel OSM line): 6 lines (Mukatsar - Ghubaya 1 -> 2; Mukatsar - Abohar 1 -> 2; Aurangabad (PG) - Padghe (PG) line 1 -> 2; Mukatsar - Malout 1 -> 2; Kayathar - Tuticorin 1 -> 2; Sitapuram -Huzurnagar line 1 -> 2) (estimated)
- lines named by the CEA ledger and missing from OSM, added: North Karanpura - Gaya 400 kV D/C (North Karanpura TPP 400kV - Gaya 400kV, 98 km x2); Sirohi - Pindwara 220 kV (Sirohi 220kV - Pindwara 220kV, 23 km x1); Dindi - Kondamallepally 220 kV (Dindi 220kV - Kondamallepally Sub Station 220kV, 33 km x2); Jagalur (Hiremallanahole) - Chitradurga 220 kV (Jagaluru 220kV - Chitradurga Sub Station 220kV, 36 km x2) (estimated: published length, default conductor)
- OSM loose ends of lines the CEA ledger names, joined (round 8): Pulivendula - Mutyalacheruvu (join) (D:12252527382:220 220kV - Pulivendula Sub Station 220kV, 21.4 km x2); Sahupuri - Bhelupur (join) (D:6216564757:220 220kV - Bhelupur 220kV, 5.5 km x2); Tanda (NTPC) - Tanda (New) (join) (D:7203801384:220 220kV - NTPC Tanda 220kV, 6.1 km x2); Barabanki - Satrikh Road (join) (D:13624819159:220 220kV - Satrikh Road 220kV, 5.8 km x2); Raxaul (New) - Gopalganj (join) (D:13120218411:220 220kV - Gopalganj 220kV, 6.5 km x2); Babai - Bhiwani 400 kV (join) (D:12301435270:400 400kV - D:9247036553:400 400kV, 5.6 km x2); Madakkathara - Malaparamba (join) (D:3739713918:220 220kV - Madakkathara Substation 220kV, 0.5 km x2); Shapar - Babara (join) (D:10760154575:220 220kV - D:10760154576:220 220kV, 0.6 km x2); Jangaon - Devannapet (join) (D:12375730110:220 220kV - D:12832512443:220 220kV, 5 km x2); Botad - Chorania (join) (D:10784693654:220 220kV - Chorania 220kV, 4.6 km x2); Ghangapura (Nimbarga) - Sindagi (Aheri) (join) (D:14209357614:220 220kV - Aheri 220kV, 8.3 km x2) (estimated: ledger length less the OSM parts, default conductor)
- generators whose connection bus is not in this case re-attached to the nearest kept substation (400/765 kV for >= 500 MW): 89 (estimated)
- generators >= 500 MW listed on a 220 kV bus moved to the nearest 400/765 kV bus: 51 (estimated)
- generator step-up transformers: synchronous plant moved behind 635 lumped GSUs (386295 MVA in total), x 14.5 % on own rating, one generator bus per grid bus (estimated; CEA GT 14-15 %)
- slack: largest dispatched generator in the main island, Sasan UMPP (6x660MW) at Vindhyachal Pooling Station 765kV gen bus, reactive band widened to +/-23294 MVAr (synthetic)
- demand rows on buses outside this case moved to the nearest kept substation: 14 rows, 1215 MW (estimated)
- dispatch scaled by 1.2122 to meet the demand table (271643 MW) plus 3% losses; 15 units capped at 90 % of nameplate; dispatch now 279432 MW (was 231020 MW) (estimated)
- demand scaled by 0.9978 so total demand = dispatch x (1 - 0.03) = 271049 MW (balanced snapshot; the slack takes the exact losses)
- INFERRED (brief rule PHYSICS-INFERRED ELEMENTS, replaces the FITTED radial stand-in of r5-r10): 21 generic feeds, 25 circuits, 593.7 circuit-km, each from the nearest 220 kV bus with a transformer to a higher voltage into a radial subtree whose net import exceeds its single feeder's thermal rating; minimum circuits by the excess; listed in inferred_elements (MODEL_CARD)
- back-to-back HVDC stations split into two converter buses: 4 (Vindhyachal back-to-back: 1 line(s), Bhadravati back-to-back: 1 line(s), Vizag (Gazuwaka) back-to-back: 1 line(s), Pusauli (Sasaram) back-to-back: 1 line(s)); the far region's AC lines no longer bypass the converter (synthetic bus, estimated)
- sourced bus splits; only where a source names the sections): Jhatikara: Bamnoli/Dwarka section (bus 321, ICT 2 x 1500 MVA, lines moved 0), Mundka section (bus 5318, ICT 2 x 1500 MVA, lines moved 1) [CTU ISTS Interim Rolling Plan 2031-32 p. 37] (derived; sectionaliser taken as open, because CTU reports ICT N-1 loading per section)
- cross-border exchanges as boundary injections (estimated; capacities and landing points checked against Druk Green / CTU, round 4): Bhutan generator 1091 MW at Alipurduar subtation 400kV; Bhutan generator 561 MW at Binaguri 400kV; Bhutan generator 185 MW at Birpara 220kV; Bhutan generator 33 MW at Bongaigaon 220kV; Bangladesh load 1000 MW at Gorkana 400kV; Bangladesh load 160 MW at Surjamani Nagar 400kV
- ICTs at OSM sites with no voltage tag (layers inferred from lines only) and no CEA ledger ICT match removed as phantom couplings: 64 check; no ICT sat on a substation=transition site)
- yard ties between separately mapped yards of one station (<= 5 km, same station name, or a synthetic yard-tie repair) rated at the station's connected capacity instead of one line circuit: 113 ties, 69149 -> 230125 MVA (estimated)
- zero-dispatch converter plant (evening: solar) is a fixed zero injection, not a voltage controller: 1203 units, 201202 MVA set to role pq, Q 0 (estimated; inverters off at night)
- FITTED: dispatched converter plant (wind, synthetic RE fill) regulates its bus voltage (351 units) instead of the fixed power factor rule, because this case has no solution with converter plant at fixed power factor, nor with the CEA Grid Connectivity Regulations B2 size rule (measured rounds 5-10: collapse at 0.8906 (r6), 0.9495 (r9, after the ledger's Karjat 400/220 kV station cleared the Maharashtra pocket), 0.8889 (r10, Alipurduar 220 kV group once the ledger's Bongaigaon ICT meshes it); weak pockets Alipurduar, Sabour / Jamalpur BGCL, Chhatarpur, Telangana, Konkan; the 132 kV network and distribution compensation are not modelled
- fixed shunt reactors for 765 kV line charging: 70% of each line's charging, half at each end, 96783 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- fixed shunt reactors for 400 kV line charging: 50% of each line's charging, half at each end, 54890 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- line reactors named in the line table used as given on 86 lines, 13534 MVAr (not a repair: attested where the table says so); the blanket share skips those lines
- sourced STATCOMs / SVCs as zero-MW voltage-control units (role pv, published Q range): 16 devices, -7350 to +6000 MVAr (not a repair: CERC 2015 Annexure-XXXI / CTU; in-service status estimated)
- on-load tap changers on 512 ICTs (400/220 kV 417, 400/230 kV 5, 765/400 kV 90), each holding its LV bus inside the CEA 3.10.4 planning band (400 kV 0.97-1.03, 220 kV 0.92-1.09 pu); 765/400 kV +/-5.5 % in 0.5 % steps (POWERGRID 765 kV auto-transformer model specification Rev. 08 cl. 2.16), 400/220 kV +/-10 % in 1.25 % steps (CEA); estimated; 51 ICTs whose LV bus a generator / STATCOM / SVC regulates have none; GSUs have off-circuit taps (no OLTC)
- sourced bus reactors (CEA ledger / CTU text): 3 in this case, 2 switched in (960 MVAr) where the bus is above 1.02 pu before them, the rest available and out of service (not a repair)
- bus shunts placed where the snapshot still needs reactive support (10 passes of a Newton solve WITH the units' reactive limits, CEA 4.3(a) voltage limits): 6 reactors 2580 MVAr, 111 capacitors 12170 MVAr (synthetic; stands in for compensation, lines, ICTs or plant the model lacks)
- converter plant with zero dispatch in this snapshot (evening: solar) feeds no fault current: 1203 units, 171022 MW (converterFaultCurrentPu 0; estimated)

## Known gaps

- 61 line(s) join buses of different nominal kV (220 vs 230 kV in Tamil Nadu); per unit uses each bus's own base, so this is a small voltage offset, not an error
- Nepal exchange not modelled (monsoon export, dry-season import; direction for the evening snapshot unknown)
- Bhutan machines feed no fault current in this case (boundary injections behind 100-150 km of cross-border line; converterFaultCurrentPu 0)
- sourced compensation not in this case: Khavda 765 kV bus reactor: named substation not in this case; nearest 765 kV bus 31.9 km away (> 25 km); Khavda 420 kV bus reactor: named substation not in this case; nearest 400 kV bus 38.5 km away (> 25 km)
- Line impedances are per-km values x route length (official length where the line crosswalk matched, else OSM geometry x 1.03): 6558 of 6558 lines use CEA 2026 Annexure-II per-km values (131 with a published conductor, the rest the layer default: 765 kV Quad Bersimis, 400 kV Twin Moose, 220 kV Single Zebra). Minimum section length 0.50 km (220 sections floored, shorter yard and tee artefacts merged.
- Series compensation on 14 lines and line reactors on 86 lines, only where CERC Annexure-XXIV names them (no default compensation: CERC shows fixed series capacitors on only about one in five 400 kV lines over 250 km and on no 765 kV line); elsewhere a share of charging is cancelled at the line ends.
- Reactive compensation by origin: CERC-named line reactors -13534 MVAr; blanket line reactor share -151673 MVAr (synthetic); CEA Manual 2026 clause 5.4.2.1 load capacitors 0 MVAr (estimated rule); sourced bus reactors switched in -960 MVAr of -1290 available; 16 sourced STATCOMs / SVCs as zero-MW voltage-control units, -7350 to +6000 MVAr; auto-placed repair shunts -2580 MVAr reactors and +12170 MVAr capacitors (synthetic). GridSim v1 has no switched-shunt or FACTS element: switchable devices are fixed for this snapshot.
- ICTs are inferred where one OSM site carries two voltage layers: 563 banks, 297 with a CEA ledger MVA, the rest a default bank; impedance is CEA typical. Bus sections are not modelled: every OSM substation is one bus, while CTU runs several stations (the Delhi ring among them) with bus sectionalisers open for fault-level control, so our fault levels there are an upper bound.
- Synchronous plants sit behind 635 lumped generator step-up transformers (386296 MVA, CEA GT 14-15 %, 14.5 % used), one per grid bus; inverter plant connects straight to the bus.
- Generation: WRI GPPD (2021) and CTU connectivity rows reconciled to CEA installed capacity 30.09.2026 by fuel; 29.8% of MW is synthetic 'unplaced' capacity (state-connected renewables with no public plant register), spread over the state's buses.
- Demand: loads table scenario 'evening_peak_2026_27' (CEA LGBR 2026-27 state peaks x coincidence factor), scaled to the dispatch.
- HVDC: 16 links, sending converter = load, receiving converter = fixed generator (type hvdc, role pq); schedules from CTU ISTS Rolling Plan 2030-31 HVDC table, scenario 8 Winter Evening Peak (a 2030-31 study used as a 2026-27 proxy); 4 back-to-back stations split into two converter buses.
- Cross-border exchanges are boundary injections (capacities and landing points checked against Druk Green and CTU Interim Rolling Plan 2031-32 p. 113 in round 4; output share estimated): Bhutan generator 1091 MW at Alipurduar subtation 400kV; Bhutan generator 561 MW at Binaguri 400kV; Bhutan generator 185 MW at Birpara 220kV; Bhutan generator 33 MW at Bongaigaon 220kV; Bangladesh load 1000 MW at Gorkana 400kV; Bangladesh load 160 MW at Surjamani Nagar 400kV.
- Fault studies: 1203 converter units with zero output in this snapshot (evening solar) feed no fault current; every other unit feeds at its full rating whatever its dispatch (GridSim IEC 60909; synchronous X''d 0.20 pu default).
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
| (b) separately mapped yard of one station tied to its partner (<= 1.5 km) | synthetic | 33 | 42 |
| (c) 400/220 kV ICT to a 220 kV yard with no ICT (400 kV yard <= 2 km) | estimated | 1 | 1 |
| (d) plant switchyard line end joined to the nearest same-kV substation (<= 3 km) | estimated | 1 | 2 |

| Repair | Island bus | Target bus | km |
|---|---|---|---:|
| (a) | D:14306510325:765 | RJ:ajmer:765 | 3.53 |
| (a) | D:14276624198:765 | GJ:halvad:765 | 4.56 |
| (b) | KA:world wind:220 | KA:harti:220 | 0.09 |
| (b) | TG:warangal:220:w412026867 | TG:warangal:220:w168500527 | 0.13 |
| (b) | DL:w296222975:220 | DL:w423229313:220 | 0.14 |
| (b) | KA:shahabad:220:w248736761 | KA:shahabad:220:w248736764 | 0.17 |
| (b) | WB:w118506962:220 | WB:w118506961:220 | 0.17 |
| (b) | PB:w428212210:400 | PB:rajpura tpp:400 | 0.18 |
| (b) | AP:sileru static inverter plant:220 | AP:sileru:220 | 0.19 |
| (b) | MH:w295414211:220 | MH:pawas:220 | 0.19 |
| (b) | GJ:shapar:220:w1336647551 | GJ:shapar:220:w1157077530 | 0.28 |
| (b) | OD:w201428272:220 | OD:w201428238:220 | 0.36 |
| (b) | TN:w1167812747:220 | TN:thiruvarur:220:w341599770 | 0.37 |
| (b) | MH:ugml:220 | MH:bhuagon wardha ii s:220 | 0.39 |
| (b) | GJ:w316421342:220 | GJ:essar:220 | 0.39 |
| (b) | TN:w1431938940:230 | TN:kanarpatti:230 | 0.42 |
| (b) | RJ:w1143180462:220 | RJ:w1001700967:220 | 0.46 |
| (b) | RJ:w428002998:220 | RJ:ramgarh:220 | 0.50 |
| (b) | MH:lonand tss:220 | MH:lonand:220 | 0.67 |
| (b) | UK:mahuakheraganj:220 | UK:gama ccpp:220 | 0.70 |
| (b) | KA:exora:220 | KA:vikas tech park:220 | 0.79 |
| (b) | GJ:gothasn tss:220 | GJ:w1487729820:220 | 0.82 |
| (b) | MH:vilebhagad:220 | MH:msl:220:w516717579 | 0.91 |
| (b) | DH:w704305038:220 | DH:w704304097:220 | 0.95 |
| (b) | KL:info park:220 | KL:brahmapuram:220 | 1.06 |
| (b) | MH:lonand midc:220 | MH:sona alloy:220 | 1.08 |
| (b) | GJ:ukai:220 | GJ:ukai hydro:220 | 1.11 |
| (b) | MH:flagship:220 | MH:msetcl hinjewadi i:220 | 1.27 |
| (b) | GJ:un2 alfanar:220 | GJ:baranda suzlon:220 | 1.27 |
| (b) | TG:nagole:220 | TG:w1467558690:220 | 1.32 |
| (b) | MH:rly traction seawoods:220 | MH:nerul:220 | 1.33 |
| (b) | MH:inox:220 | MH:posco:220 | 1.34 |
| (b) | MH:borivalli tata:220 | MH:borivalli:220 | 1.43 |
| (b) | HR:dfcc:220 | HR:faridabad ccpp:220 | 1.46 |
| (b) | AP:mylavaram 3:220 | AP:mylavaram 4:220 | 1.46 |
| (c) | WB:durgapur steel thermal power:220 | WB:durgapur steel tps:400 | 1.16 |
| (d) | D:13314156609:220 | MH:w293597861:220 | 2.96 |

## Inference round india-spine-220-r13 (base india-stage-220-r11-pre, 2026-11-01)

Brief rule PHYSICS-INFERRED ELEMENTS: the smallest generic elements the solver shows must exist, evidence class 'inferred' (recorded as estimated, [VERIFY]); every one is listed in inferred_elements.json. Generic only: no facility or load is identified or located; demand stays aggregate at existing public substations. Validation data was not used to infer anything. Tool: a build step.

- Feeds: 21 (28 circuits / units, 476.01 circuit-km), each the minimum circuits from the nearest public bulk supply point that clears an N-0 overload above 115 % (or cuts its excess by a quarter), within the no-worsening rule below, no unit newly held at a reactive limit and at most 2 inferred circuits at any bus; overhead per-circuit class medians.
- Compensation: 0 sites, 0 MVAr capacitive / 0 MVAr inductive, replacing the generic repair (117 shunts, 12170 / 2580 MVAr); NOT inferred in this round: every compensation mode broke the no-worsening rule, so the generic repair is kept exactly as the base round placed it (mode 'repair kept').
- Taps: 0 transformers moved off 1.0 by the tap-changer loop (nr_check rule, target 1.0, deadband 0.02, step 0.0125); no tap pass may hold a unit at a reactive limit that the base round did not.
- No-worsening rule, one test at every stage and end to end: after every feed, tap move, compensation move or trim, and in the final case, every branch of the base round must be at or below max(100 %, its base-round loading + 1 point) (tolerance 1 point: an overloaded branch may rise at most 1 point, a branch at or below 100 % may cross 100 % by at most 1 point above its base); inferred feed circuits stay within their own rating.
- Units at a reactive limit: base round 241; held because generic repair shunts on generator terminal buses were moved to their public substation: 0 (a shortfall in those units' own reactive range, plant side behind the step-up transformer: data gap, not compensated; GSU = plant).

| metric | before | after |
|---|---:|---:|
| iterations | 17 | 15 |
| iterations_warm | 17 | 13 |
| loss_mw | 7149.927 | 7052.974 |
| vmin_pu | 0.900 | 0.902 |
| vmax_pu | 1.065 | 1.066 |
| angle_spread_deg | 88.821 | 87.617 |
| over_100 | 215 | 189 |
| over_120 | 100 | 83 |
| over_140 | 62 | 54 |
| auto_cap_mvar | 12170.000 | 12170.000 |
| auto_reactor_mvar | 2580.000 | 2580.000 |
| inferred_comp_mvar_abs | 0.000 | 0 |
| units_held_at_q_limit | 241 | 240 |
| cpf_lambda | 1.053 | 1.055 |
| physics_pass | True | True |

Worst after: 263.4 % ict:w288560138:400/220 (400/220/33  kV New Koyna 400kV - 400/220/33  kV New Koyna 220kV); 260.9 % ict:w242702027:400/220 (Warangal 400kV #2 - Warangal 220kV #2); 252.7 % ict:w372701897:400/220 (Moga 400kV - Moga 220kV #2)

Overloads of 100-115 % left as they are: possible real constraint (unconstrained snapshot dispatch; the operator would redispatch). No element is inferred for them:

- 115.0 % osm:220:w148851126:n1619115782 (Belmuri 220kV - Arambag 220kV)
- 114.9 % osm:400:w294201887:n2977616853 (400 KV Chakan MSETCL 400kV - Talegaon PG 400/220 KV ss 400kV)
- 114.7 % ict:w244894482:400/220 (Veltoor 400kV - Veltoor 220kV)
- 114.7 % osm:220:w221543085:n2304329805 (T:13605303201:220 220kV - T:2304329805:220 220kV)
- 114.3 % osm:220:w1206938756:n2507787397 (T:2507787397:220 220kV - Raidurg GIS Sub station 220kV)
- 113.4 % ict:w492327212:400/220 (Thervoi Kandigai 400kV - Thervoi Kandigai 220kV)
- 112.9 % osm:400:w360554644:n2060844115 (T:3353736994:400 400kV - T:2060844115:400 400kV)
- 112.9 % osm:220:w77011081:n1835811732 (Sarita Vihar 220kV - T:1835811848:220 220kV)
- 112.7 % ict:w140058348:400/220 (Amreli 400KV 400kV - Amreli 400KV 220kV)
- 112.7 % osm:220:w100592797:n1162987813 (Kanpur 220kV - T:1162987813:220 220kV)
- 112.3 % osm:400:w309120574:n3144623337 (Thirunelveli 400kV - T:3144623337:400 400kV)
- 112.0 % osm:220:w251260628:n2575077857 (Lingapura 220kV - KA:w254681372:220 220kV)
- 111.9 % ict:w563356617:400/220 (400/220 kV Talandge 400kV - 400/220 kV Talandge 220kV)
- 111.4 % osm:220:w242543817:n2500100415 (Nagarjunasagar PSP 220kV - Nagarjuna Sagar 220kV)
- 111.4 % osm:220:w116521274:n12424529664 (Dalkola (PGCL) 220kV - Malda (PGCL) 220kV)
- 110.9 % ict:w1207167077:400/220 (Kethireddypally Sub Station 400kV - Kethireddypally Sub Station 220kV)
- 110.9 % osm:220:w245008396:n2522709294 (Dhone Sub Station 220kV - Kambalapadu Sub Station 220kV)
- 110.8 % ict:w116541259:400/220 (Binaguri 400kV - Binaguri 220kV)
- 110.8 % ict:w1012903459:400/220 (Rasra 400kV - Rasra 220kV)
- 110.7 % ict:w465937306:400/220 (Maradam 400kV - Maradam 220kV)
- 110.7 % osm:220:w63724929:n788011534 (Najafgarh 220kV - Bamnauli Substation 220kV)
- 110.2 % osm:220:w166692105:n1119656352 (Gorakhpur (PGCIL) 220kV - Gorakhpur I 220kV)
- 109.5 % osm:400:w196678369:n12618926612 (Anpara TPS 400kV - Obra TPS 400kV)
- 109.4 % osm:220:w754330653:n313985884 (T:1067863961:220 220kV - Sarangapur 220kV #2)
- 109.3 % ict:w221914594:400/220 (Lonikand S/S 400kV - Lonikand S/S 220kV)
- 109.3 % inferred feed 19 (Vizag B2B HVDC Station 220kV - AP:w241951935:220 220kV)
- 109.2 % osm:220:w140460714:n2340963316 (Suva 220kV - Haldarwa 220kV)
- 109.1 % osm:220:w288560158:n2921120125 (400/220/33  kV New Koyna 220kV - T:2921120125:220 220kV)
- 108.6 % osm:220:w421287196:n4210675482 (Versova Recieving Station 220kV - MH:w1187675513:220 220kV)
- 108.2 % ict:w192715776:400/220 (Khandwa PGCIL 400kV - Khandwa PGCIL 220kV)
- 108.2 % ict:w294715960:400/220 (Jejuri II 400kV - Jejuri II 220kV)
- 108.2 % ict:w26651187:400/220 (Sarnath 400kV - Sarnath 220kV)
- 108.2 % osm:220:w256774614:n2624028794 (T:2624028794:220 220kV - Talaku Substation 220kV)
- 108.0 % ict:w475959658:400/220 (Chanditala New 400kV - Chanditala New 220kV)
- 107.9 % osm:220:w667122689:n12613651050 (220/132 kV GCR 220kV - 220/132/33 kV OCR Eklahare SS 220kV)
- 107.9 % osm:220:w466424150:n4612208118 (Bongulur Sub station 220kV - Maheshwaram 220kV)
- 107.9 % osm:220:w1362390422:n12613651043 (220/132 kV GCR 220kV - 220/132/33 kV OCR Eklahare SS 220kV)
- 107.6 % osm:220:w545883628:n1619115842 (Midnapur 220kV - Arambag 220kV)
- 107.5 % osm:220:w663883998:n6216564164 (Sahupuri 220kV - Raja Talab 220kV)
- 107.3 % osm:220:w370258402:n3739713918 (T:3739713921:220 220kV - D:3739713918:220 220kV)
- 107.2 % osm:220:w666907723:n4348040263 (T:4348040263:220 220kV - Chandrapur II 220kV)
- 107.2 % ledger:Madakkathara - Malaparamba (join) (D:3739713918:220 220kV - Madakkathara Substation 220kV)
- 107.1 % osm:220:w30786894:n2528649911 (Singaperumalkovil 220kV - TN:w775147277:220 220kV)
- 106.9 % osm:220:w149250649:n1622568050 (Rajarhat 220kV - Bantala CLC 220kV)
- 106.9 % osm:220:w1455651397:n13349485967 (220kV MTPS-B 220kV - Mejia TPS 220kV #2)
- 106.9 % osm:220:w1329624559:n12301655937 (T:12301655937:220 220kV - Jawaharpur TPP 220kV)
- 106.8 % ict:w323661901:400/220 (NTPL 400kV - NTPL 220kV)
- 106.7 % osm:220:w245697648:n2528449008 (Manali 220kV - T:2528449008:220 220kV)
- 106.5 % osm:220:w436970080:n4348040255 (220/33 kV Tadali s/s 220kV - T:4348040263:220 220kV)
- 106.5 % osm:220:w420141880:n2316539842:2 (Versova Recieving Station 220kV - T:2316539842:220 220kV)
- 106.5 % osm:220:w124786338:n2206223334 (T:3953610395:220 220kV - Gobindgarh 220kV)
- 106.3 % osm:220:w747799973:n2305719953 (Solapur II (Bale) 220kV - T:2972118869:220 220kV)
- 106.1 % osm:220:w139729659:n1531273114 (Bhesan 220kV - Jetpur 220kV)
- 106.0 % osm:220:w686857022:n1795120480 (T:1795120480:220 220kV - Kurukshetra HVDC site 220kV)
- 105.9 % osm:400:w195006855:n2060845318 (Vindhyanagar 400kV - T:3353736994:400 400kV)
- 105.7 % osm:220:w258703320:n1946026795 (HR:w125096281:220 220kV - Panipat TPS 220kV)
- 105.7 % osm:220:w124843069:n2206221838 (T:2206221838:220 220kV - Phagan Majra 220kV)
- 105.4 % osm:220:w436970080:n4348040255:2 (220/33 kV Tadali s/s 220kV - T:4348040263:220 220kV)
- 105.2 % osm:220:w245008429:n2522709312 (Dhone Sub Station 220kV - Somayajulapally Sub Station 220kV)
- 105.1 % osm:220:w372827005:n11755313539 (Alipurduar subtation 220kV - Bongaigaon 220kV)
- 104.9 % osm:220:w666907723:n4348040259 (T:4348040263:220 220kV - Chandrapur II 220kV)
- 104.8 % osm:220:w1192640277:n2836931685 (Vrishabavathi Valley Substation 220kV - Tataguni 220kV)
- 104.7 % osm:220:w140469210:n1538928575 (T:1538928575:220 220kV - T:2299848961:220 220kV)
- 104.3 % osm:220:w153242091:n1659498194:2 (Varahi 220kV - Heggunje 220kV)
- 104.2 % ict:w195174081:400/220 (Damoh PGCIL 400kV - Damoh PGCIL 220kV)
- 104.2 % osm:220:w521790757:n5083586404 (Chandrapura New 220kV - CTPS 220kV)
- 104.1 % osm:220:w124786312:n1387719410 (Ablowal 220kV - T:2206221838:220 220kV)
- 103.8 % osm:220:w202180613:n2502798455 (T:2502798455:220 220kV - T:2502798714:220 220kV)
- 103.6 % osm:220:w210540843:n2206221655 (Nabha 220kV - Phagan Majra 220kV)
- 103.1 % osm:220:w309056139:n4348041062 (Chhuri 220kV - Kotmi Kalan 220kV)
- 103.1 % osm:220:w220802620:n2298920112 (Babhleshwar I "MSETCL" 400 KV Sub-Station 220kV - T:2299040490:220 220kV)
- 103.1 % osm:220:w140460886:n1538892658 (Dhule 220kV - T:1538892658:220 220kV)
- 102.9 % osm:220:w294418881:n2980191748 (Boisar 220kV - Palghar 220kV)
- 102.9 % osm:220:w124121495:n1382300353 (Sahnewal 220kV - T:1382300539:220 220kV)
- 102.7 % osm:220:w1012903455:n3956848628 (T:3956848628:220 220kV - Rasra 220kV #2)
- 102.4 % ict:w411727660:400/220 (Samba 400kV - Samba 220kV)
- 102.4 % osm:220:w124658733:n1386806392 (Mansa 220kV - PB:w255035555:220 220kV)
- 102.3 % osm:220:w1458393551:n9804669663 (Latehar 220kV - Latehar 220kV #2)
- 101.8 % ict:w206009230:400/220 (Mejia TPS 400kV - Mejia TPS 220kV #2)
- 101.4 % osm:220:w577176492:n1067863961 (Jhusi 220kV - T:1067863961:220 220kV)
- 101.3 % osm:220:w607682796:n1620918419 (Chanditala New 220kV - Rishra 220kV)
- 101.1 % osm:220:w242167522:n2496871947 (TG:w242167536:220 220kV - BG Kothuru Sub Station 220kV)
- 101.1 % osm:220:w63724940:n1390790177 (Dwarka-III Sector-19 Substation 220kV - Dwarka Sec-5 Substation 220kV)
- 101.0 % osm:220:w202184603:n2121660074 (220kV Raipur 220kV - T:2121660248:220 220kV)
- 101.0 % osm:220:w484574332:n4773233180 (Sherpur 220kV - T:4773233180:220 220kV)
- 101.0 % osm:220:w484574332:n4773233180:2 (T:4773233180:220 220kV - Dehradun 220kV)
- 100.9 % ict:r9:karjat:400/220 (Karjat 400kV - Karjat 220kV)
- 100.9 % inferred feed 1 (Chanditala New 220kV - Howrah 220kV)
- 100.7 % osm:220:w124237069:n1383280778 (Khasa 220kV - Balachak 220kV)
- 100.7 % osm:400:w315823986:n4110498281 (Nannor 400kV - Kurnool 400kV)
- 100.7 % osm:220:w425758299:n4250657064 (Maithon PGCIL 220kV - Dumka 220kV)
- 100.5 % osm:220:w408924407:n2119555036 (Kaulewada 220kV - Tiroda TPP 220kV)
- 100.4 % osm:220:w118252458:n1330922757 (Durgapur Projects Limited Power Station 220kV - Bakreshwar TPS 220kV)
- 100.3 % osm:220:w220933715:n2301079398 (T:2977618116:220 220kV - Bhusawal 220kV)
- 100.2 % osm:400:w834039241:n7785766165 (Arasur - POWERGRID -KARUMPATHAMPATTI 400kV - Pugalur HVDC Station 400kV)
- 100.2 % osm:220:w466142887:n3146177073 (Tuticorin Auto 220kV - NTPL 220kV)

Inferred feeds:

- inferred feed 22: 220 kV line x2 N.P. Kunta 220kV - Chakrayapeta Sub Station 220kV 25.33 km; demanded by inferred feed 21 (N.P. Kunta 220kV - Chakrayapeta Sub Station 220kV) at 191.7 % (N-0 snapshot); after 80.4 %
- inferred feed 23: 220 kV line x2 Bihar Sharif (PGCIL) 220kV - Sheikpura-BGCL 220kV 16.42 km; demanded by inferred feed 18 (Bihar Sharif (PGCIL) 220kV - Sheikpura-BGCL 220kV) at 175.3 % (N-0 snapshot); after 71.1 %
- inferred feed 24: transformer unit x2 Subhasgram 400kV / Subhasgram 220kV #2; demanded by ict:w149255384:400/220 at 171.2 % (N-0 snapshot); after 92.3 %
- inferred feed 25: 220 kV line x1 New Simbhavali 220kV - Amroha 220kV 38.52 km; demanded by osm:220:w935472285:n1207419940 (Amroha 220kV - Moradabad 220kV) at 141.8 % (N-0 snapshot); after 83.8 %
- inferred feed 26: 220 kV line x1 Badnawar 220kV - Nagra 220kV 35.81 km; demanded by osm:220:w1499088167:n13535863241 (T:13727941638:220 220kV - Nagra 220kV) at 140.4 % (N-0 snapshot); after 90.9 %
- inferred feed 27: 220 kV line x2 Hindupur 220kV #2 - Gollapuram Sub Station 220kV 25.54 km; demanded by osm:220:w1331634699:n4030454777 (T:4030454777:220 220kV - Hindupur 220kV #2) at 138.3 % (N-0 snapshot); and osm:220:w1331634699:n4030454777 (T:4030454777:220 220kV - Hindupur 220kV #2) at 127.0 % -> 120.1 %; after 120.1 %
- inferred feed 28: 220 kV line x2 KSEB 400kV GIS Kottayam 220kV - Brahmapuram 220kV Substation 220kV 34.58 km; demanded by osm:220:w370027496:n2310341097 (Kochi East 220kV - Brahmapuram 220kV Substation 220kV) at 136.1 % (N-0 snapshot); after 93.0 %
- inferred feed 29: 220 kV line x2 Patna (PGCIL) 220kV - Fatuha 220kV 14.27 km; demanded by osm:220:w92994751:n1078009749 (Fatuha 220kV - T:1078013192:220 220kV) at 135.8 % (N-0 snapshot); after 68.8 %
- inferred feed 30: 220 kV line x1 Bhuj 765kV 220kV - Baranda Suzlon 220kV 28.54 km; demanded by osm:220:w1127651321:n10310014044 (Bhuj 765kV 220kV - T:10310014044:220 220kV) at 130.1 % (N-0 snapshot); after 81.3 %
- inferred feed 31: 220 kV line x1 Abdullahpur 220kV - Khera 220kV 5.61 km; demanded by inferred feed 6 (Abdullahpur 220kV - Khera 220kV) at 124.6 % (N-0 snapshot); after 67.6 %
- inferred feed 32: 220 kV line x1 Vijayawada TPS 220kV - AP:w242291940:220 220kV 0.61 km; demanded by osm:220:w308802829:n13061649061 (AP:w242291940:220 220kV - Vijayawada TPS 220kV) at 124.3 % (N-0 snapshot); after 72.6 %
- inferred feed 33: 220 kV line x1 NTPL 220kV - TuticorinTPS 220kV 1.1 km; demanded by osm:220:w466142895:n3146187719 (TuticorinTPS 220kV - NTPL 220kV) at 123.3 % (N-0 snapshot); after 86.1 %
- inferred feed 34: 220 kV line x1 Nannor 220kV - Brahmankotkur Sub Station 220kV 15.11 km; demanded by osm:220:w245008391:n3219562552 (Nannor 220kV - T:3219562552:220 220kV) at 121.2 % (N-0 snapshot); after 89.3 %
- inferred feed 35: transformer unit x1 Balipara 400kV / Balipara 220kV; demanded by ict:w203673991:400/220 at 119.8 % (N-0 snapshot); after 75.8 %
- inferred feed 36: 220 kV line x1 Dindi 220kV - Kalwakurthy Substation 220kV 20.73 km; demanded by osm:220:w243441955:n2508474672 (Dindi 220kV - Kalwakurthy Substation 220kV) at 119.8 % (N-0 snapshot); after 84.5 %
- inferred feed 37: transformer unit x1 Raigarh Converter Station 765kV / Raigarh Converter Station 400kV; demanded by ict:w311954709:765/400 at 119.5 % (N-0 snapshot); after 90.9 %
- inferred feed 38: 220 kV line x1 Alamathi Substation 220kV - Koyambedu Substation 220kV 18.23 km; demanded by osm:220:w342204853:n4112155172 (T:5848897162:220 220kV - T:4112155172:220 220kV) at 116.4 % (N-0 snapshot); after 98.2 %
- inferred feed 39: transformer unit x1 400/220  kV Akola 400kV / 400/220  kV Akola 220kV; demanded by ict:w221135443:400/220 at 116.3 % (N-0 snapshot); after 75.8 %
- inferred feed 40: transformer unit x1 Bhinmal 400kV / Bhinmal 220kV #2; demanded by ict:w193681211:400/220 at 116.1 % (N-0 snapshot); after 74.8 %
- inferred feed 41: 220 kV line x2 Kala 220kV - Dahanu TPP 220kV 35.34 km; demanded by osm:220:w420141880:n2316539842:2 (Versova Recieving Station 220kV - T:2316539842:220 220kV) at 116.0 % (N-0 snapshot); after 106.5 %
- inferred feed 42: 220 kV line x1 Mansar 220kV - Halvad 220kV 8.79 km; demanded by osm:220:w1144196657:n2187537081 (Mansar 220kV - Halvad 220kV) at 115.4 % (N-0 snapshot); after 77.1 %

Inferred compensation (largest 15; full list in inferred_elements.json):
