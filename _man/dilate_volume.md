---
section: 1
title: dilate_volume
author: David MacDonald
group: Volume Operations
---
# dilate_volume

dilate regions of a specified value in a MINC volume

`dilate_volume input.mnc output.mnc dilation_value [6|26] [n_dilations] [mask.mnc min_mask max_mask]`

## DESCRIPTION

`dilate_volume` dilates all regions in a MINC volume that have the
specified `dilation_value`. Dilation is performed using a 3x3x3
neighbourhood by `n_dilations` iterations (1 by default). The
connectivity can be set to 6 (face-connected) or 26 (face-, edge-, and
corner-connected), with 26 being the default. If a mask volume and range
are specified, only voxels within the given mask range will be considered
for dilation.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`dilation_value`
:   The voxel value identifying the regions to dilate.

`6|26`
:   Connectivity type. Use 6 for face-connected neighbours or 26 for
    all neighbours. Defaults to 26.

`n_dilations`
:   Number of dilation iterations to apply. Defaults to 1.

`mask.mnc`
:   An optional mask volume restricting where dilation may occur.

`min_mask`
:   Minimum mask value for the allowed dilation region.

`max_mask`
:   Maximum mask value for the allowed dilation region.

## EXAMPLES

Dilate label value 1 once with 26-connectivity:

    dilate_volume input.mnc output.mnc 1

Dilate label value 1 five times with 6-connectivity:

    dilate_volume input.mnc output.mnc 1 6 5

Dilate with a mask restricting to voxels between 0.5 and 1.5:

    dilate_volume input.mnc output.mnc 1 26 3 mask.mnc 0.5 1.5

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[dilate_volume_completely](dilate_volume_completely) [chamfer_volume](chamfer_volume) [mincmorph](mincmorph)
