---
section: 1
title: itk_laplacian_sharpening
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_laplacian_sharpening

apply Laplacian sharpening filter to a volume

`itk_laplacian_sharpening <input> <output> [options]`

## DESCRIPTION

**itk_laplacian_sharpening** applies a Laplacian sharpening filter to an image
volume using the Insight Toolkit (ITK). The filter enhances edges and fine
detail by subtracting a Laplacian-filtered version of the image from the
original. This has the effect of amplifying high-frequency components,
making transitions between different tissue types and structural boundaries
more prominent.

Laplacian sharpening is useful as a preprocessing step to improve the
contrast of boundaries before segmentation, registration, or visual
inspection of medical images.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Apply Laplacian sharpening to enhance edges:

    itk_laplacian_sharpening input.mnc sharpened.mnc

Apply with verbose output and overwrite existing file:

    itk_laplacian_sharpening input.mnc sharpened.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_laplace](itk_laplace), [itk_diffusion](itk_diffusion), [mincblur](mincblur), [minccalc](minccalc)
