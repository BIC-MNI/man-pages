---
section: 1
title: c_fit_harmonics_grids
author: Vladimir S. Fonov
group: Distortion Correction
---
# c_fit_harmonics_grids

Fit cylindrical harmonic coefficients to deformation grids for distortion correction.

`c_fit_harmonics_grids <grid1> <mask1> [<grid2> <mask2> ...] <output.par> [options]`

## DESCRIPTION

**c_fit_harmonics_grids** fits cylindrical harmonic basis functions to one or
more deformation grid files to estimate a parametric model of geometric
distortion. Each deformation grid is paired with a mask that defines the
region over which the fitting is performed.

The cylindrical harmonic model is particularly suited for correcting
gradient-coil-induced distortions in MRI, where the distortion pattern has
cylindrical symmetry. The fitted coefficients are written to a parameter file
that can be converted to a correction grid using `c_param2grid`.

Multiple grid/mask pairs can be provided to perform a joint fit across
several acquisitions, improving robustness.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--order` *n*
:   Maximum order of the cylindrical harmonic expansion.

`--skip` *n*
:   Skip every *n*-th voxel during fitting to reduce computation time.

`--cylindrical`
:   Use cylindrical harmonic basis functions (default behaviour).

`--limit` *val*
:   Exclude voxels with displacement magnitude above this threshold.

`--par` *file*
:   Initialize fitting from an existing parameter file.

## EXAMPLES

    # Fit cylindrical harmonics to a single grid/mask pair
    c_fit_harmonics_grids grid.mnc mask.mnc output.par --order 10

    # Fit using multiple grid/mask pairs with outlier rejection
    c_fit_harmonics_grids grid1.mnc mask1.mnc grid2.mnc mask2.mnc \
        output.par --order 12 --limit 5.0

    # Use voxel skipping for faster fitting
    c_fit_harmonics_grids grid.mnc mask.mnc output.par --order 8 --skip 2

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[c_param2grid](c_param2grid) ,
[fit_harmonics_grids](fit_harmonics_grids) ,
[phantomfit.pl](phantomfit.pl)
