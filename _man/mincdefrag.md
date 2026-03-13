---
section: 1
title: mincdefrag
author: David MacDonald
group: Volume Operations
---
# mincdefrag

remove small disconnected fragments from a labelled MINC volume

`mincdefrag input.mnc output.mnc label stencil [max_connect]`

## DESCRIPTION

**mincdefrag** removes small disconnected fragments of a specified label
from a labelled MINC volume. The program identifies connected components
of voxels with the given label value and removes components that contain
fewer voxels than the *max_connect* threshold by replacing them with
the most common neighbouring label.

The *label* argument specifies the integer label value of the voxels to
process. The *stencil* argument defines the connectivity neighbourhood:
**6** for face-connected neighbours, **19** for face- and edge-connected
neighbours, or **27** for face-, edge-, and corner-connected neighbours.

The optional *max_connect* parameter sets the minimum number of connected
voxels required for a component to be retained. Components smaller than
this threshold are removed.

## EXAMPLES

Remove small fragments of label 3 using 6-connectivity:

    mincdefrag labels.mnc cleaned.mnc 3 6

Remove fragments smaller than 100 voxels using 26-connectivity:

    mincdefrag labels.mnc cleaned.mnc 3 27 100

## SEE ALSO

[dilate_volume](dilate_volume), [mask_volume](mask_volume),
[mincmorph](mincmorph)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
