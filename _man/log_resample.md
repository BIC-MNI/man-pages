---
section: 1
title: log_resample
author: Vladimir S. Fonov
group: Deformable Registration
---
# log_resample

Resample image using log-domain vector field transforms.

`log_resample <input> <output.mnc> [options]`

## DESCRIPTION

**log_resample** resamples a MINC volume using a log-domain velocity field
transform. The velocity field is exponentiated via scaling and squaring to
produce the final deformation, and the input image is resampled accordingly.
This tool is useful for applying diffeomorphic transformations stored in
log-domain form, as produced by log-domain demons registration or the
`grid_2_log` utility.

Interpolation order can be controlled, and the transform can optionally be
inverted. For label images, nearest-neighbour interpolation should be used
(see `--labels`).

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--like` *file*
:   Resample the output on the same grid as the specified MINC file.

`--transform` *field*
:   Specify the log-domain velocity field to use as the transform.

`--order` *n*
:   Set the spline interpolation order. Use 0 for nearest-neighbour, 1 for
    linear, or higher values for cubic and above.

`--invert_transform`
:   Invert the transform before applying it.

`--labels`
:   Use nearest-neighbour interpolation, appropriate for resampling label volumes.

`--byte`
:   Store output voxels as unsigned byte.

`--short`
:   Store output voxels as short integer.

`--float`
:   Store output voxels as single-precision floating point.

`--double`
:   Store output voxels as double-precision floating point.

## EXAMPLES

    # Resample an image using a log-domain velocity field
    log_resample input.mnc output.mnc --transform velocity_field.mnc

    # Resample with inversion and a reference grid
    log_resample input.mnc output.mnc --transform velocity_field.mnc \
        --like template.mnc --invert_transform

    # Resample a label volume
    log_resample labels.mnc resampled_labels.mnc --transform velocity_field.mnc \
        --labels --short

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_resample](itk_resample) ,
[grid_proc](grid_proc) ,
[grid_2_log](grid_2_log)
