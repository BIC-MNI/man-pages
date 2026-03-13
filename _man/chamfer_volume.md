---
section: 1
title: chamfer_volume
author: David MacDonald
group: Volume Operations
---
# chamfer_volume

compute the chamfer distance transform of a binary volume

`chamfer_volume input.mnc output.mnc min max [6|26]`

## DESCRIPTION

`chamfer_volume` computes a chamfer distance transform on a MINC volume.
Voxels with values between `min` and `max` (inclusive) are treated as
foreground. The output volume contains, for each voxel, an approximation
of its distance to the nearest foreground voxel. An optional connectivity
argument specifies 6-neighbour or 26-neighbour connectivity for the
distance computation.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`min`
:   The minimum value defining the foreground region.

`max`
:   The maximum value defining the foreground region.

`6|26`
:   Connectivity type for the distance computation. Use 6 for
    face-connected neighbours or 26 for face-, edge-, and
    corner-connected neighbours. Defaults to 26 if not specified.

## EXAMPLES

Compute a chamfer distance transform for voxels with values between 1 and 1:

    chamfer_volume input.mnc output.mnc 1 1

Compute with 6-connectivity:

    chamfer_volume input.mnc output.mnc 1 1 6

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[dilate_volume](dilate_volume) [mincchamfer](mincchamfer) [cluster_volume](cluster_volume)
