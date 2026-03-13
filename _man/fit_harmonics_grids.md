---
section: 1
title: fit_harmonics_grids
author: Vladimir S. Fonov
group: Distortion Correction
---
# fit_harmonics_grids

Fit spherical harmonic coefficients to deformation grids.

`fit_harmonics_grids <grid1> <mask1> [<grid2> <mask2> ...] <output.par> [options]`

## DESCRIPTION

**fit_harmonics_grids** fits spherical harmonic basis functions to one or more
deformation grid volumes to produce a compact parametric model of the
distortion field. Each deformation grid must be paired with a corresponding
mask that defines the fitting region.

Spherical harmonics provide a smooth, global basis that is well-suited for
modelling slowly varying geometric distortions such as those caused by
gradient non-linearity in MRI scanners. The fitted coefficients are saved to
a parameter file that can later be evaluated on an arbitrary grid using
`param2grid`.

Multiple grid/mask pairs allow joint fitting across different acquisitions or
phantom positions.

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

## EXAMPLES

    # Fit spherical harmonics to a single grid/mask pair
    fit_harmonics_grids grid.mnc mask.mnc output.par --order 10

    # Joint fit across multiple acquisitions
    fit_harmonics_grids grid1.mnc mask1.mnc grid2.mnc mask2.mnc \
        output.par --order 12

    # Fit with voxel skipping and displacement limit
    fit_harmonics_grids grid.mnc mask.mnc output.par \
        --order 8 --skip 2 --limit 10.0

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[fit_harmonics_grids_diff](fit_harmonics_grids_diff) ,
[fit_harmonics_grids_regularize](fit_harmonics_grids_regularize) ,
[param2grid](param2grid)
