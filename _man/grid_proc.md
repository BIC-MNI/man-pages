---
section: 1
title: grid_proc
author: Vladimir S. Fonov
group: Deformable Registration
---
# grid_proc

Perform operations on deformation grids: log, exp, magnitude, determinant, inverse.

`grid_proc <in_grid.mnc> <out_grid.mnc> [options]`

## DESCRIPTION

**grid_proc** performs various mathematical operations on MINC deformation grid
files. Supported operations include computing the matrix logarithm or
exponential of a deformation field, extracting the displacement magnitude or
Jacobian determinant, inverting the field, and computing harmonic energy.
The output data type can be controlled.

This utility is used for manipulating deformation fields in registration
pipelines, particularly when converting between standard and log-domain
representations.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--log`
:   Compute the log of the deformation field.

`--exp`
:   Compute the exponential of the deformation field (scaling and squaring).

`--mag`
:   Compute the displacement magnitude at each voxel.

`--det`
:   Compute the Jacobian determinant at each voxel.

`--inv`
:   Invert the deformation field.

`--harmonic`
:   Compute the harmonic energy of the deformation field.

`--float`
:   Store output voxels as single-precision floating point.

`--double`
:   Store output voxels as double-precision floating point.

## EXAMPLES

    # Compute the log of a deformation field
    grid_proc deformation.mnc log_field.mnc --log

    # Exponentiate a velocity field back to a deformation
    grid_proc velocity.mnc deformation.mnc --exp

    # Compute displacement magnitude
    grid_proc deformation.mnc magnitude.mnc --mag

    # Invert a deformation field
    grid_proc forward.mnc inverse.mnc --inv

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[grid_statistics](grid_statistics) ,
[grid_2_log](grid_2_log) ,
[log_resample](log_resample)
