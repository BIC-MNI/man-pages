---
section: 1
title: nu_correct_norm
author: Andrew Janke
group: Intensity Normalization
---
# nu_correct_norm

perform combined non-uniformity correction and intensity normalization

`nu_correct_norm [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**nu_correct_norm** is a Perl script that performs combined N3 non-uniformity
correction and intensity normalization in a single pipeline. It wraps
**nu_correct** for bias field estimation and removal, then applies intensity
normalization to standardize the output values.

This combined approach is more efficient than running nu_correct and intensity
normalization as separate steps, and ensures that the non-uniformity correction
and normalization are applied consistently.

The script is commonly used as a preprocessing step before tissue classification
or other quantitative analyses that require both uniform intensity and
standardized intensity ranges.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite the output file if it already exists.

`-mask <file>`
:   Specify a brain mask to restrict the region used for bias field and intensity
    estimation.

`-model <file>`
:   Specify the intensity model file to use as the normalization reference.

## EXAMPLES

Correct and normalize a T1-weighted volume:

    nu_correct_norm t1_raw.mnc t1_corrected.mnc

Correct and normalize with a brain mask:

    nu_correct_norm -mask brain_mask.mnc t1_raw.mnc t1_corrected.mnc

Correct and normalize with a specific model and verbose output:

    nu_correct_norm -verbose -clobber -model /opt/models/icbm_t1.mnc t1_raw.mnc t1_corrected.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[nu_correct](nu_correct) [normalize_mri](normalize_mri) [inormalize](inormalize)
