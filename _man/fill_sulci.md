---
section: 1
title: fill_sulci
author: David MacDonald
group: Surface and Geometry Tools
---
# fill_sulci

fill sulcal regions between a surface and a volume using a threshold

`fill_sulci in_volume.mnc in_surface.obj threshold out_volume.mnc`

## DESCRIPTION

`fill_sulci` fills the sulcal regions (grooves) on a cortical surface by
combining information from an input volume and a surface object. Voxels
below the specified threshold that lie in sulcal areas between the surface
and the volume are filled, and the result is written to the output volume.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`in_volume.mnc`
:   The input MINC volume.

`in_surface.obj`
:   The input surface object file defining the cortical surface.

`threshold`
:   The intensity threshold used to determine sulcal regions.

`out_volume.mnc`
:   The output MINC volume with sulci filled.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[classify_sulcus](classify_sulcus) [label_sulci](label_sulci) [surface_mask](surface_mask)
