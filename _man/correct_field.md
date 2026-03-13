---
section: 1
title: correct_field
author: John G. Sled
group: Non-Uniformity Correction
---
# correct_field

apply a bias field correction to a MINC volume using a mask

`correct_field input.mnc mask.mnc output.mnc`

## DESCRIPTION

**correct_field** applies a bias field correction to a MINC volume. It takes an
input volume and a mask volume and produces a corrected output volume. The bias
field is typically estimated by **nu_estimate** or **spline_smooth** as part of
the N3 non-parametric non-uniform intensity normalization pipeline. The mask
defines the region of the volume over which the correction is applied.

## EXAMPLES

    correct_field input.mnc brain_mask.mnc output_corrected.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_correct](nu_correct), [nu_estimate](nu_estimate), [spline_smooth](spline_smooth), [evaluate_field](evaluate_field)
