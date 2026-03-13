---
section: 1
title: mask_volume
author: David MacDonald
group: Volume Operations
---
# mask_volume

mask a MINC volume by setting voxels outside a specified mask range

`mask_volume input.mnc mask_volume.mnc output.mnc [min] [max] [value_to_set]`

## DESCRIPTION

**mask_volume** modifies voxels in the input volume based on a mask volume.
A voxel is changed to *value_to_set* if the corresponding voxel in the mask
volume does **not** have a value between *min* and *max*.

By default, *min* is set so that the mask selects voxels with values greater
than zero, *max* is effectively unbounded, and *value_to_set* defaults to
the volume minimum. This means that by default, voxels where the mask is
zero or negative are replaced with the volume minimum.

## OPTIONS

`min`
:   Minimum mask value for a voxel to be preserved. Default: values > 0
    are preserved.

`max`
:   Maximum mask value for a voxel to be preserved.

`value_to_set`
:   Value assigned to masked-out voxels. Default: volume minimum.

## EXAMPLES

Mask a volume using default settings (preserve where mask > 0):

    mask_volume brain.mnc mask.mnc output.mnc

Mask with explicit range and replacement value:

    mask_volume brain.mnc mask.mnc output.mnc 0.5 1.5 0

## SEE ALSO

[mincmask](mincmask), [mask_values](mask_values), [mincmath](mincmath)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
