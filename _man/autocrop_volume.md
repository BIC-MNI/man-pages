---
section: 1
title: autocrop_volume
author: David MacDonald
group: Volume Operations
---
# autocrop_volume

crop a MINC volume by removing outer voxels below a threshold

`autocrop_volume input.mnc output.mnc [min_threshold] [n_boundary_voxels]`

## DESCRIPTION

`autocrop_volume` crops a MINC volume by removing the outer voxels whose
values are less than or equal to the specified minimum threshold. If no
threshold is given, a default of zero is used. An optional number of
boundary voxels can be specified to retain a margin around the
non-background region.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`min_threshold`
:   The minimum voxel value to consider as foreground. Voxels at or below
    this value are treated as background and removed during cropping.
    Defaults to zero if not specified.

`n_boundary_voxels`
:   The number of extra voxels to keep as a boundary around the cropped
    region. Defaults to zero if not specified.

## EXAMPLES

Crop a volume using the default threshold of zero:

    autocrop_volume input.mnc output.mnc

Crop a volume using a threshold of 10 with 2 boundary voxels:

    autocrop_volume input.mnc output.mnc 10 2

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[autocrop](autocrop) [mincreshape](mincreshape)
