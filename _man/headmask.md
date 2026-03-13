---
section: 1
title: headmask
author: Andrew Janke
group: Intensity Normalization
---
# headmask

create a head mask for MRI intensity normalization

`headmask [options] <input.mnc> <output_mask.mnc>`

## DESCRIPTION

**headmask** is a Perl script that creates a binary head mask from a T1-weighted
MRI volume. The mask identifies the head region (including skull and brain)
separated from the background air.

The script works by first applying non-uniformity correction using **nu_correct**
to reduce intensity bias, then using intensity thresholding to separate the head
from the background. Morphological operations are applied to clean up the
resulting mask, filling holes and removing small isolated regions.

The resulting head mask is useful as an initialization step for intensity
normalization pipelines, providing a region of interest that excludes background
noise while retaining all head tissues.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite the output file if it already exists.

`-threshold <val>`
:   Set the intensity threshold value for separating head from background.
    Voxels with intensity above this threshold are included in the mask.

## EXAMPLES

Create a head mask with default threshold:

    headmask t1.mnc head_mask.mnc

Create a head mask with a custom threshold and verbose output:

    headmask -verbose -clobber -threshold 50 t1.mnc head_mask.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[lgmask](lgmask) [inormalize](inormalize) [nu_correct](nu_correct)
