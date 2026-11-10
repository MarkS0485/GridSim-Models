# GridSim Models

Public library of 36 national and regional transmission-grid snapshots for GridSim RC2.
Each case uses GridSim's v1 JSON format and includes per-element evidence and provenance.
The database licence is [ODbL 1.0](LICENCE). See [licensing and credits](LICENSING.md).

| Frequency | Cases | Buses per case |
|---|---:|---:|
| 50 Hz | 31 | 36-5,318 |
| 60 Hz | 5 | 843-5,771 |

Each case models one operating snapshot at general-purpose fidelity. The cases carry
the `UnvalidatedAtScale` label and are intended for demonstrations, teaching and
exploratory comparisons. Planning, operations and investment require validated studies.
The lowest listed voltage may be a generator terminal voltage behind a step-up transformer.

## Open a case

GridSim 2.1.000 or later can open any folder under `models/`. In the desktop app,
choose **File > Open case folder**. From the command line:

| Task | Command |
|---|---|
| AC power flow | `gridsim pf models/<case>` |
| Solve and check conservation laws | `gridsim physics-check models/<case>` |
| IEC 60909 fault levels | `gridsim iec60909 models/<case>` |

## Case files

| File | Contents |
|---|---|
| `system.json`, `buses.json`, `generation.json`, `demand.json` | Case settings, buses, generation and demand |
| `transmission.json`, `transformer.json`, `onloadtapchanger.json`, `boundaries.json` | Lines, transformers, tap controls and boundary exchanges |
| `geography.json` | Country outline and regions for the map view |
| `provenance.json`, `evidence_tags.json` | Source records and evidence classes |
| `MODEL_CARD.md`, `BUILD_README.md` | Snapshot, solve results, assumptions, sources and build history |
| `ATTRIBUTION.txt` | Source credits to retain when redistributing |

| Evidence class | Meaning |
|---|---|
| Attested | Recorded in a source |
| Derived | Calculated from recorded data |
| Estimated | Modelled from a proxy or engineering assumption |
| Synthetic | Added to represent behaviour or support the solve |

## Models

