---
section: 1
title: field2imp
author: John G. Sled
group: Non-Uniformity Correction
---
# field2imp

convert a bias field MINC volume to an IMP format compact representation

`field2imp [options] <input.mnc> <output.imp>`

## DESCRIPTION

**field2imp** is a Perl script that converts a bias field stored as a MINC
volume into an IMP format compact representation. The IMP format is used
internally by the N3 non-uniformity correction pipeline to store field
estimates in a compact spline-based form. This tool is the inverse of
**imp2field**.

## EXAMPLES

    field2imp bias_field.mnc field.imp

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[imp2field](imp2field), [evaluate_field](evaluate_field), [spline_smooth](spline_smooth), [nu_correct](nu_correct)
