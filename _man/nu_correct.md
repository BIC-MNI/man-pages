---
section: 1
title: nu_correct
author: John G. Sled
group: Non-Uniformity Correction
---
# nu_correct

correct intensity non-uniformity artifacts in MRI volumes

`nu_correct [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**nu_correct** is the main command of the N3 (Non-parametric Non-uniform
intensity Normalization) package. It corrects intensity non-uniformity (bias
field) artifacts in MRI volumes. The N3 algorithm iteratively estimates and
removes the smooth, multiplicative bias field that is a common artifact in MR
images due to RF coil inhomogeneity and other factors.

**nu_correct** is a Perl script that orchestrates the full correction pipeline,
calling **nu_estimate** to estimate the field, **evaluate_field** to evaluate
it, and **correct_field** to apply the correction. It supports iterative
refinement of the field estimate.

## EXAMPLES

    nu_correct input.mnc output_corrected.mnc

    nu_correct -mask brain_mask.mnc input.mnc output_corrected.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_estimate](nu_estimate), [nu_evaluate](nu_evaluate), [correct_field](correct_field), [evaluate_field](evaluate_field), [spline_smooth](spline_smooth), [sharpen_volume](sharpen_volume)
