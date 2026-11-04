# Darkspots data

Machine-readable candidate stargazing locations and derived map clusters,
maintained by [@mivek](https://github.com/mivek). The database and derived cluster
databases are offered under the **Open Database License (ODbL) 1.0**. See
[LICENSE](LICENSE) and the separate upstream notices in [ATTRIBUTION.md](ATTRIBUTION.md).

## E3 2025 release

The radiance data year is **2025**, not the observation year of every supporting
dataset. The configured coverage is mainland France (bounding box
`[-6, 41, 8, 51]`), the United Kingdom and Ireland within `[-11, 49, 2, 55]`
(including the 55°N northern limit), and the Canary Islands within
`[-19, 27, -13, 30]`. Country ownership is determined with Natural Earth;
the bounding boxes do not imply complete national or island coverage.

This repository tree contains the E3 2025 release payload for geographic
revision `34cc9365f131d3c6a0abaf2d7c83e3bc74d38630cd6b9787ed278893e25caaa6`.
It contains 2,207 France spots, 1,217 United Kingdom and Ireland spots, and 66
Canary Islands spots (3,490 total), all confidence A in the offline geographic
publication audit. These files and the accompanying notices form the release
offer for this repository revision. The audit is technical and does not certify
the legal sufficiency of the notices or independently establish rights in
upstream datasets.

## Files and formats

- `spots/<tile>.json`: JSON envelopes with `tile`, `source`, `version`,
  `generated` (UTC) and a `spots` array. Tiles are one-degree cells named with
  three-digit latitude/longitude magnitudes, for example `N042E001`.
- Each spot includes WGS84 `lat`/`lon`, a deterministic `id` formed from those
  coordinates at four decimals, modeled `darkness` (0–1), `bortle`, `country`,
  locality/name fields and `altitude` in metres where available (`null` when
  unavailable). Naming provenance includes GeoNames identifiers and feature
  codes. Geographic confidence is internal audit evidence, not a public JSON field.
- `clusters/L1.json` through `L6.json`: cluster arrays for increasing map extents,
  containing a centroid, bounding box, count and representative spot. These are
  summaries of the spot database, not additional surveyed locations.
- `clusters/index.json`: schema version, data year, generation time and levels
  with cell sizes, view-width ranges and SHA-256 hashes of the level files.

Obtain the machine-readable database from this repository's `spots/` and
`clusters/` directories: [browse or download the repository](https://github.com/mivek/darkskyspots-data).
Use a specific Git revision for reproducibility and retain the licence and
attribution notices with copies. The release record identifies the geographic
revision and audited Git tree for this payload.

## Generation

The [Darkspots pipeline](https://github.com/mivek/darkskyspots-pipeline) converts
raw VIIRS radiance into modeled artificial-light ratio, darkness and Bortle
classes. Candidates remain at original VIIRS pixel centres. Natural Earth
supplies land/country attribution. E3 combines Copernicus WBM, OSMCoastline,
OSM hydrography and ESA WorldCover to qualify and prioritize candidates.
It then applies the existing mesh selection, same-Bortle redundancy rule and
locality-coverage additions. GeoNames supplies locality coverage and names;
Copernicus DEM supplies sampled elevations. All configured regions are merged,
global clusters are regenerated, and the complete staged Git tree is audited.

No raw source geometries, source rasters or private geographic packages are
distributed in this repository. Database licensing does not relicense those
upstream datasets; their permissions and attribution remain separate.

## Limitations

These are modeled candidates, not inspected observing sites. Geographic
confidence A is relative to the retained evidence and does not guarantee dry
ground, access rights, road access, safety or observing conditions. Tides are
not modeled. Raster resolution, acquisition dates, classification errors and
incomplete mapping can affect results. Copernicus DEM is a surface model and
may include vegetation or structures. Darkness and Bortle are model outputs,
not on-site sky measurements. No provider endorsement is implied.

## Reuse

Preserve the ODbL notice and upstream credits. Publicly used derivative databases
must meet the applicable ODbL share-alike and machine-readable access obligations;
produced works need appropriate attribution and any applicable underlying-data
offer. ODbL governs database rights, while upstream contents retain their
separate rights described in [ATTRIBUTION.md](ATTRIBUTION.md). The responsible
maintainer for this distribution decision is **@mivek**; no independent legal
certification is asserted.
