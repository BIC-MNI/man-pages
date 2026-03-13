---
section: 1
title: itk_diffusion
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_diffusion

apply anisotropic diffusion filtering to a volume

`itk_diffusion <input> <output> [options]`

## DESCRIPTION

**itk_diffusion** applies anisotropic diffusion filtering to an image volume
using the Insight Toolkit (ITK). This edge-preserving smoothing technique
reduces noise while retaining important structural boundaries. It is
particularly useful as a preprocessing step for segmentation and registration
of medical images.

Two diffusion models are available. The default gradient-magnitude model
(Perona-Malik) uses the gradient magnitude to control the diffusion rate,
reducing smoothing near strong edges. The alternative curvature model
(`--curvature`) uses curvature-driven diffusion, which better preserves thin
structures and sharp corners.

The strength of the filtering is controlled by the number of iterations
(`--iter`) and the conductance parameter (`--conduct`). Higher conductance
values allow more diffusion across edges; lower values restrict smoothing
to homogeneous regions.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--iter` *n*
:   Number of diffusion iterations. More iterations produce stronger smoothing. Default is 5.

`--conduct` *val*
:   Conductance parameter controlling edge sensitivity. Higher values smooth more aggressively across edges. Default is 1.0.

`--curvature`
:   Use the curvature anisotropic diffusion model instead of the default gradient magnitude model. The curvature model better preserves thin structures and sharp corners.

## EXAMPLES

Apply default gradient-based anisotropic diffusion:

    itk_diffusion input.mnc smoothed.mnc

Apply 10 iterations with low conductance for strong edge preservation:

    itk_diffusion input.mnc smoothed.mnc --iter 10 --conduct 0.5

Use the curvature diffusion model:

    itk_diffusion input.mnc smoothed.mnc --curvature --iter 8 --conduct 1.5

Overwrite an existing output:

    itk_diffusion noisy.mnc filtered.mnc --iter 20 --conduct 2.0 --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_laplace](itk_laplace), [itk_laplacian_sharpening](itk_laplacian_sharpening), [mincblur](mincblur), [itk_g_morph](itk_g_morph)
