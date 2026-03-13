---
section: 1
title: sharpen_volume
author: John G. Sled
group: Non-Uniformity Correction
---
# sharpen_volume

apply histogram sharpening to a MINC volume

`sharpen_volume [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**sharpen_volume** is a Perl script that sharpens the intensity histogram of a
MINC volume to improve contrast between tissue classes. It computes the
intensity histogram using **volume_hist**, deconvolves it using **sharpen_hist**,
and then applies the resulting lookup table to remap the volume intensities.
This process is part of the N3 non-uniformity correction pipeline where
histogram sharpening is used to estimate and remove the bias field.

## EXAMPLES

    sharpen_volume input.mnc sharpened.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[sharpen_hist](sharpen_hist), [volume_hist](volume_hist), [nu_correct](nu_correct), [minclookup](minclookup)
