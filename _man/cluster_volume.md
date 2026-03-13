---
section: 1
title: cluster_volume
author: David MacDonald
group: Volume Operations
---
# cluster_volume

label connected components in a thresholded MINC volume

`cluster_volume input.mnc output.mnc min_threshold max_threshold [6|26]`

## DESCRIPTION

`cluster_volume` creates a label volume where each connected component of
voxels with values between `min_threshold` and `max_threshold` (inclusive)
is assigned a distinct label number. The connectivity can be specified as
6-neighbour (face-connected) or 26-neighbour (face-, edge-, and
corner-connected).

## OPTIONS

This tool uses positional arguments only. There are no named options.

`min_threshold`
:   The minimum voxel value for inclusion in a cluster.

`max_threshold`
:   The maximum voxel value for inclusion in a cluster.

`6|26`
:   Connectivity type. Use 6 for face-connected neighbours or 26 for
    fully connected neighbours. Defaults to 26 if not specified.

## EXAMPLES

Label connected components with values between 0.5 and 1.5 using 26-connectivity:

    cluster_volume input.mnc output.mnc 0.5 1.5

Label with 6-connectivity:

    cluster_volume input.mnc output.mnc 0.5 1.5 6

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[chamfer_volume](chamfer_volume) [dilate_volume](dilate_volume) [mincdefrag](mincdefrag)
