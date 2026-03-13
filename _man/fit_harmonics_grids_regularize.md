---
section: 1
title: fit_harmonics_grids_regularize
author: Vladimir S. Fonov
group: Distortion Correction
---
# fit_harmonics_grids_regularize

Spherical harmonic fitting with Legendre polynomial regularization.

`fit_harmonics_grids_regularize <grid1> <mask1> [...] <output.par> [options]`

## DESCRIPTION

**fit_harmonics_grids_regularize** fits spherical harmonic coefficients to
deformation grids with an additional Legendre polynomial regularization term.
The regularization penalizes high-order coefficients to produce smoother
distortion models and reduce overfitting, particularly when the input data
is noisy or sparsely sampled.

The regularization strength is controlled by the `--lambda` parameter. Higher
values produce smoother fits at the expense of fitting accuracy, while lower
values allow the model to follow the data more closely.

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

`--lambda` *val*
:   Regularization weight. Higher values produce smoother fits (default: 0).

## EXAMPLES

    # Regularized fit with default lambda
    fit_harmonics_grids_regularize grid.mnc mask.mnc output.par --order 10

    # Strong regularization for noisy data
    fit_harmonics_grids_regularize grid.mnc mask.mnc output.par \
        --order 12 --lambda 0.1

    # Joint regularized fit across multiple grids
    fit_harmonics_grids_regularize grid1.mnc mask1.mnc grid2.mnc mask2.mnc \
        output.par --order 10 --lambda 0.01 --skip 2

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[fit_harmonics_grids](fit_harmonics_grids) ,
[fit_harmonics_grids_diff](fit_harmonics_grids_diff) ,
[param2grid](param2grid)
