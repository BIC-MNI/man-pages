---
section: 1
title: c_param2grid
author: Vladimir S. Fonov
group: Distortion Correction
---
# c_param2grid

Convert cylindrical harmonic parameters to deformation grid.

`c_param2grid <parameters> <output_grid.mnc> [options]`

## DESCRIPTION

**c_param2grid** converts a cylindrical harmonic parameter file (produced by
`c_fit_harmonics_grids`) into a MINC deformation grid volume. The resulting
grid represents the distortion correction field that can be applied to
images using tools such as `mincresample` or `itk_resample`.

A reference MINC file can be provided with `--like` to define the sampling
grid geometry (dimensions, voxel size, and orientation). Alternatively, a
uniform step size can be specified.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--like` *file*
:   Use the specified MINC file as a template for the output grid geometry.

`--step` *val*
:   Set the voxel step size (in mm) for the output grid.

`--cylindrical`
:   Interpret parameters as cylindrical harmonics.

## EXAMPLES

    # Convert parameters to a grid using a reference volume
    c_param2grid distortion.par correction_grid.mnc --like reference.mnc

    # Convert with a specified step size
    c_param2grid distortion.par correction_grid.mnc --step 2.0

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[c_fit_harmonics_grids](c_fit_harmonics_grids) ,
[param2grid](param2grid)
