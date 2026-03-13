---
section: 1
title: transform_volume
author: David MacDonald
group: Volume Operations
---
# transform_volume

apply a spatial transform to a MINC volume by modifying its voxel-to-world transform

`transform_volume input.mnc input.xfm output.mnc`

## DESCRIPTION

**transform_volume** changes the voxel-to-world coordinate transformation of a
MINC volume by appending the input transform to the existing one. Unlike
**mincresample**, this tool does not resample or interpolate the voxel data.
The voxel values remain identical; only the header information describing the
mapping from voxel indices to world coordinates is modified.

This approach is computationally efficient because no resampling is needed,
but note that the output volume will appear shifted or rotated when viewed in
world coordinates.

## EXAMPLES

    transform_volume input.mnc shift.xfm output.mnc

## SEE ALSO

[mincresample](mincresample), [transform_objects](transform_objects),
[transform_tags](transform_tags), [xfmconcat](xfmconcat)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
