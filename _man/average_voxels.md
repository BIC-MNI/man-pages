---
section: 1
title: average_voxels
author: David MacDonald
group: Volume Operations
---
# average_voxels

average voxels in blocks within a MINC volume

`average_voxels input.mnc output.mnc nx ny nz`

## DESCRIPTION

`average_voxels` reads a MINC volume and produces a new volume where each
output voxel is the average of a block of nx × ny × nz voxels from the
input. This effectively downsamples the volume by the specified block
dimensions.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`nx`
:   The block size along the first spatial dimension.

`ny`
:   The block size along the second spatial dimension.

`nz`
:   The block size along the third spatial dimension.

## EXAMPLES

Average voxels in 2×2×2 blocks:

    average_voxels input.mnc output.mnc 2 2 2

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincresample](mincresample) [subsample_volume](subsample_volume)
