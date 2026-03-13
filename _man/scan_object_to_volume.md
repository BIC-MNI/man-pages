---
section: 1
title: scan_object_to_volume
author: David MacDonald
group: Volume Operations
---
# scan_object_to_volume

scan a BIC object into a MINC volume creating a binary mask

`scan_object_to_volume volume.mnc object.obj output_file.mnc`

## DESCRIPTION

**scan_object_to_volume** scans a BIC object file (such as a surface or lines
object) into a MINC volume, producing a binary mask. Voxels that intersect or
are enclosed by the object are set to a non-zero value, while all other voxels
are set to zero. The output volume has the same sampling grid as the input
example volume.

This tool is useful for converting geometric surface representations into
volumetric masks for further processing or analysis.

## SEE ALSO

[surface_mask](surface_mask), [surface_mask2](surface_mask2),
[scan_lines_to_polygons](scan_lines_to_polygons)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
