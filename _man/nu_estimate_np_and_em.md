---
section: 1
title: nu_estimate_np_and_em
author: John G. Sled
group: Non-Uniformity Correction
---
# nu_estimate_np_and_em

estimate non-uniformity using non-parametric and EM methods

`nu_estimate_np_and_em [options] <input.mnc> <output.imp>`

## DESCRIPTION

**nu_estimate_np_and_em** is a Perl script that estimates the non-uniformity
(bias) field from an MRI volume using a combined approach of non-parametric
(N3) and expectation-maximization (EM) methods. This hybrid approach can
provide improved field estimates compared to using either method alone,
particularly in cases where tissue classification information can help
constrain the field estimation. The estimated field is output in a compact IMP
format.

## EXAMPLES

    nu_estimate_np_and_em input.mnc field_estimate.imp

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_estimate](nu_estimate), [nu_correct](nu_correct), [nu_evaluate](nu_evaluate), [classify](classify)
