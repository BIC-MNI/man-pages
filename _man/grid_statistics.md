---
section: 1
title: grid_statistics
author: Vladimir S. Fonov
group: Deformable Registration
---
# grid_statistics

Compute statistics on deformation grid: Jacobian, harmonic energy, magnitude.

`grid_statistics <input_field> [options]`

## DESCRIPTION

**grid_statistics** computes various statistics from a deformation grid field
stored in MINC format. It can output the Jacobian determinant, displacement
magnitude, and determinant maps as separate volumes, and optionally compute
harmonic energy. Results can be restricted to a mask region and exported in
CSV format for further analysis.

This tool is commonly used to assess the quality and properties of
deformation fields produced by non-linear registration.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--jacobian` *file*
:   Write the Jacobian determinant map to the specified MINC file.

`--mag` *file*
:   Write the displacement magnitude map to the specified MINC file.

`--det` *file*
:   Write the determinant map to the specified MINC file.

`--log`
:   Compute the log of the Jacobian determinant.

`--mask` *file*
:   Restrict statistics computation to voxels within the specified mask volume.

`--csv`
:   Output statistics in CSV format.

## EXAMPLES

    # Compute Jacobian determinant from a deformation field
    grid_statistics deformation.mnc --jacobian jacobian.mnc

    # Compute magnitude and Jacobian with a mask
    grid_statistics deformation.mnc --mag magnitude.mnc --jacobian jacobian.mnc \
        --mask brain_mask.mnc

    # Output statistics in CSV format
    grid_statistics deformation.mnc --csv --mask brain_mask.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[grid_proc](grid_proc) ,
[grid_2_log](grid_2_log) ,
[DemonsRegistration](DemonsRegistration)
