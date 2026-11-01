# GridSim-Models

Free, openly licensed power-system network models of national and regional transmission grids, ready to load in
GridSim. Every model is built to one case format, carries an evidence class on
every value and a provenance record for every source, and solves with GridSim's bit-identical power flow, so
differences between grids are properties of the grids, not of the tools.

The models are shared in full for anyone to use, free of commercial consideration, under the Open Database Licence
(ODbL) 1.0 (see LICENCE). GridSim itself is a separate, commercially backed tool; this repository is not covered by
GridSim's licence.

Licence status: each model is in one of three categories, listed in LICENSING.md and in the table below. Only
category (a), open, is cleared for public redistribution today. Models in (b), needing JAO's written consent, and
(c), with an input whose terms are still being checked, are included so each can be kept or removed as its question
is settled; their MODEL_CARD.md, ATTRIBUTION.txt and BUILD_README.md each carry a RELEASE STATUS saying so.

## What these models are, and are not

- **UnvalidatedAtScale.** Every case name carries this tag. No model has been validated against official studies,
  operator base cases or measured events. Each is a solvable approximation for one snapshot hour.
- **General-purpose fidelity, never planning grade.** This is a deliberate ceiling. The models are assembled from
  published open data: topology from OpenStreetMap or open national registers, standard line and transformer
  parameters by voltage class, register-based generation, population-allocated demand, and the snapshot hour's
  published generation and cross-border flows. Reactive compensation is not published anywhere, so the bus shunts
  that let each case solve are labelled synthetic. Use the models to learn, compare, teach and explore; never to plan,
  operate or invest.
- **A starting point.** Each model is a base others can extend with better data. Every assumption is listed so it
  can be replaced.

## What is in each model folder

`models/<case>/` is a standard GridSim v1 JSON case folder:

| File | What it holds |
|---|---|
| `system.json`, `buses.json`, `generation.json`, `demand.json`, `transmission.json`, `transformer.json`, `onloadtapchanger.json`, `boundaries.json` | The network GridSim solves (buses carry the solved voltages as the start point) |
| `geography.json` | Country outline and first-level regions for GridSim's map view (format `gda-geography/1`, GridSim's geography format) |
| `MODEL_CARD.md` | What the model is: snapshot, counts, dispatch, repairs, fitted and assumed values, known gaps, sources, solve record |
| `BUILD_README.md` | How it was built: every source (URL, date, SHA-256, licence), the licences, the round-by-round history with exact numbers, the assumptions register and the gaps |
| `ATTRIBUTION.txt` | The credits every source requires. Keep them in anything you publish |
| `provenance.json`, `evidence_tags.json` | Per-element source and evidence class (attested, derived, estimated, synthetic) |

`MANIFEST.sha256` (repository root) lists the SHA-256 of every file; `MANIFEST.json` adds sizes and each model's
solve summary. Check a copy with `sha256sum -c MANIFEST.sha256`.

## How GridSim loads a model

Any GridSim 2.1.000 or later reads a model folder as a JSON case:

```
gridsim pf models/<case>              # one AC power flow
gridsim physics-check models/<case>   # solve and audit the conservation laws
gridsim iec60909 models/<case>        # fault levels
```

In the desktop app, use File > Open case folder... and pick a model folder. GridSim plans to link this repository
as a git submodule for RC2 (proposed mount point `data/models`), so that the app's model picker can list the models
directly. GridSim never needs this repository to build, test or run, and reads the models as ordinary input through
its normal loaders. Bundled, signed models are planned to be exempt from GridSim's licence-tier bus limits; that is a
GridSim change made in GridSim's own release, not something this repository can grant.

## Models

Coverage and voltage depth (the table is written by the export step; every model converges with GridSim's power flow
and the cleaned files re-solve bit-identically to the originals; the lowest voltage listed, 13.8 to 22 kV, is the
generator terminal level behind the modelled step-up transformers, not a distribution network):

