---
section: 1
title: itk_g_morph
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_g_morph

perform gray-scale morphological operations on a volume

`itk_g_morph <input> <output> [options]`

## DESCRIPTION

**itk_g_morph** applies grayscale morphological operations to a volume using the
Insight Toolkit (ITK). Unlike **itk_morph**, which operates on binary images,
**itk_g_morph** works directly on the continuous intensity values of the input
volume. This is useful for non-uniform illumination correction, feature
enhancement, and noise reduction without prior binarization.

Operations are specified through an expression string (`--exp`) using
single-character codes. The structuring element radius is controlled with
`--radius`. Compound operations such as grayscale opening (erode then dilate)
and closing (dilate then erode) can be built by chaining codes.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--exp` *str*
:   Specify the morphological expression string. Operation codes: **D** = grayscale dilate, **E** = grayscale erode, **M** = grayscale median filter.

`--radius` *r*
:   Set the radius (in voxels) of the structuring element. Default is 1.

## EXAMPLES

Apply grayscale dilation with radius 2:

    itk_g_morph input.mnc dilated.mnc --exp D --radius 2

Apply grayscale morphological closing (dilate then erode):

    itk_g_morph input.mnc closed.mnc --exp DE --radius 1

Apply a grayscale median filter:

    itk_g_morph input.mnc median.mnc --exp M --radius 2

Apply grayscale morphological opening (erode then dilate):

    itk_g_morph input.mnc opened.mnc --exp ED --radius 3 --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_morph](itk_morph), [mincmorph](mincmorph), [itk_diffusion](itk_diffusion), [minccalc](minccalc)
