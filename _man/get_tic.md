---
section: 1
title: get_tic
author: David MacDonald
group: Statistical and Analysis Tools
---
# get_tic

compute statistics for spherical regions in a MINC volume

`get_tic filename.mnc x y z v|w [radius1] [radius2] [radius3]`

## DESCRIPTION

`get_tic` computes the minimum, maximum, mean, standard deviation, and
median for a spherical region centred at a given position in a MINC volume.
Positions are specified in voxel coordinates (with `v`) or world
coordinates (with `w`). Up to three radii may be specified to define the
sphere axes; if fewer are given, the region defaults to a single voxel or
a sphere with the given radius.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`filename.mnc`
:   The input MINC volume.

`x y z`
:   The centre position of the spherical region.

`v|w`
:   Coordinate system: `v` for voxel coordinates, `w` for world coordinates.

`radius1`
:   Optional radius of the sphere along the first axis.

`radius2`
:   Optional radius along the second axis.

`radius3`
:   Optional radius along the third axis.

## EXAMPLES

Get statistics at voxel (50, 60, 70):

    get_tic volume.mnc 50 60 70 v

Get statistics at world (10, -20, 30) with radius 5mm:

    get_tic volume.mnc 10 -20 30 w 5

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincstats](mincstats) [intensity_statistics](intensity_statistics) [print_world_value](print_world_value)
