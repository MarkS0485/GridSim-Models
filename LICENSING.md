# Licensing of the models

The models are databases offered under the Open Database Licence (ODbL) 1.0 (see LICENCE) once each is cleared for public redistribution. Each model's own ATTRIBUTION.txt lists the credit every source requires; keep those credits in anything you publish. End users comply with each nation's data obligations where they use a model.

Every model is in one of three categories. Only category (a) is cleared for public redistribution today. Categories (b) and (c) are included so that each can be kept or removed as its licence question is settled; each of their MODEL_CARD.md, ATTRIBUTION.txt and BUILD_README.md files carries a RELEASE STATUS saying so. Remove a rejected model by deleting its folder and re-running the export (or by changing its category), never by editing files by hand.

## (a) Open: cleared for public redistribution

Every input is openly licensed and redistributable (ODbL, CC BY 4.0, CC BY-SA, NLOD, Open Government Licence, US public domain, or factual figures from operator publications reused with attribution).

| Grid | Folder | Sources and licences |
|---|---|---|
| Italy, mainland and Sicily | `models/italy-spine-380-220-150-r5` | OSM via PyPSA-Eur (ODbL), powerplantmatching / energy-charts / Eurostat / openpolis (CC BY 4.0), Terna monthly report facts (reuse with attribution), Natural Earth (PD). |
| Italy, Sardinia | `models/italy-spine-sardinia-380-220-150-r4` | As Italy mainland (same sources). |
| Iberian peninsula (Spain and Portugal) | `models/iberia-spine-400-220-132-r9` | OSM via PyPSA-Eur and Geofabrik (ODbL), powerplantmatching / energy-charts / Eurostat-GISCO (CC BY 4.0), Natural Earth (PD). |
| Finland | `models/finland-spine-400-220-110-r11` | OSM via PyPSA-Eur and Geofabrik (ODbL), powerplantmatching / energy-charts / Eurostat-GISCO / Svenska kraftnat (CC BY 4.0), Natural Earth (PD). SvK credit was missing from the case's ATTRIBUTION.txt; the export adds it. |
| Norway | `models/norway-spine-420-300-132-r7` | NVE registers (NLOD 1.0 / 2.0), energy-charts / GeoNames / geoBoundaries (CC BY 4.0), pandapower line types (BSD-3), Natural Earth (PD). |
| Ireland, all-island (Ireland and Northern Ireland) | `models/ireland-spine-400-275-220-110-r5` | OSM via PyPSA-Eur and Geofabrik (ODbL), powerplantmatching / energy-charts / GeoNames / GHSL / geoBoundaries (CC BY 4.0), Natural Earth (PD). EirGrid TYTFS (all rights reserved) NOT used. |
| Greece, interconnected system with Crete | `models/greece-spine-400-150-r4` | As Ireland (same batch and source types). |
| Bulgaria | `models/bulgaria-spine-400-220-r3` | As Ireland; Bulgarian regions from geoBoundaries (public domain). |
| Baltic states (Estonia, Latvia, Lithuania) | `models/baltics-spine-400-330-r3` | As Ireland; Estonian regions from geoBoundaries (ODbL, OSM-derived). |
| Western Balkans (Serbia, Bosnia and Herzegovina, Montenegro, North Macedonia, Albania, Kosovo) | `models/wbalkans-spine-400-220-r2` | As Ireland; Kosovo regions from geoBoundaries are CC BY-SA 2.0 (OSM-derived, share-alike; credited). |
| Texas (ERCOT interconnection, 60 Hz) | `models/ercot-spine-345-138-r3` | OSM Geofabrik Texas extract (ODbL), EIA-860M / EIA-930 / Census / TIGER (US public domain). No CEII; ERCOT planning cases never used. |

