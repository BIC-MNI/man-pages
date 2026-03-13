---
section: 1
title: contour_slice
author: David MacDonald
group: Surface and Geometry Tools
---
# contour_slice

create contour lines for a given slice of a volume

`contour_slice volume_file output_file x|y|z|xw|yw|zw slice_pos [contour_value1] [contour_value2] ...`

## DESCRIPTION

`contour_slice` extracts a 2D slice from a MINC volume at the specified
position along the given axis and creates contour lines at the specified
contour values. The axis can be specified in voxel coordinates (`x`, `y`,
`z`) or world coordinates (`xw`, `yw`, `zw`). If no contour values are
given, a default is used. The output is written as a lines object file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume_file`
:   The input MINC volume file.

`output_file`
:   The output object file containing contour lines.

`x|y|z|xw|yw|zw`
:   The axis along which to extract the slice. Use `x`, `y`, or `z` for
    voxel coordinates, or `xw`, `yw`, or `zw` for world coordinates.

`slice_pos`
:   The position of the slice along the specified axis.

`contour_value1 contour_value2 ...`
:   One or more contour values at which to generate contour lines.
    Optional.

## EXAMPLES

Create contour lines at value 50 on an axial slice at z=100:

    contour_slice volume.mnc contours.obj z 100 50

Create multiple contour lines in world coordinates:

    contour_slice volume.mnc contours.obj zw 0.0 50 100 150

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[marching_cubes](marching_cubes) [make_slice](make_slice)
