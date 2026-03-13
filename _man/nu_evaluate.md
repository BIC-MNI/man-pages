---
section: 1
title: nu_evaluate
author: John G. Sled
group: Non-Uniformity Correction
---
# nu_evaluate

evaluate and apply a non-uniformity correction to an MRI volume

`nu_evaluate [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**nu_evaluate** is a Perl script that evaluates a previously estimated
non-uniformity field and applies the correction to an MRI volume. It takes a
field estimate (typically produced by **nu_estimate**) and applies it to the
input volume to produce a corrected output. This tool provides a way to
separate the estimation and application steps of the N3 correction pipeline.

## EXAMPLES

    nu_evaluate input.mnc corrected.mnc

    nu_evaluate -mapping field_estimate.imp input.mnc corrected.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_estimate](nu_estimate), [nu_correct](nu_correct), [evaluate_field](evaluate_field), [correct_field](correct_field)
