---
section: 1
title: param2grid
author: Vladimir S. Fonov
group: Distortion Correction
---
# param2grid

Convert spherical harmonic parameters to deformation grid.

`param2grid <parameters> <output_grid.mnc> [options]`

## DESCRIPTION

**param2grid** evaluates a spherical harmonic parameter file (produced by
`fit_harmonics_grids` or related tools) on a regular 3D grid and writes the
resulting deformation field as a MINC volume. The output grid can then be
used to correct geometric distortions by applying it as a nonlinear
transform in resampling tools.

A reference MINC file can be provided with `--like` to define the output grid
geometry. Alternatively, a uniform step size can be specified.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--like` *file*
:   Use the specified MINC file as a template for the output grid geometry
    (dimensions, voxel size, start coordinates, direction cosines).

`--step` *val*
:   Set the voxel step size (in mm) for the output grid.

## EXAMPLES

    # Generate a correction grid from fitted parameters
    param2grid distortion.par correction_grid.mnc --like reference.mnc

    # Generate a grid with a specific step size
    param2grid distortion.par correction_grid.mnc --step 2.0

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[fit_harmonics_grids](fit_harmonics_grids) ,
[c_param2grid](c_param2grid)
