---
section: 1
title: make_surface_bitlist
author: David MacDonald
group: Surface and Geometry Tools
---
# make_surface_bitlist

create a surface bitlist volume from a thresholded MINC volume

`make_surface_bitlist input.mnc output_prefix threshold [x_size] [y_size] [z_size] [tolerance]`

## DESCRIPTION

**make_surface_bitlist** creates a binary bitlist volume from a MINC volume
by thresholding. Voxels in the input volume that exceed the *threshold* are
marked in the output bitlist. The output files are written with the given
*output_prefix*.

Optional *x_size*, *y_size*, and *z_size* parameters control the dimensions
of the output bitlist volume. If not specified, the dimensions match the
input volume.

An optional *tolerance* parameter controls the tolerance used when
determining surface voxels. The bitlist is used internally by surface
extraction and reconstruction algorithms.

## EXAMPLES

    make_surface_bitlist brain.mnc surface_bits 0.5

    make_surface_bitlist brain.mnc surface_bits 0.5 256 256 256 0.01

## SEE ALSO

[marching_cubes](marching_cubes), [surface_mask](surface_mask)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
