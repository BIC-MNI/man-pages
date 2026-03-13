---
section: 1
title: surface_mask
author: David MacDonald
group: Surface and Geometry Tools
---
# surface_mask

create a binary mask volume from a surface object

`surface_mask in_volume.mnc in_surface.obj out_volume.mnc [min_value max_value] [set_value]`

## DESCRIPTION

**surface_mask** creates a binary mask volume from a surface object. Voxels
that lie inside the surface are set in the output volume, while voxels outside
are set to zero. The output volume uses the same sampling grid as the input
volume.

If **min_value** and **max_value** are specified, only voxels in the input
volume whose values fall within this range and are inside the surface are set
in the mask.

If **set_value** is specified, masked voxels are set to this value instead of
the default.

## SEE ALSO

[surface_mask2](surface_mask2), [scan_object_to_volume](scan_object_to_volume),
[mincmask](mincmask)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
