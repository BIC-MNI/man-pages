---
section: 1
title: resample_labels
author: John G. Sled
group: Non-Uniformity Correction
---
# resample_labels

resample a labelled MINC volume to match a template

`resample_labels [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**resample_labels** is a Perl script that resamples a label volume to a
different sampling grid while preserving label values. Unlike standard
resampling which interpolates intensity values, this tool uses nearest-neighbour
interpolation to ensure that discrete label values are not corrupted by
averaging. This is part of the N3 package and is useful when label volumes need
to be aligned with volumes at different resolutions.

## EXAMPLES

    resample_labels labels.mnc resampled_labels.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[mincresample](mincresample), [nu_correct](nu_correct), [classify](classify)
