---
section: 1
title: lgmask
author: Andrew Janke
group: Intensity Normalization
---
# lgmask

create a large-structure brain mask for intensity normalization

`lgmask [options] <input.mnc> <output_mask.mnc>`

## DESCRIPTION

**lgmask** is a Perl script that creates a large-region brain mask from an MRI
volume. The mask captures the major brain structures and is intended for use as
an initialization step in intensity normalization pipelines.

Unlike a precise brain extraction, lgmask produces a coarse mask that broadly
covers the brain region. This is sufficient for estimating intensity normalization
parameters where an approximate region of interest is needed rather than an exact
brain boundary.

The script uses a combination of thresholding and morphological operations to
identify the large brain region from the input volume.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Create a large brain mask:

    lgmask t1.mnc brain_mask.mnc

Create a mask with verbose output, overwriting existing files:

    lgmask -verbose -clobber t1.mnc brain_mask.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[headmask](headmask) [inormalize](inormalize) [nu_correct](nu_correct)