| Coverage | Folder under `models/` | Frequency | Buses | Voltage levels (kV) |
|---|---|---:|---:|---|
| [Australia, National Electricity Market (eastern states)](models/australia-nem-spine-500-110-r14/MODEL_CARD.md) | `australia-nem-spine-500-110-r14` | 50 Hz | 1,038 | 500 / 330 / 275 / 220 / 132 / 110 / 20 |
| [Australia, Wholesale Electricity Market (south-west WA)](models/australia-wem-spine-330-132-r5/MODEL_CARD.md) | `australia-wem-spine-330-132-r5` | 50 Hz | 188 | 330 / 220 / 132 / 20 |
| [Austria](models/austria-spine-380-220-r4/MODEL_CARD.md) | `austria-spine-380-220-r4` | 50 Hz | 189 | 380 / 220 / 110 / 21 |
| [Baltic states (Estonia, Latvia, Lithuania)](models/baltics-spine-400-330-r3/MODEL_CARD.md) | `baltics-spine-400-330-r3` | 50 Hz | 87 | 400 / 330 / 220 / 20 |
| [Belgium](models/belgium-spine-380-220-r5/MODEL_CARD.md) | `belgium-spine-380-220-r5` | 50 Hz | 165 | 380 / 220 / 110 / 21 |
| [Bulgaria](models/bulgaria-spine-400-220-r3/MODEL_CARD.md) | `bulgaria-spine-400-220-r3` | 50 Hz | 185 | 400 / 220 / 20 |
| [Canada, Alberta and British Columbia](models/canada-west-spine-500-240-138-r4/MODEL_CARD.md) | `canada-west-spine-500-240-138-r4` | 60 Hz | 1,371 | 500 / 345 / 230 / 161 / 138 / 13.8 |
| [Canada, Ontario](models/canada-ontario-spine-500-230-115-r2/MODEL_CARD.md) | `canada-ontario-spine-500-230-115-r2` | 60 Hz | 1,071 | 500 / 345 / 230 / 115 / 13.8 |
| [Canada, Quebec interconnection](models/canada-quebec-spine-735-315-120-r3/MODEL_CARD.md) | `canada-quebec-spine-735-315-120-r3` | 60 Hz | 843 | 735 / 315 / 230 / 161 / 115 / 13.8 |
| [Croatia](models/croatia-spine-400-220-r4/MODEL_CARD.md) | `croatia-spine-400-220-r4` | 50 Hz | 55 | 400 / 220 / 110 / 21 |
| [Czechia](models/czechia-spine-400-220-r3/MODEL_CARD.md) | `czechia-spine-400-220-r3` | 50 Hz | 120 | 400 / 220 / 110 / 21 |
| [Denmark DK1 (Jutland and Funen)](models/denmark-dk1-spine-400-220-150-132-r6/MODEL_CARD.md) | `denmark-dk1-spine-400-220-150-132-r6` | 50 Hz | 179 | 400 / 220 / 150 / 20 |
| [Denmark DK2 (Zealand)](models/denmark-dk2-spine-400-220-132-r6/MODEL_CARD.md) | `denmark-dk2-spine-400-220-132-r6` | 50 Hz | 153 | 400 / 220 / 150 / 132 / 20 |
| [Finland](models/finland-spine-400-220-110-r11/MODEL_CARD.md) | `finland-spine-400-220-110-r11` | 50 Hz | 1,391 | 400 / 220 / 110 / 20 |
| [France](models/france-spine-400-225-r16/MODEL_CARD.md) | `france-spine-400-225-r16` | 50 Hz | 2,128 | 400 / 225 / 63 / 21 |
| [Germany](models/germany-spine-380-220-r6/MODEL_CARD.md) | `germany-spine-380-220-r6` | 50 Hz | 986 | 380 / 220 / 110 / 21 |
| [Greece, interconnected system with Crete](models/greece-spine-400-150-r4/MODEL_CARD.md) | `greece-spine-400-150-r4` | 50 Hz | 450 | 400 / 150 / 20 |
| [Hungary](models/hungary-spine-400-220-r5/MODEL_CARD.md) | `hungary-spine-400-220-r5` | 50 Hz | 110 | 400 / 220 / 110 / 21 |
| [Iberian peninsula (Spain and Portugal)](models/iberia-spine-400-220-132-r9/MODEL_CARD.md) | `iberia-spine-400-220-132-r9` | 50 Hz | 3,688 | 400 / 220 / 150 / 132 / 110 / 20 |
| [India, 765 / 400 / 220 kV](models/india-spine-220-r13/MODEL_CARD.md) | `india-spine-220-r13` | 50 Hz | 5,318 | 765 / 400 / 230 / 220 / 21 |
| [India, 765 / 400 kV](models/india-spine-765-400-r10/MODEL_CARD.md) | `india-spine-765-400-r10` | 50 Hz | 1,657 | 765 / 400 / 21 |
| [Ireland, all-island (Ireland and Northern Ireland)](models/ireland-spine-400-275-220-110-r5/MODEL_CARD.md) | `ireland-spine-400-275-220-110-r5` | 50 Hz | 513 | 400 / 275 / 220 / 110 / 20 |
| [Italy, Sardinia](models/italy-spine-sardinia-380-220-150-r4/MODEL_CARD.md) | `italy-spine-sardinia-380-220-150-r4` | 50 Hz | 168 | 380 / 220 / 150 / 20 |
| [Italy, mainland and Sicily](models/italy-spine-380-220-150-r5/MODEL_CARD.md) | `italy-spine-380-220-150-r5` | 50 Hz | 5,006 | 380 / 220 / 150 / 132 / 20 |
| [Japan east (50 Hz)](models/japan-east-spine-500-66-r6/MODEL_CARD.md) | `japan-east-spine-500-66-r6` | 50 Hz | 4,551 | 500 / 275 / 220 / 154 / 66 / 20 |
| [Japan west (60 Hz)](models/japan-west-spine-500-66-r6/MODEL_CARD.md) | `japan-west-spine-500-66-r6` | 60 Hz | 3,611 | 500 / 275 / 220 / 187 / 154 / 110 / 77 / 66 / 20 |
| [Netherlands](models/netherlands-spine-380-220-r6/MODEL_CARD.md) | `netherlands-spine-380-220-r6` | 50 Hz | 138 | 380 / 220 / 150 / 21 |
| [Norway](models/norway-spine-420-300-132-r7/MODEL_CARD.md) | `norway-spine-420-300-132-r7` | 50 Hz | 1,349 | 420 / 300 / 220 / 132 / 110 / 13.8 |
| [Poland](models/poland-spine-400-220-r5/MODEL_CARD.md) | `poland-spine-400-220-r5` | 50 Hz | 375 | 400 / 220 / 110 / 21 |
| [Romania](models/romania-spine-400-220-r5/MODEL_CARD.md) | `romania-spine-400-220-r5` | 50 Hz | 260 | 400 / 220 / 110 / 21 |
| [Slovakia](models/slovakia-spine-400-220-r4/MODEL_CARD.md) | `slovakia-spine-400-220-r4` | 50 Hz | 83 | 400 / 220 / 110 / 21 |
| [Slovenia](models/slovenia-spine-400-220-r3/MODEL_CARD.md) | `slovenia-spine-400-220-r3` | 50 Hz | 36 | 400 / 220 / 110 / 21 |
| [Sweden](models/sweden-spine-400-220-r8/MODEL_CARD.md) | `sweden-spine-400-220-r8` | 50 Hz | 320 | 400 / 220 / 20 |
| [Switzerland](models/switzerland-spine-380-220-hv-r9/MODEL_CARD.md) | `switzerland-spine-380-220-hv-r9` | 50 Hz | 737 | 380 / 220 / 150 / 132 / 110 / 20 |
| [Texas (ERCOT interconnection, 60 Hz)](models/ercot-spine-345-138-r3/MODEL_CARD.md) | `ercot-spine-345-138-r3` | 60 Hz | 5,771 | 345 / 138 / 22 |
| [Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo)](models/wbalkans-spine-400-220-r2/MODEL_CARD.md) | `wbalkans-spine-400-220-r2` | 50 Hz | 198 | 400 / 220 / 20 |

## Verify a copy

Run `sha256sum -c MANIFEST.sha256` from the repository root. `MANIFEST.json` also
records file sizes, the solver build and each case's recorded solve results.

## Contribute

Cite a published source and update the evidence class for each changed value.
Include the case's power-flow result and document any assumptions.
