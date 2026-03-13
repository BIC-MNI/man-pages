---
section: 1
title: imp2field
author: John G. Sled
group: Non-Uniformity Correction
---
# imp2field

convert an IMP format compact representation to a bias field MINC volume

`imp2field [options] <input.imp> <output.mnc>`

## DESCRIPTION

**imp2field** is a Perl script that converts an IMP format compact
representation of a bias field into a MINC volume. The IMP format is used
internally by the N3 non-uniformity correction pipeline to store field
estimates in a compact spline-based form. This tool is the inverse of
**field2imp**.

## EXAMPLES

    imp2field field.imp bias_field.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[field2imp](field2imp), [evaluate_field](evaluate_field), [spline_smooth](spline_smooth), [nu_correct](nu_correct)
