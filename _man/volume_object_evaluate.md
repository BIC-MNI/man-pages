---
section: 1
title: volume_object_evaluate
author: David MacDonald
group: Volume Operations
---
# volume_object_evaluate

evaluate volume values at surface object vertex positions

`volume_object_evaluate [options] volume.mnc object.obj output.txt`

## DESCRIPTION

**volume_object_evaluate** samples a MINC volume at each vertex position of a
BIC object file and writes the interpolated values to a text file. This is
useful for extracting intensity profiles or statistical measurements along a
surface.

The interpolation method can be selected using command-line options.

## OPTIONS

`-linear`
:   Use trilinear interpolation (default).

`-nearest_neighbour`
:   Use nearest-neighbour interpolation (no smoothing).

`-cubic`
:   Use tricubic interpolation.

`-rgb`
:   Convert RGB colour values to a colour flag in the output.

## EXAMPLES

    volume_object_evaluate brain.mnc cortex.obj values.txt

    volume_object_evaluate -cubic brain.mnc cortex.obj values.txt

    volume_object_evaluate -nearest_neighbour labels.mnc cortex.obj labels.txt

## SEE ALSO

[print_world_values](print_world_values),
[evaluate](evaluate), [surface_mask](surface_mask)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
