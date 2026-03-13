---
section: 1
title: box_filter_volume
author: David MacDonald
group: Volume Operations
---
# box_filter_volume

apply a box filter (uniform averaging) to a MINC volume

`box_filter_volume input.mnc output.mnc x_width y_width z_width [world|voxel] [byte]`

## DESCRIPTION

**box_filter_volume** applies a uniform averaging (box) filter to a MINC
volume. Each output voxel is the mean of all input voxels within the specified
rectangular neighbourhood.

The filter widths are specified separately for each dimension as **x_width**,
**y_width**, and **z_width**. By default, widths are specified in voxel units.
If the **world** keyword is given, the widths are interpreted as millimetres
in world coordinates. If the **voxel** keyword is given, voxel units are used
explicitly.

If the **byte** keyword is specified, the output volume is stored as an
unsigned byte volume.

## EXAMPLES

    box_filter_volume input.mnc smoothed.mnc 3 3 3

    box_filter_volume input.mnc smoothed.mnc 6.0 6.0 6.0 world

    box_filter_volume input.mnc smoothed.mnc 5 5 5 voxel byte

## SEE ALSO

[box_filter_volume_nd](box_filter_volume_nd), [mincblur](mincblur),
[mincresample](mincresample)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
