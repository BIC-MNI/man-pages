---
section: 1
title: make_template
author: John G. Sled
group: Non-Uniformity Correction
---
# make_template

create a sampling template volume for N3 non-uniformity correction

`make_template [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**make_template** is a Perl script that creates a template volume used by the
N3 non-uniformity correction pipeline. The template defines the sampling grid
on which the non-uniformity field is estimated. It is typically generated from
the input MRI volume and used by **nu_estimate** during field estimation.

## EXAMPLES

    make_template input.mnc template.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_correct](nu_correct), [nu_estimate](nu_estimate), [spline_smooth](spline_smooth)
