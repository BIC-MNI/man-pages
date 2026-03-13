---
section: 1
title: copy_stats_to_volume
author: David MacDonald
group: Volume Operations
---
# copy_stats_to_volume

copy per-vertex statistics to a volume using a surface mapping

`copy_stats_to_volume volume.mnc object.obj stats.txt result.mnc [fillvalue]`

## DESCRIPTION

`copy_stats_to_volume` maps per-vertex statistical values from a text file
onto a MINC volume using a surface object as the spatial reference. Each
vertex of the surface object is associated with a value from the
statistics file, and the corresponding voxel in the output volume is set
to that value. An optional fill value specifies the value assigned to
voxels not covered by any vertex.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume.mnc`
:   The input MINC volume providing the sampling grid.

`object.obj`
:   The surface object file providing the vertex-to-voxel mapping.

`stats.txt`
:   A text file containing one statistical value per vertex.

`result.mnc`
:   The output MINC volume with mapped statistical values.

`fillvalue`
:   The value to assign to voxels not covered by any surface vertex.
    Optional.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[scan_object_to_volume](scan_object_to_volume) [surface_mask](surface_mask)
