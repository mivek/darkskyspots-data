# Darkspots database attribution

Assessment date: **2026-11-04**. Responsible maintainer: **[@mivek](https://github.com/mivek)**.

The Darkspots spot database and derived cluster databases are distributed under
[Open Database License 1.0](https://opendatacommons.org/licenses/odbl/1-0/)
(`ODbL-1.0`; see [LICENSE](LICENSE)). This is a conservative maintainer decision,
not a conclusive finding that upstream OSM rights legally require this
classification, and not an independently certified legal opinion.

**ODbL applies to the Darkspots database, not as a relicensing of upstream raster
or vector datasets or their individual contents.** Retain the following source
credits and applicable content rights when redistributing the database. Upstream
providers do not endorse Darkspots.

## NASA Black Marble and lightpollutionmap.info

NASA's Black Marble nighttime lights product: **VJ146A4**, NOAA-20/JPSS-1,
yearly 2025, **Collection 2**, `AllAngle_Composite_Snow_Free` subset as identified
by the distributor's documentation. Credit: **Jurij Stare, www.lightpollutionmap.info**,
and **NASA's Black Marble nighttime lights product**.

- [NASA product description](https://ladsweb.modaps.eosdis.nasa.gov/missions-and-measurements/products/VJ146A4)
- [NASA LAADS data-use and citation policy](https://ladsweb.modaps.eosdis.nasa.gov/learn/)
- [lightpollutionmap.info documentation](https://www.lightpollutionmap.info/help.html),
  especially FAQ 14 (credits), 18 (raw Float32 data), 29 (rendered maps) and 30 (raw maps).

NASA LAADS describes its data products as not copyrighted, with unrestricted
subsequent use and redistribution, and requests citation. The distributor
describes the NASA raw products as CC0 and requests the credits above. This
assessment relies on the NASA policy and the documented raw-data redistribution;
it does not assign CC0 to every layer, image or service on lightpollutionmap.info.

The maintainer confirmed that the retained GeoTIFFs came from lightpollutionmap.info.
They are single-band Float32 WGS84 data on a 15-arc-second grid; all three
regional files exactly match pixels of the retained global TIFF. That global
file also matches the size and CRC32 of the TIFF member currently offered by
the official 2025 raw VJ146A4 download. **Size/CRC32 concordance is supporting
evidence, not cryptographic identity or proof of historical acquisition.**
No remote SHA-256 comparison was performed. Original download URLs/dates and
NASA granule identifiers were not retained and are not reconstructed from
file timestamps. The current link is a verification reference, not an asserted
historical download URL.

Darkspots computes its own ALR, darkness, Bortle classes and candidate selection
from the retained raw radiance. It does not redistribute the site's rendered
RGB overlays, Sky Brightness layer, country statistics or user measurements.

## OpenStreetMap, OSMCoastline and Geofabrik

**© OpenStreetMap contributors.** Data available under
[ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/).
See [OpenStreetMap copyright](https://www.openstreetmap.org/copyright) and
[OSMF attribution guidance](https://osmfoundation.org/wiki/Licence/Attribution_Guidelines).

- **OSMCoastline land polygons**, processed and distributed through
  [OSM Data](https://osmdata.openstreetmap.de/). The retained
  `land-polygons-split-4326.zip` has recorded retrieval on 2026-10-31 and server
  last modification on 2026-10-31; these are not asserted to be the original
  OSM edit dates. [Data licence](https://osmdata.openstreetmap.de/info/license.html).
- **Geofabrik OpenStreetMap hydrography extracts**, retained dated `261030`
  shapefile archives/members and their recorded regional provenance, not today's
  `latest` downloads. [Geofabrik download terms](https://www.geofabrik.de/data/download.html).

OSM-derived land, water and wetland evidence is spatially prepared and indexed,
then influences candidate qualification, ranking, selection and retention.
Coordinates originate at VIIRS pixel centres; that fact alone does not remove
possible database-right obligations. The ODbL treatment of the generated
database is distinct from the unambiguous ODbL treatment of the prepared
OSM-derived geometry databases.

## ESA WorldCover

**ESA WorldCover 10 m 2021 v200**, licensed under
[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).
[Official usage and citation instructions](https://esa-worldcover.org/en/data-access).

© ESA WorldCover project 2021 / Contains modified Copernicus Sentinel data (2021) processed by ESA WorldCover consortium

Dataset citation: Zanaga, D., Van De Kerchove, R., Daems, D., De Keersmaecker, W.,
Brockmann, C., Kirches, G., Wevers, J., Cartus, O., Santoro, M., Fritz, S., Lesiv,
M., Herold, M., Tsendbazar, N.E., Xu, P., Ramoino, F., Arino, O., 2022.
**ESA WorldCover 10 m 2021 v200.** [doi:10.5281/zenodo.7254221](https://doi.org/10.5281/zenodo.7254221).

Darkspots samples the retained classification tiles at native resolution and
uses their classes in a combined geographic qualification and selection
process. The distributed spot/cluster databases are derived outputs; they are
not original ESA classifications. This describes the transformation performed
by Darkspots, in addition to retaining the provider's Sentinel modification
notice. No WorldCover raster is included in this repository and no endorsement
by ESA or the consortium is implied.

## Copernicus DEM GLO-30 and water body mask

**Copernicus DEM GLO-30 DGED**, retained release **2024_1**, including its
associated water body mask (WBM). Sampled elevations and WBM-based candidate
qualification are derived uses. GLO-30 uses its own Copernicus DEM terms,
not ODbL, CC0 or the restricted EEA-10 licence.

Required notice for modified or derived GLO-30 products:

> produced using Copernicus WorldDEM-30 © DLR e.V. 2010-2014 and © Airbus Defence and Space GmbH 2014-2018 provided under COPERNICUS by the European Union and ESA; all rights reserved

Required liability notice (GLO-30 licence, article 6(c)):

> The organisations in charge of the Copernicus programme by law or by delegation do not incur any liability for any use of the Copernicus WorldDEM-30

[Official product, licence and notice instructions](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM).
The [supplier licence compilation](https://dataspace.copernicus.eu/sites/default/files/media/files/2025-06/copernicus_contributing_mission_data_access_v2_cop_dem_licenses.pdf),
pages 22–24 (GLO-30 section, articles 4–9), grants reproduction, distribution
and adaptation while retaining supplier rights. Subsequent users must retain
the applicable article 6 notices, liability disclaimer and non-endorsement
obligations for any onward distribution or communication of that material.
Dataset citation: [doi:10.5270/ESA-c5d3d65](https://doi.org/10.5270/ESA-c5d3d65).
The original DEM/WBM rasters remain under their supplier's terms; Darkspots does
not redistribute them here. Sampled elevations are rounded metres from a
surface model, not surveyed ground heights.

## GeoNames

**GeoNames**, under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).
[GeoNames](https://www.geonames.org/), [official extract licence and format](https://download.geonames.org/export/dump/readme.txt).

The local `cities500` extract supplies locality coverage and nearest-town labels.
Country-filtered FR/ES/GB extracts recorded as downloaded on 2026-08-25 and IE
on 2026-08-27 supply the naming cascade. Country extracts are filtered by
feature code and geographic extent; names, distances and identifiers are
incorporated into the derived spot records. These dates identify recorded
acquisitions, not a version date for all GeoNames data. The historical
`cities500` acquisition date is unknown; its retained checksum identifies the
actual input. No separate GeoNames elevation input supplies E3 spot altitudes.

## Natural Earth

**Made with Natural Earth.** Natural Earth **v5.1.1**, 1:10m `land` and
`admin_0_countries`, used for land/country qualification and country attribution.
The datasets are [public-domain data](https://www.naturalearthdata.com/about/terms-of-use/).

## Provenance, access and redistribution

The assessment and metadata/checksum inventory are maintained in the pipeline:
[assessment](https://github.com/mivek/darkskyspots-pipeline/blob/main/docs/licensing/e3-2025-assessment.md)
and [provenance](https://github.com/mivek/darkskyspots-pipeline/blob/main/docs/licensing/e3-2025-provenance.json).
These links identify intended repository locations; local preparation does not
assert that these documents or E3 have already been pushed.

The machine-readable Darkspots database is distributed through
[this repository](https://github.com/mivek/darkskyspots-data), in `spots/` and
`clusters/`. Use the audited release revision and preserve these notices and
the licence when conveying copies. Publicly used derivative databases must
meet ODbL share-alike and section 4.6 access obligations; produced works must
retain attribution and any applicable underlying-database offer. Include
GeoNames/WorldCover attribution, licence links and modification information
where their material is reused.

Private retention of prepared geometries does not itself waive any applicable
ODbL obligation. Any future distribution or public use requiring access to an
OSM-derived geometry database must separately provide that database or the
applicable alterations/method offer under ODbL. No raw geometry, source raster
or private geographic package is included here. Other third-party rights,
including trademarks, access rights and provider notices, are not granted by
the Darkspots database licence.
