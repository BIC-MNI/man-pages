---
section: 1
title: minc_rank
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# minc_rank

Convert voxel intensities to rank values in the range 0-100.

`minc_rank [options] <source> <output>`

## DESCRIPTION

**minc_rank** converts voxel intensities in a MINC volume into rank-based
percentile values ranging from 0 to 100. Each voxel's output value represents
its percentile position in the overall intensity distribution. This is useful
for normalizing intensity distributions across subjects or for non-parametric
statistical analyses.

## OPTIONS

`--mask` *mask.mnc*
:   Restrict the rank computation to voxels within the specified binary mask.
    Voxels outside the mask will have a value of 0 in the output.

`--fix_zero_padding`
:   Handle zero-padded regions by excluding them from the ranking.

`--verbose`
:   Print progress information during processing.

## EXAMPLES

Convert intensities to ranks:

    minc_rank source.mnc ranked.mnc

Convert intensities to ranks within a brain mask:

    minc_rank --mask brainmask.mnc source.mnc ranked.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[minc_nuyl](minc_nuyl), [volume_pol](volume_pol)
