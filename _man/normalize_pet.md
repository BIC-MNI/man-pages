---
section: 1
title: normalize_pet
author: David MacDonald
group: Volume Operations
---
# normalize_pet

intensity normalize a PET MINC volume

`normalize_pet [options] <norm.mnc> [<in.mnc>] <out.mnc>`

## DESCRIPTION

**normalize_pet** performs intensity normalization on a PET (Positron
Emission Tomography) MINC volume. The program scales the intensity values
so that the mean value within a specified mask region equals the target
normalized mean.

If both *in.mnc* and *out.mnc* are specified, the normalization factor is
computed from *norm.mnc* and applied to *in.mnc*, writing the result to
*out.mnc*. If only *out.mnc* is specified, the normalization is computed
from and applied to *norm.mnc*.

## OPTIONS

`-mask` maskfile
:   Specify a mask file to restrict normalization to a region of interest.
    Only voxels within the mask are used to compute the normalization factor.

`-normalized_mean` value
:   Target mean value for the normalized volume. Default: 100.

## EXAMPLES

Normalize a PET volume to a mean of 100:

    normalize_pet pet.mnc normalized.mnc

Normalize using a mask and apply to a different volume:

    normalize_pet -mask brain_mask.mnc -normalized_mean 50 norm.mnc input.mnc output.mnc

## SEE ALSO

[inormalize](inormalize), [mincmath](mincmath)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
