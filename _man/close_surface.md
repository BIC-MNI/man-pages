---
section: 1
title: close_surface
author: David MacDonald
group: Surface and Geometry Tools
---
# close_surface

fill the interior of a surface in a volume

`close_surface in_volume.mnc in_surface.obj out_volume.mnc [label_to_set] [close_threshold]`

## DESCRIPTION

`close_surface` creates a new MINC volume with the interior of the given
surface filled with a label value. The input volume provides the sampling
grid for the output. An optional label value and closing threshold can be
specified.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`in_volume.mnc`
:   The input MINC volume that provides the sampling grid.

`in_surface.obj`
:   The input surface object file whose interior will be filled.

`out_volume.mnc`
:   The output MINC volume with the surface interior filled.

`label_to_set`
:   The label value to assign to voxels inside the surface. Optional.

`close_threshold`
:   A threshold value controlling the closing operation. Optional.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[surface_mask](surface_mask) [scan_object_to_volume](scan_object_to_volume)
