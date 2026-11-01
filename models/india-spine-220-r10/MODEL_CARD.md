# MODEL CARD: India transmission spine 765/400/220 kV (UnvalidatedAtScale)

**RELEASE STATUS: Included in the GridSim-Models repository PENDING a licence check of some of its inputs (see LICENSING.md); it is NOT cleared for public redistribution until that check is complete. General-purpose fidelity, never planning grade.**

**UnvalidatedAtScale.** This case has not been checked against official Indian study results. It is a fair approximation of the Indian transmission spine assembled from public data. Demand is low fidelity (an allocated snapshot, not metered). Impedances are typical values per voltage class, not the real conductors. Use it to learn and to explore, not to plan or operate.

## What it is

- Voltage layers: 765, 400, 220 kV, one synchronous grid (India), largest electrical island kept.
- Built from the `model` tables.
- Buses 5318 (1044 are line junctions: OSM tee points and line ends), branches 7736 (lines 6537, transformers 1199), generators 2651.
- Buses by kV: 765 kV 172, 400 kV 1078, 230 kV 52, 220 kV 3381, 21 kV 635.
- Snapshot: Indian evening peak, no solar. Dispatch 279432 MW; net demand in demand.json 301345 MW (includes the HVDC sending converters and any cross-border export below).
- Slack: bus 4696 (1 reference: Sasan UMPP (6x660MW)).
- Islands before selection: 317; dropped 316 islands, 479 buses (322 of them substations); 91.1% of selected buses are in the kept island.

## Evidence class shares

