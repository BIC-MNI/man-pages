---
section: 1
title: surface_mask2
author: David MacDonald
group: Surface and Geometry Tools
---
# surface_mask2

create a binary mask from a surface (alternative implementation)

`surface_mask2 in_volume.mnc surface.obj output.mnc`

## DESCRIPTION

**surface_mask2** creates a binary mask volume from a surface object. This is
an alternative implementation to **surface_mask** that takes an input volume
for its sampling grid and a surface object, and produces a binary mask where
voxels inside the surface are set to a non-zero value.

The output volume inherits the voxel grid from the input volume.

## SEE ALSO

[surface_mask](surface_mask), [scan_object_to_volume](scan_object_to_volume),
[mincmask](mincmask)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
