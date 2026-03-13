---
section: 1
title: convex_hull
author: David MacDonald
group: Surface and Geometry Tools
---
# convex_hull

create a convex hull polyhedron from a surface or volume

`convex_hull input.[mnc|obj] output_hull.obj [min_value] [max_value]`

## DESCRIPTION

`convex_hull` creates a polyhedron which is the convex hull of the input
data. The input can be either a surface object file (.obj) or a MINC
volume file (.mnc). When a volume is provided, the convex hull is
computed from the region containing voxels with values between `min_value`
and `max_value`. If no value range is specified, the convex hull is
computed from all non-zero voxels.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.[mnc|obj]`
:   The input file, either a MINC volume or a surface object file.

`output_hull.obj`
:   The output convex hull surface object file.

`min_value`
:   The minimum voxel value for inclusion (volume input only). Defaults
    to non-zero if not specified.

`max_value`
:   The maximum voxel value for inclusion (volume input only). Defaults
    to non-zero if not specified.

## EXAMPLES

Create a convex hull from a surface:

    convex_hull brain.obj hull.obj

Create a convex hull from a volume with values between 1 and 255:

    convex_hull brain.mnc hull.obj 1 255

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[marching_cubes](marching_cubes) [close_surface](close_surface)
