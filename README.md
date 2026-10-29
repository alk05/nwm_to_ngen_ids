# NWM to NGEN IDs
Builds 1-to-1 ID matching between NWM feature IDs and NextGen IDs.

Output .json files are in the format of `{"nex-<id>": [hf_id]}`. Requires the VPU v2.2_hydrofabric geopackages and the `conus_reference.gpkg`.

## Methodology
For each `wb-` id in a VPU's `network` table, one `hf_id` is kept:
1. If any of its `hf_id`s is a gage (from `conus_reference.gpkg`), keep the gage with the lowest `hf_hydroseq` (furthest downstream).
2. Otherwise, keep the `hf_id` with the lowest `hf_hydroseq`.

## Getting the geopackages
`conus_reference.gpkg` is found within the 22_reference_tar.gz found at https://qoomon.github.io/aws-s3-bucket-browser/index.html?bucket=https://s3.amazonaws.com/communityhydrofabric

VPU geopackages are in the AWS S3 bucket: https://datastream.ciroh.org/index.html#resources/v2.2_hydrofabric/geopackages
