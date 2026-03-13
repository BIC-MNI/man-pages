---
section: 1
title: grid_2_log
author: Vladimir S. Fonov
group: Deformable Registration
---
# grid_2_log

Convert deformation field to log-domain velocity field (or compute exponent).

`grid_2_log <input> <output> [options]`

## DESCRIPTION

**grid_2_log** converts a standard deformation field into its log-domain
velocity field representation using an iterative Baker-Campbell-Hausdorff (BCH)
approximation. The resulting velocity field can be exponentiated via scaling
and squaring to recover the original deformation.

When the `--exp` flag is given, the tool performs the inverse operation:
it exponentiates a velocity field to produce a deformation field. A scaling
factor can be applied to the velocity field before exponentiation.

This tool is essential for log-domain diffeomorphic registration workflows
where deformations must be represented as stationary velocity fields.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--iter` *n*
:   Number of iterations for the BCH approximation (default: 10).

`--sigma` *f*
:   Smoothing sigma for regularization (default: 2).

`--approx` *n*
:   Number of BCH terms to use in the approximation (default: 3).

`--steps` *n*
:   Number of integration steps for scaling and squaring (default: 500).

`--byte`
:   Store output voxels as unsigned byte.

`--short`
:   Store output voxels as short integer.

`--float`
:   Store output voxels as single-precision floating point.

`--exp`
:   Compute the exponent of the velocity field instead of the logarithm.

`--factor` *f*
:   Multiply the velocity field by this factor before exponentiation.

## EXAMPLES

    # Convert a deformation field to a log-domain velocity field
    grid_2_log deformation.mnc velocity.mnc

    # Convert with custom iteration count and BCH terms
    grid_2_log deformation.mnc velocity.mnc --iter 20 --approx 4

    # Exponentiate a velocity field to recover the deformation
    grid_2_log velocity.mnc deformation.mnc --exp

    # Apply a scaling factor during exponentiation
    grid_2_log velocity.mnc scaled_deformation.mnc --exp --factor 0.5

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[grid_proc](grid_proc) ,
[grid_statistics](grid_statistics) ,
[LogDomainDemonsRegistration](LogDomainDemonsRegistration)
