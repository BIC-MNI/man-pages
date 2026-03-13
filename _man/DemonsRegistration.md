---
section: 1
title: DemonsRegistration
author: Vladimir S. Fonov
group: Deformable Registration
---
# DemonsRegistration

Diffeomorphic demons registration between two volumes.

`DemonsRegistration -f <fixed> -m <moving> [options]`

## DESCRIPTION

**DemonsRegistration** performs diffeomorphic demons-based non-linear
registration between a fixed and a moving image. The algorithm iteratively
estimates a dense deformation field that warps the moving image to match the
fixed image, using the demons force with Gaussian smoothing of the
deformation and update fields.

Multiple update rules are supported: diffeomorphic (default), additive, and
compositive. Gradient computation can be symmetrized, computed from the fixed
image, the warped moving image, or the mapped moving image. Multi-resolution
registration is controlled by specifying iteration counts per level.

Optional masks can restrict the registration to regions of interest, and an
initial deformation field or affine transform can be provided as a starting
point.

## OPTIONS

`-f`, `--fixed-image` *image*
:   Fixed (target) image. Required.

`-m`, `--moving-image` *image*
:   Moving (source) image. Required.

`--fixed-mask` *image*
:   Mask for the fixed image (restrict registration to masked region).

`--moving-mask` *image*
:   Mask for the moving image.

`-b`, `--input-field` *field*
:   Initial deformation field to start from.

`-p`, `--input-transform` *xfm*
:   Initial affine transform to apply before deformable registration.

`-o`, `--output-image` *image*
:   Output the warped moving image.

`-O`, `--outputDef-field` *field*
:   Output the final deformation field.

`-J`, `--output-jacobian` *image*
:   Output the Jacobian determinant map of the deformation.

`-r`, `--true-field` *field*
:   True deformation field for validation (computes error metrics).

`-i`, `--num-iterations` *UINTxUINTxUINT*
:   Number of iterations per resolution level, specified as a product string
    (default: 15x10x5).

`-s`, `--def-field-sigma` *float*
:   Gaussian smoothing sigma for the deformation field (default: 1.5).

`-g`, `--up-field-sigma` *float*
:   Gaussian smoothing sigma for the update field (default: 0.0).

`-l`, `--max-step-length` *float*
:   Maximum step length for the demons force (default: 2.0).

`-a`, `--update-rule` *int*
:   Update rule: 0 = diffeomorphic (default), 1 = additive, 2 = compositive.

`-t`, `--gradient-type` *int*
:   Gradient computation type: 0 = symmetrized (default), 1 = fixed image,
    2 = warped moving image, 3 = mapped moving image.

`-e`, `--use-histogram-matching`
:   Use histogram matching to normalize intensities before registration.

`-d`, `--verbose` *level*
:   Set debug/verbosity level.

## EXAMPLES

    # Basic registration
    DemonsRegistration -f fixed.mnc -m moving.mnc \
        -o warped.mnc -O deformation.mnc

    # Multi-resolution with histogram matching
    DemonsRegistration -f fixed.mnc -m moving.mnc \
        -o warped.mnc -O deformation.mnc \
        -i 30x20x10 -e

    # Using an initial affine transform with masks
    DemonsRegistration -f fixed.mnc -m moving.mnc \
        --fixed-mask mask.mnc -p initial.xfm \
        -o warped.mnc -O deformation.mnc -s 2.0

## AUTHOR

Tom Vercauteren - INRIA & Mauna Kea Technologies, with additions by Vladimir S. Fonov.

## COPYRIGHTS

Copyright &copy; 2008 by Tom Vercauteren, INRIA & Mauna Kea Technologies

## SEE ALSO

[LogDomainDemonsRegistration](LogDomainDemonsRegistration) ,
[minctracc](minctracc) ,
[itk_resample](itk_resample)
