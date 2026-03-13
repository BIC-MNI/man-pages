---
section: 1
title: itk_vesselness
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_vesselness

apply vesselness filter for vessel-like structure enhancement

`itk_vesselness <input> <output> [options]`

## DESCRIPTION

**itk_vesselness** applies a Hessian-based vesselness filter (Frangi filter) to
a volume using the Insight Toolkit (ITK). The filter enhances tubular structures
such as blood vessels by analysing the eigenvalues of the Hessian matrix at each
voxel. It produces a response map where high values indicate a strong likelihood
of vessel-like geometry.

A multi-scale approach is supported through `--min-sigma`, `--max-sigma`, and
`--steps`, which allow the filter to detect vessels across a range of diameters.
At each scale, a Gaussian smoothing with the corresponding sigma is applied
before Hessian computation, and the maximum response across all scales is
retained.

The sensitivity of the filter is controlled by `--alpha`, `--beta`, and
`--gamma`, which weight the contributions of the plate-like, blob-like, and
structureness measures respectively.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--sigma` *val*
:   Set a single Gaussian sigma value (in mm) for single-scale vesselness computation.

`--min-sigma` *val*
:   Minimum sigma for multi-scale vesselness computation (in mm).

`--max-sigma` *val*
:   Maximum sigma for multi-scale vesselness computation (in mm).

`--steps` *n*
:   Number of discrete sigma steps between min-sigma and max-sigma for multi-scale analysis.

`--alpha` *val*
:   Sensitivity parameter for plate-like structure suppression. Controls the weight of the ratio between the two largest eigenvalues.

`--beta` *val*
:   Sensitivity parameter for blob-like structure suppression. Controls the weight of the ratio that distinguishes blobs from tubes.

`--gamma` *val*
:   Sensitivity parameter for the structureness (Frobenius norm) term. Controls the overall background noise suppression.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

## EXAMPLES

Apply single-scale vesselness enhancement:

    itk_vesselness input.mnc vessels.mnc --sigma 1.0 --float

Apply multi-scale vesselness across a range of vessel diameters:

    itk_vesselness input.mnc vessels.mnc --min-sigma 0.5 --max-sigma 3.0 --steps 5 --float

Adjust sensitivity parameters for specific vessel characteristics:

    itk_vesselness input.mnc vessels.mnc --sigma 1.5 --alpha 0.5 --beta 0.5 --gamma 5.0 --float --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_laplace](itk_laplace), [itk_diffusion](itk_diffusion), [mincblur](mincblur), [minccalc](minccalc)
