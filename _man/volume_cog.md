---
section: 1
title: volume_cog
author: Louis Collins
group: Registration
---
# volume_cog

compute the intensity-weighted center of gravity of a MINC volume

`volume_cog volume.mnc [mask.mnc]`

## DESCRIPTION

`volume_cog` reads a 3D MINC volume and computes its intensity-weighted
center of gravity (COG) in world coordinates. For each voxel, the world
coordinate is weighted by the voxel's intensity value, and the COG is
calculated as:

    COG = sum(coordinate * intensity) / sum(intensity)

for each of the X, Y, and Z axes.

If an optional mask volume is provided, only voxels that are not masked out
are included in the computation.

The three COG coordinates (x, y, z) are printed to standard output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

## EXAMPLES

Compute the center of gravity of a brain volume:

    volume_cog brain.mnc

Compute the center of gravity using a mask:

    volume_cog brain.mnc mask.mnc

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[xfm2param](xfm2param) [mincstats](mincstats)
