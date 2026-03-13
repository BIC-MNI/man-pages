---
section: 1
title: mincchamfer
author: Louis Collins
group: Registration
---
# mincchamfer

compute the chamfer distance transform of a MINC volume

`mincchamfer [<options>] <inputfile> <outputfile>`

## DESCRIPTION

`mincchamfer` reads a 3D MINC volume and computes the chamfer distance
transform, writing the result to an output MINC volume. The chamfer distance
is an approximation of the Euclidean distance transform: for each voxel, it
estimates the distance to the nearest non-background (boundary) voxel using
a multi-pass local neighbourhood propagation algorithm.

The maximum distance value can be capped via the `-max_dist` option. This
is useful in registration pipelines for computing distance maps from
segmented structures or binary masks, which can then be used as features
for registration cost functions.

## OPTIONS

`-max_dist` value
:   Maximum distance value in the output transform. Default: 50.

`-first` n
:   Number of initial background structure dilations. Default: 0.

`-verbose`
:   Write messages indicating progress (default).

`-quiet`
:   Do not write log messages.

`-debug`
:   Print out debugging information.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXAMPLES

Compute the chamfer distance transform of a binary mask:

    mincchamfer mask.mnc distance_map.mnc

Compute the distance transform with a maximum distance of 100mm:

    mincchamfer -max_dist 100 mask.mnc distance_map.mnc

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Louis Collins

## SEE ALSO

[minctracc](minctracc) [mincmorph](mincmorph) [dilate_volume](dilate_volume)
