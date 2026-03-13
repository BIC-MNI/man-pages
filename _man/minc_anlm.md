---
section: 1
title: minc_anlm
author: Vladimir S. Fonov
group: Noise Filtering
---
# minc_anlm

Adaptive non-local means denoising of MRI images.

`minc_anlm [options] <source> <output>`

## DESCRIPTION

**minc_anlm** applies an adaptive non-local means (ANLM) denoising filter to
a MINC volume. The method is based on Manjon, Coupe, Marti-Bonmati, Collins,
and Robles (2010), "Adaptive Non-Local Means Denoising of MR Images With
Spatially Varying Noise Levels" (Journal of Magnetic Resonance Imaging,
31(1):192-203).

The filter removes noise while preserving edges and structural details by
averaging similar patches from a local search neighborhood. The adaptive
variant automatically adjusts the filtering strength based on local noise
estimates. A Rician noise correction mode is available for magnitude MRI data.

## OPTIONS

`--rician`
:   Apply correction for Rician noise bias, appropriate for magnitude MRI data.

`--search` *n*
:   Set the search neighborhood radius in voxels.

`--patch` *n*
:   Set the patch radius in voxels for similarity comparisons.

`--beta` *f*
:   Adjust the smoothing weight parameter. Higher values produce more
    smoothing. Default: 1.

`--mt` *n*
:   Set the number of threads for parallel processing. Default: 1.

`--verbose`
:   Print progress information during processing.

`--double`
:   Write output in double-precision floating-point format.

`--float`
:   Write output in single-precision floating-point format.

`--short`
:   Write output in short integer format.

`--byte`
:   Write output in byte (unsigned char) format.

## EXAMPLES

Denoise a T1-weighted MRI volume:

    minc_anlm t1.mnc t1_denoised.mnc

Denoise with Rician noise correction and 4 threads:

    minc_anlm --rician --mt 4 t1.mnc t1_denoised.mnc

Denoise with custom search and patch radii:

    minc_anlm --search 3 --patch 1 --beta 0.8 t1.mnc t1_denoised.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mincnlm](mincnlm), [noise_estimate](noise_estimate)
