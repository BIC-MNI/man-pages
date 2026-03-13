---
section: 1
title: find_volume_centroid
author: David MacDonald
group: Volume Operations
---
# find_volume_centroid

find and print the centroid of a MINC volume

`find_volume_centroid input.mnc [threshold]`

## DESCRIPTION

`find_volume_centroid` computes and prints the centroid (centre of mass)
of a MINC volume. If a threshold is specified, only voxels with values at
or above the threshold are included in the centroid calculation. The
centroid is printed in world coordinates.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.mnc`
:   The input MINC volume.

`threshold`
:   An optional intensity threshold. Only voxels at or above this value
    contribute to the centroid calculation.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[volume_cog](volume_cog) [mincstats](mincstats)
