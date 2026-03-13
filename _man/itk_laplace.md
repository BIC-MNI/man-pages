---
section: 1
title: itk_laplace
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_laplace

apply Laplacian of Gaussian filter to a volume

`itk_laplace <input> <output> [options]`

## DESCRIPTION

**itk_laplace** applies a Laplacian of Gaussian (LoG) filter to an image volume
using the Insight Toolkit (ITK). The LoG filter first smooths the image with a
Gaussian kernel of a given sigma, then computes the Laplacian (second spatial
derivative). This highlights regions of rapid intensity change such as edges
and boundaries.

The LoG filter is commonly used for edge detection, blob detection, and as a
preprocessing step for segmentation. The `--sigma` parameter controls the scale
of the Gaussian smoothing: smaller values detect fine detail while larger values
respond to broader features.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--sigma` *val*
:   Set the standard deviation (sigma) of the Gaussian kernel in mm. Controls the spatial scale of the filter. Default is 1.0.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

## EXAMPLES

Apply a Laplacian of Gaussian filter with default sigma:

    itk_laplace input.mnc laplacian.mnc --float

Apply with a larger sigma for coarser edge detection:

    itk_laplace input.mnc laplacian.mnc --sigma 2.0 --float

Apply with double precision output:

    itk_laplace input.mnc laplacian.mnc --sigma 0.5 --double --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_laplacian_sharpening](itk_laplacian_sharpening), [itk_diffusion](itk_diffusion), [mincblur](mincblur), [itk_vesselness](itk_vesselness)
