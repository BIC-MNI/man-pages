---
section: 1
title: itk_morph
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_morph

perform binary morphological image operations (dilate, erode, open, close)

`itk_morph <input> <output> [options]`

## DESCRIPTION

**itk_morph** applies binary morphological operations to a volume using the
Insight Toolkit (ITK). Operations are specified through an expression string
(`--exp`) composed of single-character operation codes. Multiple operations
can be chained in sequence within a single expression, and each operation uses
the structuring element radius set by `--radius`.

The input image is first binarized using either a fixed threshold (`--threshold`)
or automatic bimodal threshold estimation (`--bimodal`). The supported operations
are: **D** (dilate), **E** (erode), **M** (median filter), **T** (binary
thinning), **P** (pruning), **I** (inversion), **S** (threshold / binarize),
and **A** (add / union with the original input). Combining these operations
allows standard compound operations such as morphological opening (ED) and
closing (DE).

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--exp` *str*
:   Specify the morphological expression string. Operation codes: **D** = dilate, **E** = erode, **M** = median, **T** = thin, **P** = prune, **I** = invert, **S** = threshold/binarize, **A** = add (union with original).

`--bimodal`
:   Use bimodal (Otsu) threshold estimation to automatically binarize the input before applying morphological operations.

`--threshold` *val*
:   Set a fixed threshold value for binarizing the input image. Voxels above this value are set to 1; all others are set to 0.

`--radius` *r*
:   Set the radius (in voxels) of the structuring element used for morphological operations. Default is 1.

## EXAMPLES

Erode a binary mask with a radius of 2:

    itk_morph mask.mnc eroded.mnc --exp E --radius 2

Dilate then erode (morphological closing):

    itk_morph mask.mnc closed.mnc --exp DE --radius 1

Apply automatic thresholding followed by dilation:

    itk_morph input.mnc output.mnc --bimodal --exp D --radius 3

Erode then dilate (morphological opening) with a fixed threshold:

    itk_morph input.mnc output.mnc --threshold 0.5 --exp ED --radius 1

Invert a binary mask:

    itk_morph mask.mnc inverted.mnc --exp I

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_g_morph](itk_g_morph), [mincmorph](mincmorph), [itk_distance](itk_distance), [minccalc](minccalc)
