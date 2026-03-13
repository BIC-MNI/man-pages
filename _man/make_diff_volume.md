---
section: 1
title: make_diff_volume
author: David MacDonald
group: Volume Operations
---
# make_diff_volume

create a 4-class volume based on value ranges in two input volumes

`make_diff_volume input1.mnc min1 max1 input2.mnc min2 max2 output.mnc`

## DESCRIPTION

**make_diff_volume** creates a 4-class output volume based on whether each
voxel in two input volumes falls within specified value ranges. For each
voxel position, the program tests whether the value in *input1.mnc* is
within the range (*min1*, *max1*) and whether the value in *input2.mnc* is
within the range (*min2*, *max2*). The four resulting classes correspond to
the four possible combinations: both within range, only the first within
range, only the second within range, or neither within range.

This is useful for comparing two volumes and identifying regions of agreement
and disagreement, such as comparing two segmentations or classification
results.

## EXAMPLES

    make_diff_volume seg1.mnc 0.5 3.5 seg2.mnc 0.5 3.5 diff.mnc

## SEE ALSO

[mask_volume](mask_volume), [minccmp](minccmp)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
