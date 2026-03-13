---
section: 1
title: itk_minc_nonlocal_filter
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_minc_nonlocal_filter

Patch-based non-local means denoising.

`itk_minc_nonlocal_filter <input.mnc> <output.mnc> [options]`

## DESCRIPTION

**itk_minc_nonlocal_filter** performs patch-based non-local means (NLM)
denoising on MINC volumes. The filter computes a weighted average of voxel
neighbourhoods, where the weights are determined by the similarity between
patches. This preserves edges and fine structures better than Gaussian
smoothing.

Several variants are supported: the standard NLM filter, the adaptive NLM
(ANLM), median-based filtering, and various output modes including
similarity maps, weight maps, and standard deviation maps. The search and
patch radii control the trade-off between computation time and denoising
quality.

An ROI mask can restrict processing to a specific region. The noise level
can be estimated automatically or specified manually.

## OPTIONS

`--noise` *f*
:   Specify the noise standard deviation. If not given, it is estimated
    automatically.

`--clobber`
:   Overwrite the output file if it already exists.

`--verbose`
:   Print progress information during processing.

`--search` *r*
:   Search radius in voxels (default: 2).

`--patch` *r*
:   Patch radius in voxels (default: 1).

`--float`
:   Store output voxels as single-precision floating point.

`--short`
:   Store output voxels as short integer.

`--byte`
:   Store output voxels as unsigned byte.

`--beta` *f*
:   Smoothing parameter controlling the decay of weights (default: 1.0).

`--mindist`
:   Use minimum distance instead of mean distance for weight computation.

`--median`
:   Use median instead of weighted mean for output.

`--similarity`
:   Output the similarity map instead of the denoised image.

`--mweight`
:   Output the maximum weight map.

`--mean`
:   Output the local mean.

`--sd`
:   Output the local standard deviation.

`--flat`
:   Use flat (uniform) patch weighting.

`--ball`
:   Use a ball-shaped search neighbourhood instead of a cube.

`--anlm`
:   Use the adaptive non-local means variant.

`--roi` *minc*
:   Restrict processing to voxels within the specified ROI mask.

`--log`
:   Process the image in the log domain.

`--regularize` *f*
:   Apply regularization with the specified weight.

`--preselect`
:   Enable voxel preselection based on local statistics (faster).

`--no_preselect`
:   Disable voxel preselection.

`--th_m` *f*
:   Mean preselection threshold (default: 0.95).

`--th_v` *f*
:   Variance preselection threshold (default: 0.5).

## EXAMPLES

    # Basic non-local means denoising
    itk_minc_nonlocal_filter input.mnc denoised.mnc

    # ANLM with specified noise level
    itk_minc_nonlocal_filter input.mnc denoised.mnc --anlm --noise 5.0

    # Larger search radius with preselection
    itk_minc_nonlocal_filter input.mnc denoised.mnc --search 3 --patch 2 \
        --preselect --float

    # Denoise within a mask
    itk_minc_nonlocal_filter input.mnc denoised.mnc --roi brain_mask.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[minc_anlm](minc_anlm) ,
[mincnlm](mincnlm) ,
[noise_estimate](noise_estimate)
