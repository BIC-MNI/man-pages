---
section: 1
title: mask_values
author: David MacDonald
group: Statistical and Analysis Tools
---
# mask_values

mask values in a volume based on a range in another volume

`mask_values input1.mnc input2.mnc output.mnc min1 max1 set2`

## DESCRIPTION

**mask_values** masks values in the second volume based on a value range in
the first volume. For each voxel, if the value in *input1.mnc* falls within
the range (*min1*, *max1*), the corresponding voxel in the output is taken
from *input2.mnc*. Otherwise, the voxel in the output is set to *set2*.

This is useful for selectively extracting values from one volume using
another volume as a mask, with control over the acceptance range and the
replacement value for rejected voxels.

## EXAMPLES

    mask_values classification.mnc t1.mnc masked.mnc 2.5 3.5 0

## SEE ALSO

[mask_volume](mask_volume), [mincmask](mincmask), [mincmath](mincmath)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
