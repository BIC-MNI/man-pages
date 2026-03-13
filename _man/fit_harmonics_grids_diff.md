---
section: 1
title: fit_harmonics_grids_diff
author: Vladimir S. Fonov
group: Distortion Correction
---
# fit_harmonics_grids_diff

Spherical harmonic fitting using paired linear/nonlinear transform differentials.

`fit_harmonics_grids_diff <lin_xfm1> <nl_xfm1> <mask1> [...] [options]`

## DESCRIPTION

**fit_harmonics_grids_diff** fits spherical harmonic coefficients to
distortion fields derived from the difference between paired linear and
nonlinear transforms. For each input triplet, the tool computes the
displacement between the linear and nonlinear transforms within the masked
region, then fits spherical harmonics to the resulting differential field.

This approach is useful when distortion is estimated by comparing a linear
(affine) registration with a nonlinear registration of the same data. The
difference isolates the nonlinear distortion component, which is then
modelled parametrically using spherical harmonics.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--order` *n*
:   Maximum order of the spherical harmonic expansion.

`--skip` *n*
:   Skip every *n*-th voxel during fitting to reduce computation time.

`--limit` *val*
:   Exclude voxels with displacement magnitude above this threshold.

`--par` *file*
:   Initialize fitting from an existing parameter file.

`-o`, `--output` *file*
:   Write the fitted parameter file to the specified path.

## EXAMPLES

    # Fit harmonics from a single linear/nonlinear pair
    fit_harmonics_grids_diff linear.xfm nonlinear.xfm mask.mnc \
        -o output.par --order 10

    # Fit from multiple transform pairs
    fit_harmonics_grids_diff lin1.xfm nl1.xfm mask1.mnc \
        lin2.xfm nl2.xfm mask2.mnc -o output.par --order 12

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[fit_harmonics_grids](fit_harmonics_grids) ,
[fit_harmonics_grids_regularize](fit_harmonics_grids_regularize)
