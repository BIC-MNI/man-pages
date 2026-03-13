---
section: 1
title: uniformize_minc.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# uniformize_minc.pl

resample a MINC volume to a uniform axis-aligned grid

`uniformize_minc.pl <input.mnc> <output.mnc> [options]`

## DESCRIPTION

**uniformize_minc.pl** resamples a MINC volume onto a uniform, axis-aligned
(orthogonal) voxel grid. This is useful for volumes acquired with oblique slice
orientations or non-isotropic voxel spacing, converting them to a standard
sampling where the voxel axes are aligned with the world coordinate axes at a
uniform step size.

The script wraps **mincresample** with options to set the output voxel step size,
interpolation method, and output data type. An optional spatial transformation
can be applied during resampling.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--step <f>`
:   Isotropic voxel step size in millimetres for the output grid. Default: 1.0.

`--resample <type>`
:   Interpolation method to use for resampling. Accepted values include
    `trilinear`, `tricubic`, and `nearest_neighbour`. Default: tricubic.

`--transform <xfm>`
:   Apply the specified XFM transformation during resampling.

`--datatype <type>`
:   Output voxel data type (e.g. `byte`, `short`, `float`, `double`).

`--invert_transform`
:   Invert the transformation before applying it.

## EXAMPLES

Resample a volume to 1 mm isotropic with default tricubic interpolation:

    uniformize_minc.pl input.mnc output.mnc

Resample to 0.5 mm isotropic with trilinear interpolation:

    uniformize_minc.pl input.mnc output.mnc --step 0.5 --resample trilinear

Resample with a transformation applied:

    uniformize_minc.pl input.mnc output.mnc \
        --transform to_standard.xfm --datatype short --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**mincresample**(1)
