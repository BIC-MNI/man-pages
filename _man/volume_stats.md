---
section: 1
title: volume_stats
author: John G. Sled
group: Non-Uniformity Correction
---
# volume_stats

compute and print statistics for a MINC volume

`volume_stats [options] <file1> [<file2> ...]`

## DESCRIPTION

**volume_stats** computes statistics on one or more MINC volumes and prints the
results. It supports a wide range of statistical measures including volume,
minimum, maximum, sum, mean, variance, standard deviation, median, majority,
bimodal threshold, percentile threshold, entropy, and centre of mass. Voxels
can be selected by intensity thresholds, mask volumes, slice orientation, and
other criteria.

## OPTIONS

`-verbose`
:   Print progress information.

`-quiet`
:   Do not print progress information.

`-debug`
:   Print debugging information.

`-nocache`
:   Do not use volume caching.

`-transverse`
:   Process slices in transverse orientation.

`-sagittal`
:   Process slices in sagittal orientation.

`-coronal`
:   Process slices in coronal orientation.

`-dimorder`
:   Specify dimension ordering.

`-include_nan`
:   Include NaN values in statistics.

`-slice`
:   Compute statistics on individual slices.

`-ceil`
:   Set the upper intensity threshold for voxel inclusion.

`-floor`
:   Set the lower intensity threshold for voxel inclusion.

`-binvalue`
:   Select voxels with a specific integer value.

`-mask`
:   Specify a mask volume for voxel selection.

`-useWorldCoord`
:   Use world coordinates for mask evaluation.

`-maskbinvalue`
:   Select mask voxels with a specific integer value.

`-maskfloor`
:   Set the lower threshold for the mask volume.

`-maskceil`
:   Set the upper threshold for the mask volume.

`-maskrange`
:   Set a range of values for the mask volume.

`-all`
:   Print all statistics (default).

`-none`
:   Print no statistics; use with specific statistic flags.

`-volume`
:   Print the volume of selected voxels.

`-min`
:   Print the minimum intensity value.

`-max`
:   Print the maximum intensity value.

`-sum`
:   Print the sum of intensity values.

`-sum2`
:   Print the sum of squared intensity values.

`-mean`
:   Print the mean intensity value.

`-var`
:   Print the variance of intensity values.

`-stddev`
:   Print the standard deviation of intensity values.

`-median`
:   Print the median intensity value.

`-majority`
:   Print the most frequently occurring intensity value.

`-biModalT`
:   Print the bimodal threshold separating two intensity classes.

`-pctT`
:   Print the percentile threshold.

`-entropy`
:   Print the entropy of the intensity distribution.

`-CoM`
:   Print the centre of mass of the selected voxels.

## EXAMPLES

    volume_stats input.mnc

    volume_stats -mean -stddev -mask brain_mask.mnc input.mnc

    volume_stats -none -median -floor 10 input.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[volume_hist](volume_hist), [mincstats](mincstats), [nu_correct](nu_correct)
