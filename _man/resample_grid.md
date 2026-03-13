---
section: 1
title: resample_grid
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# resample_grid

apply an arbitrary transform to a deformation grid

`resample_grid <input> <xfm> <output.mnc> [options]`

## DESCRIPTION

**resample_grid** resamples a deformation grid (vector field) through a spatial
transformation. The input is a MINC deformation grid file (a 3D vector field
where each voxel stores an x, y, z displacement), and the transformation is
specified as a MINC .xfm file. The output is a new deformation grid defined on
the target sampling lattice.

This tool is useful for composing non-linear transformations, resampling
deformation fields onto different grids, or converting deformation fields
between coordinate systems. The `--like` option controls the output sampling
grid geometry, and `--invert` inverts the .xfm transformation before applying
it.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--like` *file*
:   Define the output sampling grid to match the geometry (dimensions, voxel spacing, starts, and direction cosines) of *file*.

`--invert`
:   Invert the .xfm transformation before applying it to the deformation grid.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

## EXAMPLES

Resample a deformation grid through a linear transform:

    resample_grid deformation.mnc linear.xfm resampled_grid.mnc

Resample to match the geometry of a target volume:

    resample_grid deformation.mnc transform.xfm output_grid.mnc --like target.mnc

Resample with an inverted transform and float output:

    resample_grid deformation.mnc transform.xfm output_grid.mnc --invert --float --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_resample](itk_resample), [itk_convert_xfm](itk_convert_xfm), [mincresample](mincresample), [xfmconcat](xfmconcat), [xfminvert](xfminvert)
