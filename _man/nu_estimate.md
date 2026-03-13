---
section: 1
title: nu_estimate
author: John G. Sled
group: Non-Uniformity Correction
---
# nu_estimate

estimate the non-uniformity field in an MRI volume

`nu_estimate [options] <input.mnc> <output.imp>`

## DESCRIPTION

**nu_estimate** is a Perl script that estimates the non-uniformity (bias) field
from an MRI volume using the N3 algorithm. The N3 method is a non-parametric
approach that estimates the multiplicative bias field by sharpening the
intensity histogram of the volume. The estimated field is output in a compact
IMP format that can be evaluated on a volume grid using **evaluate_field** or
applied using **correct_field**.

## EXAMPLES

    nu_estimate input.mnc field_estimate.imp

    nu_estimate -mask brain_mask.mnc input.mnc field_estimate.imp

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_correct](nu_correct), [nu_evaluate](nu_evaluate), [evaluate_field](evaluate_field), [correct_field](correct_field), [spline_smooth](spline_smooth), [sharpen_hist](sharpen_hist)
