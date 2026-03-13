---
section: 1
title: itk_resample
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_resample

resample a MINC volume using ITK with spline interpolation and .xfm transforms

`itk_resample <input> <output.mnc> [options]`

## DESCRIPTION

**itk_resample** resamples a medical image volume onto a new sampling grid. It
supports MINC .xfm and ITK transformation files to map voxel coordinates between
the input and output volumes. The interpolation is performed using B-spline
interpolation with a configurable spline order (default order 2).

A target sampling grid can be specified with `--like` to match the geometry
(dimensions, voxel sizes, start coordinates, and direction cosines) of an
existing file, or with `--uniformize` to create an isotropic grid at a given
step size.

Label volumes can be resampled with nearest-neighbour interpolation using the
`--labels` flag, and optional look-up table remapping with `--lut_string`.
Anti-aliasing prefiltering is available via the `--aa` flag for downsampling
operations.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--like` *file*
:   Resample the input to match the sampling grid of *file* (dimensions, voxel spacing, starts, and direction cosines).

`--transform` *xfm*
:   Apply the specified MINC .xfm transformation file during resampling.

`--itk_transform` *file*
:   Apply the specified ITK-format transformation file during resampling.

`--order` *n*
:   Set the B-spline interpolation order (0 to 5). Order 0 is nearest-neighbour, order 1 is trilinear, and orders 2-5 are higher-order B-splines. Default is 2.

`--uniformize` *step*
:   Resample the volume onto an isotropic grid with the given step size (in mm).

`--invert_transform`
:   Invert the transformation before applying it.

`--labels`
:   Treat the input as a label volume. Uses nearest-neighbour interpolation (order 0).

`--byte`
:   Store output voxels as unsigned 8-bit bytes.

`--short`
:   Store output voxels as signed 16-bit short integers.

`--ushort`
:   Store output voxels as unsigned 16-bit short integers.

`--int`
:   Store output voxels as signed 32-bit integers.

`--uint`
:   Store output voxels as unsigned 32-bit integers.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

`--lut_string` *str*
:   Apply a label look-up table remapping specified as a semicolon-separated string of old:new pairs (e.g., "1:2;3:4").

`--aa`
:   Enable anti-aliasing prefiltering. Useful when downsampling to prevent aliasing artefacts.

`--background` *val*
:   Set the background (fill) value for voxels that fall outside the input volume. Default is 0.

## EXAMPLES

Resample a volume to match the geometry of another file:

    itk_resample input.mnc output.mnc --like template.mnc

Resample using a transformation with trilinear interpolation:

    itk_resample input.mnc output.mnc --like template.mnc --transform input_to_template.xfm --order 1

Resample a label volume with an inverted transform:

    itk_resample labels.mnc resampled_labels.mnc --like target.mnc --transform t1_to_target.xfm --invert_transform --labels

Create an isotropic 1 mm volume:

    itk_resample input.mnc output_1mm.mnc --uniformize 1.0

Resample with anti-aliasing for downsampling:

    itk_resample hires.mnc lores.mnc --like lores_template.mnc --aa --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_convert](itk_convert), [mincresample](mincresample), [itk_convert_xfm](itk_convert_xfm), [resample_grid](resample_grid)
