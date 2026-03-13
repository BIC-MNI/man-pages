---
section: 1
title: itk_fill_hole
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_fill_hole

apply hole-filling operation to a volume

`itk_fill_hole <input> <output> [options]`

## DESCRIPTION

**itk_fill_hole** fills holes in a grayscale image volume using the ITK
grayscale fill-hole filter. A "hole" is defined as a connected region of dark
voxels that is completely surrounded by brighter voxels. The filter raises the
intensity of hole regions to match the surrounding level, effectively filling
in valleys in the intensity landscape.

This operation is useful for correcting intensity inhomogeneities,
removing dark artefacts inside structures, and preparing volumes for
subsequent segmentation or thresholding steps.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Fill holes in a grayscale volume:

    itk_fill_hole input.mnc filled.mnc

Fill holes with verbose output, overwriting existing file:

    itk_fill_hole input.mnc filled.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_morph](itk_morph), [itk_g_morph](itk_g_morph), [minccalc](minccalc), [mincmorph](mincmorph)
