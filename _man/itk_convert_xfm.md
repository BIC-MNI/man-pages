---
section: 1
title: itk_convert_xfm
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_convert_xfm

convert transformation files between ITK and MINC .xfm formats

`itk_convert_xfm <input> <output> [options]`

## DESCRIPTION

**itk_convert_xfm** converts spatial transformation files between MINC .xfm
format and ITK transformation formats. This allows transformations computed by
ITK-based registration tools (such as ANTs) to be used with MINC tools, and
vice versa.

The conversion direction is determined automatically from the file extensions
of the input and output arguments. The tool handles both linear (affine) and
non-linear (grid/deformation field) transformations.

The `--invert` option inverts the transformation during conversion, which is
useful when the source and target conventions differ between toolkits.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--invert`
:   Invert the transformation during conversion.

## EXAMPLES

Convert a MINC .xfm file to ITK format:

    itk_convert_xfm input.xfm output.txt

Convert an ITK transform to MINC .xfm format:

    itk_convert_xfm input.txt output.xfm --clobber

Convert and invert a transformation:

    itk_convert_xfm input.xfm output.txt --invert --verbose

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_resample](itk_resample), [itk_convert](itk_convert), [xfmconcat](xfmconcat), [xfminvert](xfminvert), [dircos_to_xfm](dircos_to_xfm)
