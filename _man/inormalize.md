---
section: 1
title: inormalize
author: Andrew Janke
group: Intensity Normalization
---
# inormalize

intensity normalize a MINC volume following a registered model volume

`inormalize [options] <infile> [<outfile>]`

## DESCRIPTION

**inormalize** normalizes the intensity of a MINC volume, optionally relative
to a model volume. It supports several normalization methods including ratio of
means, ratio of medians, mean of ratios, mean of log-ratios, and median of
ratios. The normalization can be performed along specific axes
(z/y/x-normalize) to correct for slice-to-slice intensity variation. A mask
can be used to restrict the normalization to a specific region.

## OPTIONS

`-clobber`
:   Overwrite an existing output file.

`-noclobber`
:   Do not overwrite an existing output file (default).

`-verbose`
:   Print progress information.

`-quiet`
:   Do not print progress information.

`-print`
:   Print the normalization parameters without writing an output file.

`-compress`
:   Compress the output file.

`-nocompress`
:   Do not compress the output file.

`-nocache`
:   Do not use volume caching.

`-const <val>`
:   Normalize to a constant value.

`-const2 <val1> <val2>`
:   Normalize using two constant values.

`-range <pct>`
:   Set the percentage of voxels to use for range estimation.

`-model <model.mnc>`
:   Specify a model volume for relative normalization.

`-znormalize`
:   Normalize along the z-axis (transverse slices).

`-ynormalize`
:   Normalize along the y-axis (coronal slices).

`-xnormalize`
:   Normalize along the x-axis (sagittal slices).

`-minvoxels <n>`
:   Set the minimum number of voxels required per slice (default: 1000).

`-constrained`
:   Use constrained normalization.

`-rms`
:   Use root mean square normalization method.

`-vr`
:   Use variance ratio normalization method.

`-ratioOfMeans`
:   Use ratio of means normalization method.

`-ratioOfMedians`
:   Use ratio of medians normalization method.

`-meanOfRatios`
:   Use mean of ratios normalization method.

`-meanOfLogRatios`
:   Use mean of log-ratios normalization method.

`-medianOfRatios`
:   Use median of ratios normalization method (default).

`-mask`
:   Specify a mask volume for restricting normalization.

`-useVoxelCoord`
:   Use voxel coordinates for mask evaluation (default).

`-useWorldCoord`
:   Use world coordinates for mask evaluation.

`-threshold <min> <max>`
:   Set intensity thresholds for voxel selection.

`-nonormalize`
:   Do not apply normalization; report parameters only.

## EXAMPLES

    inormalize input.mnc output_normalized.mnc

    inormalize -model model.mnc -znormalize input.mnc normalized.mnc

    inormalize -ratioOfMeans -mask brain_mask.mnc -model model.mnc input.mnc normalized.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2000 by Andrew Janke

## SEE ALSO

[nu_correct](nu_correct), [classify](classify), [mincmath](mincmath), [volume_stats](volume_stats)
