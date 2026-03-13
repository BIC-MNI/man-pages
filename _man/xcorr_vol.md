---
section: 1
title: xcorr_vol
author: Louis Collins
group: Registration
---
# xcorr_vol

compute the normalized cross-correlation between two MINC volumes

`xcorr_vol vol1.mnc vol2.mnc [mask.mnc]`

## DESCRIPTION

`xcorr_vol` reads two 3D MINC volumes of equal size and computes the
normalized cross-correlation coefficient between them:

    corr = sum(v1 * v2) / (sqrt(sum(v1^2)) * sqrt(sum(v2^2)))

If an optional mask volume is provided, only voxels where the mask value is
greater than or equal to 0.5 are included in the computation.

A single floating-point correlation value is printed to standard output. A
value of 1.0 indicates identical volumes, 0.0 indicates no correlation, and
-1.0 indicates perfect anti-correlation.

This tool is useful for evaluating registration quality or measuring
similarity between two volumes.

## OPTIONS

This tool uses positional arguments only. There are no named options.

## EXAMPLES

Compute the cross-correlation between two volumes:

    xcorr_vol source.mnc target.mnc

Compute the cross-correlation within a masked region:

    xcorr_vol source.mnc target.mnc brain_mask.mnc

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minctracc](minctracc) [minccmp](minccmp)
