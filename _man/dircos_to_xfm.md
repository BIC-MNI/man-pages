---
section: 1
title: dircos_to_xfm
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# dircos_to_xfm

convert direction cosines to an .xfm transformation file

`dircos_to_xfm <input> <output> [options]`

## DESCRIPTION

**dircos_to_xfm** extracts the direction cosines and start coordinates from a
MINC image file and writes a corresponding MINC .xfm linear transformation
file. The resulting transformation maps from the canonical (world) coordinate
system to the voxel-aligned coordinate system defined by the input image's
direction cosines.

This is useful when a MINC volume has non-standard direction cosines (e.g.,
oblique acquisitions) and you need a transformation that captures the
orientation for use with other tools such as **mincresample** or
**itk_resample**. The extracted .xfm can also be composed with other
transformations using **xfmconcat**.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Extract direction cosines from an oblique MRI scan:

    dircos_to_xfm oblique.mnc orientation.xfm

Overwrite an existing output file:

    dircos_to_xfm input.mnc output.xfm --clobber --verbose

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_convert_xfm](itk_convert_xfm), [mincinfo](mincinfo), [mincresample](mincresample), [xfmconcat](xfmconcat), [xfminvert](xfminvert)
