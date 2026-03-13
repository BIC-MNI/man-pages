---
section: 1
title: normalize_mri
author: Andrew Janke
group: Intensity Normalization
---
# normalize_mri

normalize MRI intensity values using a standard approach

`normalize_mri [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**normalize_mri** is a Perl script that normalizes MRI intensity values using N3
inhomogeneity correction and intensity standardization. The script performs a
combined pipeline of non-uniformity correction followed by intensity normalization
to produce a volume with standardized intensity values.

The normalization process includes:

1. Non-uniformity correction using **nu_correct** to remove intensity bias
2. Intensity standardization to match a reference model, ensuring consistent
   intensity values across different scans and scanners

This is useful for multi-subject studies where consistent intensity values are
required for reliable tissue classification, voxel-based morphometry, or other
quantitative analyses.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite the output file if it already exists.

`-model <file>`
:   Specify the intensity model file to use as the normalization reference.

`-mask <file>`
:   Specify a brain mask to restrict the region used for intensity estimation.

## EXAMPLES

Normalize a T1-weighted MRI volume:

    normalize_mri t1_raw.mnc t1_normalized.mnc

Normalize with a specific model and brain mask:

    normalize_mri -model /opt/models/icbm_t1.mnc -mask brain_mask.mnc t1_raw.mnc t1_normalized.mnc

Normalize with verbose output:

    normalize_mri -verbose -clobber t1_raw.mnc t1_normalized.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[nu_correct](nu_correct) [inormalize](inormalize) [nu_correct_norm](nu_correct_norm)
