---
section: 1
title: subsample_volume
author: David MacDonald
group: Volume Operations
---
# subsample_volume

subsample a MINC volume by taking every nth voxel in each dimension

`subsample_volume input.mnc output.mnc nx ny nz`

## DESCRIPTION

**subsample_volume** reduces the resolution of a MINC volume by taking every
**nx**-th voxel along the x-axis, every **ny**-th voxel along the y-axis, and
every **nz**-th voxel along the z-axis. The output volume has correspondingly
fewer voxels in each dimension while preserving the spatial extent and
coordinate system of the original volume.

This is a simple decimation operation without interpolation or anti-aliasing
filtering.

## SEE ALSO

[mincresample](mincresample), [box_filter_volume](box_filter_volume),
[autocrop](autocrop)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
