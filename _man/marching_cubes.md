---
section: 1
title: marching_cubes
author: David MacDonald
group: Surface and Geometry Tools
---
# marching_cubes

create a polygonal surface from a thresholded MINC volume using marching cubes

`marching_cubes input.mnc output.obj threshold`

`marching_cubes input.mnc output.obj min_threshold max_threshold`

## DESCRIPTION

**marching_cubes** creates a polygonal surface from a MINC volume using the
marching cubes algorithm. The program has two modes of operation:

In single-threshold mode, a surface is extracted at the specified isosurface
*threshold* value.

In dual-threshold mode, a surface is extracted at the boundary of the region
where voxel values fall between *min_threshold* and *max_threshold*. This is
useful for extracting the surface of a labelled region or a range of
intensity values.

The output is a BIC .obj polygon file suitable for visualization with
**Display** or further processing with other surface tools.

## EXAMPLES

Extract an isosurface at threshold 0.5:

    marching_cubes brain.mnc surface.obj 0.5

Extract the boundary of a label range:

    marching_cubes labels.mnc region.obj 1.5 4.5

## SEE ALSO

[surface_mask](surface_mask), [make_surface_bitlist](make_surface_bitlist)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
