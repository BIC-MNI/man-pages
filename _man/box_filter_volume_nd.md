---
section: 1
title: box_filter_volume_nd
author: David MacDonald
group: Volume Operations
---
# box_filter_volume_nd

apply an n-dimensional box filter to a MINC volume

`box_filter_volume_nd input.mnc output.mnc x_width [y_width [z_width [width4 [width5]]]]`

## DESCRIPTION

**box_filter_volume_nd** applies a uniform averaging (box) filter to a MINC
volume, supporting up to 5 dimensions. Filter widths are specified in world
coordinate units (millimetres).

At minimum, **x_width** must be specified. Additional widths for higher
dimensions are optional. If fewer widths are given than the number of
dimensions in the volume, only the specified dimensions are filtered.

This tool is a generalization of **box_filter_volume** that handles
multi-dimensional data such as volumes with time or vector dimensions.

## EXAMPLES

    box_filter_volume_nd input.mnc smoothed.mnc 4.0

    box_filter_volume_nd input.mnc smoothed.mnc 4.0 4.0 4.0

    box_filter_volume_nd input_4d.mnc smoothed_4d.mnc 4.0 4.0 4.0 0.0

## SEE ALSO

[box_filter_volume](box_filter_volume), [mincblur](mincblur),
[mincresample](mincresample)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