<!-- MODELS-TABLE-START (written by the export tool) -->
| Folder (models/...) | Coverage | Frequency | Buses | Voltage levels (kV) | Licence status |
|---|---|---:|---:|---|---|
| `australia-nem-spine-500-110-r9` | Australia, National Electricity Market (eastern states) | 50 Hz | 1,038 | 500 / 330 / 275 / 220 / 132 / 110 / 20 | (c) check |
| `australia-wem-spine-330-132-r2` | Australia, Wholesale Electricity Market (south-west WA) | 50 Hz | 188 | 330 / 220 / 132 / 20 | (c) check |
| `austria-spine-380-220-r4` | Austria | 50 Hz | 189 | 380 / 220 / 110 / 21 | (b) needs JAO consent |
| `baltics-spine-400-330-r3` | Baltic states (Estonia, Latvia, Lithuania) | 50 Hz | 87 | 400 / 330 / 220 / 20 | (a) open |
| `belgium-spine-380-220-r5` | Belgium | 50 Hz | 165 | 380 / 220 / 110 / 21 | (b) needs JAO consent |
| `bulgaria-spine-400-220-r3` | Bulgaria | 50 Hz | 185 | 400 / 220 / 20 | (a) open |
| `canada-west-spine-500-240-138-r4` | Canada, Alberta and British Columbia | 60 Hz | 1,371 | 500 / 345 / 230 / 161 / 138 / 13.8 | (c) check |
| `canada-ontario-spine-500-230-115-r2` | Canada, Ontario | 60 Hz | 1,071 | 500 / 345 / 230 / 115 / 13.8 | (c) check |
| `canada-quebec-spine-735-315-120-r3` | Canada, Quebec interconnection | 60 Hz | 843 | 735 / 315 / 230 / 161 / 115 / 13.8 | (c) check |
| `croatia-spine-400-220-r4` | Croatia | 50 Hz | 55 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `czechia-spine-400-220-r3` | Czechia | 50 Hz | 120 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `denmark-dk1-spine-400-220-150-132-r4` | Denmark DK1 (Jutland and Funen) | 50 Hz | 179 | 400 / 220 / 150 / 20 | (c) check |
| `denmark-dk2-spine-400-220-132-r4` | Denmark DK2 (Zealand) | 50 Hz | 153 | 400 / 220 / 150 / 132 / 20 | (c) check |
| `finland-spine-400-220-110-r6` | Finland | 50 Hz | 1,391 | 400 / 220 / 110 / 20 | (a) open |
| `france-spine-400-225-r10` | France | 50 Hz | 1,781 | 400 / 225 / 63 / 21 | (b) needs JAO consent |
| `germany-spine-380-220-r6` | Germany | 50 Hz | 986 | 380 / 220 / 110 / 21 | (b) needs JAO consent |
| `greece-spine-400-150-r4` | Greece, interconnected system with Crete | 50 Hz | 450 | 400 / 150 / 20 | (a) open |
| `hungary-spine-400-220-r5` | Hungary | 50 Hz | 110 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `iberia-spine-400-220-132-r8` | Iberian peninsula (Spain and Portugal) | 50 Hz | 3,688 | 400 / 220 / 150 / 132 / 110 / 20 | (a) open |
| `india-spine-220-r10` | India, 765 / 400 / 220 kV | 50 Hz | 5,318 | 765 / 400 / 230 / 220 / 21 | (c) check |
| `india-spine-765-400-r8` | India, 765 / 400 kV | 50 Hz | 1,657 | 765 / 400 / 21 | (c) check |
| `ireland-spine-400-275-220-110-r5` | Ireland, all-island (Ireland and Northern Ireland) | 50 Hz | 513 | 400 / 275 / 220 / 110 / 20 | (a) open |
| `italy-spine-sardinia-380-220-150-r1` | Italy, Sardinia | 50 Hz | 168 | 380 / 220 / 150 / 20 | (a) open |
| `italy-spine-380-220-150-r5` | Italy, mainland and Sicily | 50 Hz | 5,006 | 380 / 220 / 150 / 132 / 20 | (a) open |
| `japan-east-spine-500-66-r5` | Japan east (50 Hz) | 50 Hz | 4,551 | 500 / 275 / 220 / 154 / 66 / 20 | (c) check |
| `japan-west-spine-500-66-r4` | Japan west (60 Hz) | 60 Hz | 3,611 | 500 / 275 / 220 / 187 / 154 / 110 / 77 / 66 / 20 | (c) check |
| `netherlands-spine-380-220-r4` | Netherlands | 50 Hz | 138 | 380 / 220 / 150 / 21 | (b) needs JAO consent |
| `norway-spine-420-300-132-r6` | Norway | 50 Hz | 1,349 | 420 / 300 / 220 / 132 / 110 / 13.8 | (a) open |
| `poland-spine-400-220-r5` | Poland | 50 Hz | 375 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `romania-spine-400-220-r5` | Romania | 50 Hz | 260 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `slovakia-spine-400-220-r4` | Slovakia | 50 Hz | 83 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `slovenia-spine-400-220-r3` | Slovenia | 50 Hz | 36 | 400 / 220 / 110 / 21 | (b) needs JAO consent |
| `sweden-spine-400-220-r5` | Sweden | 50 Hz | 320 | 400 / 220 / 20 | (c) check |
| `switzerland-spine-380-220-hv-r6` | Switzerland | 50 Hz | 737 | 380 / 220 / 150 / 132 / 110 / 20 | (c) check |
| `ercot-spine-345-138-r3` | Texas (ERCOT interconnection, 60 Hz) | 60 Hz | 5,771 | 345 / 138 / 22 | (a) open |
| `wbalkans-spine-400-220-r2` | Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) | 50 Hz | 198 | 400 / 220 / 20 | (a) open |
<!-- MODELS-TABLE-END -->

LICENSING.md lists every grid, the licence position of each, and what must happen before a model in category (b) or
(c) is cleared for public redistribution.

## Licence and credits

- The models: ODbL 1.0 (LICENCE). Share-alike applies to derived databases.
- The credits: each model's ATTRIBUTION.txt.
- Your obligations: you comply with each source's terms and each nation's data obligations where you use a model.

## Contributing better data

Improvements are welcome when they cite a published source: an operator's line parameters, a published rating table,
a substation layout, a compensation register. Every changed value needs its source and evidence class, and the case
must still solve. A value changed only because it makes the solver converge is not an improvement.