Note on line ratings: several models apply a seasonal overhead-line rating factor (for example x 1.047 at 380-400 kV and x 1.199 at 220 kV and below in winter). The factor is a summary statistic (a median of transmission operators' published winter / summer rating ratios, taken from the JAO Static Grid Model); no operator data is redistributed. Each model card states the factor and its basis.

## (b) Needs JAO consent: included, NOT cleared for public redistribution

These grids were built with line and rating data from the JAO Static Grid Model. Publishing them is redistribution, which JAO's terms allow only with JAO's written consent. Two routes: ask JAO for written consent, or replace them with open-data rebuilds (OpenStreetMap via PyPSA-Eur, as the Italy and Iberia models are built) until consent is given.

| Grid | Folder | Sources | What is needed |
|---|---|---|---|
| Germany | `models/germany-spine-380-220-r6` | JAO Core Static Grid Model (lines | JAO written consent for redistribution, or an open-data rebuild (PyPSA-Eur OSM route, as Iberia / Italy). |
| Netherlands | `models/netherlands-spine-380-220-r6` | JAO SGM + OSM. | JAO written consent, or an open-data rebuild. |
| France | `models/france-spine-400-225-r16` | JAO SGM + ODRE (Etalab open licence) + OSM. | JAO written consent, or an open-data rebuild (ODRE RTE line data is open: the strongest rebuild candidate). |
| Belgium | `models/belgium-spine-380-220-r5` | JAO SGM + OSM. | JAO written consent, or an open-data rebuild. |
| Austria | `models/austria-spine-380-220-r4` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Czechia | `models/czechia-spine-400-220-r3` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Poland | `models/poland-spine-400-220-r5` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Slovakia | `models/slovakia-spine-400-220-r4` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Hungary | `models/hungary-spine-400-220-r5` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Slovenia | `models/slovenia-spine-400-220-r3` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Croatia | `models/croatia-spine-400-220-r4` | JAO SGM + PyPSA-Eur OSM. | JAO written consent, or an open-data rebuild. |
| Romania | `models/romania-spine-400-220-r5` | JAO SGM + PyPSA-Eur OSM + GHSL. | JAO written consent, or an open-data rebuild. |

## (c) Check: included, NOT cleared for public redistribution until the item is settled

| Grid | Folder | Inputs | What is needed |
|---|---|---|---|
| Switzerland | `models/switzerland-spine-380-220-hv-r9` | Open sources plus the Swissgrid control-block balance (EnergieUebersichtCH-2026.xlsx), 1,417.4 MW 'other' at 222 buses. | Swissgrid workbook states no licence [VERIFY]. Confirm Swissgrid reuse terms or rebuild without the Swissgrid balance. (the build pipeline |
| Sweden | `models/sweden-spine-400-220-r8` | Open sources plus eSett zonal production / consumption and SvK flows (CC BY 4.0) for the snapshot balance. | eSett open-data terms of use [VERIFY]. Confirm eSett terms. (the build pipeline |
| Denmark DK1 (Jutland and Funen) | `models/denmark-dk1-spine-400-220-150-132-r6` | Open sources plus Energinet Energi Data Service. | Energi Data Service terms recorded as 'free reuse with source attribution [VERIFY]'. One confirmation of the service's licence moves DK1 and DK2 to open. |
| Denmark DK2 (Zealand) | `models/denmark-dk2-spine-400-220-132-r6` | As DK1. | As DK1 (Energi Data Service licence confirmation). |
| Australia, National Electricity Market (eastern states) | `models/australia-nem-spine-500-110-r14` | Geoscience Australia (CC BY 4.0), OSM (ODbL), ABS / GeoNames (CC BY 4.0), AEMO data, TNSP planning reports (Transgrid, Powerlink, Ausgrid). | AEMO copyright permissions recorded [VERIFY]; TNSP planning reports (incl. the Ausgrid feeder ratings used from r8) are copyright the TNSP, reuse terms [VERIFY]. Confirm AEMO terms; for the TNSP ratings either confirm reuse or ship a round built before them (r7 or earlier still uses AEMO). |
| Australia, Wholesale Electricity Market (south-west WA) | `models/australia-wem-spine-330-132-r5` | Geoscience Australia (CC BY 4.0), OSM (ODbL), AEMO WA SCADA data; seasonal factor derived from Ausgrid ratings. | AEMO copyright permissions [VERIFY] (same check as the NEM). |
| Japan east (50 Hz) | `models/japan-east-spine-500-66-r6` | OSM (ODbL), WRI GPPD / GeoNames (CC BY 4.0), utility area data (METI guidelines), OCCTO committee material. | Utility area data state no open licence and OCCTO material is 'research only' [VERIFY]. Also the known reactive-limit quirk (owner to handle within GridSim). Confirm reuse terms or rebuild on OSM + GPPD only. |
| Japan west (60 Hz) | `models/japan-west-spine-500-66-r6` | As Japan east. | As Japan east. |
| Canada, Quebec interconnection | `models/canada-quebec-spine-735-315-120-r3` | OSM (ODbL), NACEI (OGL Canada), Hydro-Quebec demand data. | Hydro-Quebec demand data is CC BY-NC (non-commercial); incompatible with free-of-restriction redistribution beside a commercially backed tool. Replace the HQ demand with an open source or obtain permission. |
| Canada, Ontario | `models/canada-ontario-spine-500-230-115-r2` | OSM (ODbL), NACEI (OGL Canada), IESO public reports (ieso.ca terms of use). | IESO reports are under website terms of use, not an open licence. Confirm IESO reuse terms. |
| Canada, Alberta and British Columbia | `models/canada-west-spine-500-240-138-r4` | OSM (ODbL), NACEI (OGL Canada), AESO and BC Hydro public data (website terms of use). | AESO and BC Hydro data are under website terms of use, not an open licence. Confirm reuse terms. |
| India, 765 / 400 kV | `models/india-spine-765-400-r10` | OSM (ODbL) plus CEA / CTU / CERC publications. | CEA, CTU and CERC publications state no licence; needs a licence review. The IITH 418-bus data must NEVER ship (the tool refuses any file mentioning it). |
| India, 765 / 400 / 220 kV | `models/india-spine-220-r13` | As India 765 / 400 kV. | As India 765 / 400 kV. |

Data from IITH (the 418-bus Indian network) is never included here in any form.