| Element | Count | attested | derived | estimated | synthetic |
|---|---:|---:|---:|---:|---:|
| Buses | 5318 | 0 (0.0%) | 1 (0.0%) | 5313 (99.9%) | 4 (0.1%) |
| Branches | 7736 | 0 (0.0%) | 129 (1.7%) | 7574 (97.9%) | 33 (0.4%) |
| Generators | 2686 | 426 (15.9%) | 0 (0.0%) | 1472 (54.8%) | 788 (29.3%) |
| Demand points | 2771 | 0 (0.0%) | 0 (0.0%) | 2674 (96.5%) | 97 (3.5%) |
| Shunt buses | 1416 | 1 (0.1%) | 0 (0.0%) | 0 (0.0%) | 1415 (99.9%) |

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
- FITTED (synthetic stand-in for feeds OSM does not map replacement): radial subtrees whose net import (demand minus generation dispatched inside them) exceeds 100 % of the single feeding branch's thermal rating: 30 subtrees, 2164 MW of demand moved to the bus where each chain meets the mesh (no tuned share; rounds 1-4 used 60 % of the rating on demand only and moved 10,401 MW)
- back-to-back HVDC stations split into two converter buses: 4 (Vindhyachal back-to-back: 1 line(s), Bhadravati back-to-back: 1 line(s), Vizag (Gazuwaka) back-to-back: 1 line(s), Pusauli (Sasaram) back-to-back: 1 line(s)); the far region's AC lines no longer bypass the converter (synthetic bus, estimated)
- sourced bus splits; only where a source names the sections): Jhatikara: Bamnoli/Dwarka section (bus 321, ICT 2 x 1500 MVA, lines moved 0), Mundka section (bus 5318, ICT 2 x 1500 MVA, lines moved 1) [CTU ISTS Interim Rolling Plan 2031-32 p. 37] (derived; sectionaliser taken as open, because CTU reports ICT N-1 loading per section)
- cross-border exchanges as boundary injections (estimated; capacities and landing points checked against Druk Green / CTU, round 4): Bhutan generator 1091 MW at Alipurduar subtation 400kV; Bhutan generator 561 MW at Binaguri 400kV; Bhutan generator 185 MW at Birpara 220kV; Bhutan generator 33 MW at Bongaigaon 220kV; Bangladesh load 1000 MW at Gorkana 400kV; Bangladesh load 160 MW at Surjamani Nagar 400kV
- ICTs at OSM sites with no voltage tag (layers inferred from lines only) and no CEA ledger ICT match removed as phantom couplings: 64 check; no ICT sat on a substation=transition site)
- yard ties between separately mapped yards of one station (<= 5 km, same station name, or a synthetic yard-tie repair) rated at the station's connected capacity instead of one line circuit: 112 ties, 68940 -> 229706 MVA (estimated)
- zero-dispatch converter plant (evening: solar) is a fixed zero injection, not a voltage controller: 1203 units, 201202 MVA set to role pq, Q 0 (estimated; inverters off at night)
- FITTED: dispatched converter plant (wind, synthetic RE fill) regulates its bus voltage (351 units) instead of the fixed power factor rule, because this case has no solution with converter plant at fixed power factor, nor with the CEA Grid Connectivity Regulations B2 size rule (measured rounds 5 and 6: collapse at 0.8906 of the snapshot in the Maharashtra 220 kV pocket Bhigwan / Baramati / Phaltan / Lonand and at Sabour, Konkan, Alipurduar; the 132 kV network and distribution compensation are not modelled
- fixed shunt reactors for 765 kV line charging: 70% of each line's charging, half at each end, 96783 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- fixed shunt reactors for 400 kV line charging: 50% of each line's charging, half at each end, 54890 MVAr in total (synthetic; CEA/CTU practice compensates long EHV lines with line reactors)
- line reactors named in the line table used as given on 86 lines, 13534 MVAr (not a repair: attested where the table says so); the blanket share skips those lines
- sourced STATCOMs / SVCs as zero-MW voltage-control units (role pv, published Q range): 16 devices, -7350 to +6000 MVAr (not a repair: CERC 2015 Annexure-XXXI / CTU; in-service status estimated)
- on-load tap changers on 512 ICTs (400/220 kV 417, 400/230 kV 5, 765/400 kV 90), each holding its LV bus inside the CEA 3.10.4 planning band (400 kV 0.97-1.03, 220 kV 0.92-1.09 pu); 765/400 kV +/-5.5 % in 0.5 % steps (POWERGRID 765 kV auto-transformer model specification Rev. 08 cl. 2.16), 400/220 kV +/-10 % in 1.25 % steps (CEA); estimated; 51 ICTs whose LV bus a generator / STATCOM / SVC regulates have none; GSUs have off-circuit taps (no OLTC)
- sourced bus reactors (CEA ledger / CTU text): 3 in this case, 2 switched in (960 MVAr) where the bus is above 1.02 pu before them, the rest available and out of service (not a repair)
- bus shunts placed where the snapshot still needs reactive support (12 passes of a Newton solve WITH the units' reactive limits, CEA 4.3(a) voltage limits): 20 reactors 6740 MVAr, 193 capacitors 33940 MVAr (synthetic; stands in for compensation, lines, ICTs or plant the model lacks)
- converter plant with zero dispatch in this snapshot (evening: solar) feeds no fault current: 1203 units, 171022 MW (converterFaultCurrentPu 0; estimated)

## Known gaps

- 61 line(s) join buses of different nominal kV (220 vs 230 kV in Tamil Nadu); per unit uses each bus's own base, so this is a small voltage offset, not an error
- Nepal exchange not modelled (monsoon export, dry-season import; direction for the evening snapshot unknown)
- Bhutan machines feed no fault current in this case (boundary injections behind 100-150 km of cross-border line; converterFaultCurrentPu 0)
- sourced compensation not in this case: Khavda 765 kV bus reactor: named substation not in this case; nearest 765 kV bus 31.9 km away (> 25 km); Khavda 420 kV bus reactor: named substation not in this case; nearest 400 kV bus 38.5 km away (> 25 km)
- Line impedances are per-km values x route length (official length where the line crosswalk matched, else OSM geometry x 1.03): 6537 of 6537 lines use CEA 2026 Annexure-II per-km values (131 with a published conductor, the rest the layer default: 765 kV Quad Bersimis, 400 kV Twin Moose, 220 kV Single Zebra). Minimum section length 0.50 km (220 sections floored, shorter yard and tee artefacts merged.
- Series compensation on 14 lines and line reactors on 86 lines, only where CERC Annexure-XXIV names them (no default compensation: CERC shows fixed series capacitors on only about one in five 400 kV lines over 250 km and on no 765 kV line); elsewhere a share of charging is cancelled at the line ends.
- Reactive compensation by origin: CERC-named line reactors -13534 MVAr; blanket line reactor share -151673 MVAr (synthetic); CEA Manual 2026 clause 5.4.2.1 load capacitors 0 MVAr (estimated rule); sourced bus reactors switched in -960 MVAr of -1290 available; 16 sourced STATCOMs / SVCs as zero-MW voltage-control units, -7350 to +6000 MVAr; auto-placed repair shunts -6740 MVAr reactors and +33940 MVAr capacitors (synthetic). GridSim v1 has no switched-shunt or FACTS element: switchable devices are fixed for this snapshot.
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

## Solve record (gridsim.exe 2.1.000)

```
$ gridsim --version
gridsim 2.1.000+f85f6e7390bb45962af1753dea399ffcdc6c333f
$ gridsim pf india-spine-220-r10   (flat start: vm 1, vaDeg 0; exit 0, 3.7 s)
Power flow - India transmission spine 765/400/220 kV (UnvalidatedAtScale) (5318 buses)
  converged in 13 iteration(s), mismatch 5.94E-011 pu   losses 7141.449 MW / -63296.439 MVAr
  voltage range 0.8994 - 1.0528 pu
  lowest voltages:
      bus 2817   0.8994 pu    -39.511 deg
      bus 4611   0.9000 pu    -52.284 deg
      bus 1276   0.9010 pu    -37.712 deg
      bus 1346   0.9016 pu    -37.629 deg
      bus 4062   0.9028 pu    -40.551 deg
      bus 4406   0.9035 pu    -43.898 deg
      bus 4610   0.9043 pu    -51.660 deg
      bus 2699   0.9043 pu    -30.265 deg
      bus 4609   0.9046 pu    -51.617 deg
      bus 1266   0.9052 pu    -37.162 deg
      bus 4044   0.9076 pu    -39.254 deg
      bus 2587   0.9093 pu    -28.240 deg
(warm start baked into buses.json from that solve: flat start took 13 Newton iterations)
$ gridsim pf india-spine-220-r10 (warm start)   (exit 0, 2.8 s)
Power flow - India transmission spine 765/400/220 kV (UnvalidatedAtScale) (5318 buses)
  converged in 11 iteration(s), mismatch 6.97E-011 pu   losses 7141.449 MW / -63296.439 MVAr
  voltage range 0.8994 - 1.0528 pu
  lowest voltages:
      bus 2817   0.8994 pu    -39.511 deg
      bus 4611   0.9000 pu    -52.284 deg
      bus 1276   0.9010 pu    -37.712 deg
      bus 1346   0.9016 pu    -37.629 deg
      bus 4062   0.9028 pu    -40.551 deg
      bus 4406   0.9035 pu    -43.898 deg
      bus 4610   0.9043 pu    -51.660 deg
      bus 2699   0.9043 pu    -30.265 deg
      bus 4609   0.9046 pu    -51.617 deg
      bus 1266   0.9052 pu    -37.162 deg
      bus 4044   0.9076 pu    -39.254 deg
      bus 2587   0.9093 pu    -28.240 deg
$ gridsim physics-check india-spine-220-r10 (warm start)   (exit 0, 2.9 s)
Physics-law audit  -  india-spine-220-r10  (5318 buses, converged=True, tol 1.0E-006 MVA = BaseMva 100 x 1e-8)
| # | law | status | residual | unit | detail |
|---|-----|--------|----------|------|--------|
| 1 | Conservation of energy | Holds | 3.33E-010 | MW | independent dissipation 7141.448543 MW (branch 7141.4485 + shunt -0.0000) vs reported loss 7141.448543 MW |
| 2 | Ohm's law | Holds | 3.37E-010 | MVA | independent per-branch flow vs solver-reported line flow |
| 3 | Joule heating | Holds | 1.23E-009 | MW | total network loss 7141.448543 MW vs reported 7141.448543 MW |
| 4 | Faraday induction | Constitutive | - | - | embodied in transformer tap ratio and generator EMF E' = V + jX'I; no field model to check |
| 5 | Ampere's law (passivity) | Constitutive | 0.00E+000 | MW | series reactance X embodies the lumped inductance; all branches passive (I^2 R >= 0) |
| 6 | Kirchhoff's current law | Holds | 1.50E-009 | MW | network real injection vs specified, at constrained buses |
| 7 | Kirchhoff's voltage law | Holds | 0.00E+000 | V | structural: nodal voltages are single-valued potentials, so every loop sum vanishes identically |
| 8 | Complex power S = V I* | Holds | 7.44E-009 | MVA | same residual as law 6, reactive component included at 4536 PQ bus(es), by the bus types the solve ended with; 131 of them declared PV and solved as PQ (131 held at a reactive limit and checked against that limit, 0 with no generator) |
| 9 | AC phase & frequency synchronism | NotApplicable | - | Hz | NOT SCORED: steady-state snapshot at 50 Hz with no trajectory; law 9 is scored only when a dynamics caller supplies a SynchronismSample: stability --clear (classical or --rms) scores it from its own run, no steady-state verb or export does |
| 10 | Gauss's law / Coulomb | NotModeled | - | - | field/geometry law outside a positive-sequence phasor model; not represented |

GATE: PASS  -  state is physically admissible (all hard laws hold).
```
