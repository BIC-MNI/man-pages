---
section: 1
title: LogDomainDemonsRegistration
author: Vladimir S. Fonov
group: Deformable Registration
---
# LogDomainDemonsRegistration

Log-domain diffeomorphic demons registration between two volumes.

`LogDomainDemonsRegistration -f <fixed> -m <moving> [options]`

## DESCRIPTION

**LogDomainDemonsRegistration** performs log-domain diffeomorphic demons
registration between a fixed and a moving image. Unlike standard demons
registration, this variant parameterizes the deformation in the log domain
as a stationary velocity field, which is exponentiated via scaling and
squaring to produce the final diffeomorphism. This guarantees invertible
transformations and enables symmetric registration.

The Baker-Campbell-Hausdorff (BCH) formula is used to compose velocity field
updates. The number of BCH terms controls the accuracy of the composition
approximation. Both standard log-domain and symmetric log-domain update
rules are supported.

Optional masks, initial fields, and affine transforms are supported. The
tool can output the deformation field, its inverse, the velocity field,
and the Jacobian determinant map.

## OPTIONS

`-f`, `--fixed-image` *image*
:   Fixed (target) image. Required.

`-m`, `--moving-image` *image*
:   Moving (source) image. Required.

`--fixed-mask` *image*
:   Mask for the fixed image.

`--moving-mask` *image*
:   Mask for the moving image.

`-b`, `--input-field` *field*
:   Initial velocity field to start from.

`-p`, `--input-transform` *xfm*
:   Initial affine transform to apply before deformable registration.

`-o`, `--output-image` *image*
:   Output the warped moving image.

`-O`, `--outputDef-field` *field*
:   Output the final deformation field.

`-I`, `--outputInvDef-field` *field*
:   Output the inverse deformation field.

`-V`, `--outputVel-field` *field*
:   Output the stationary velocity field.

`-J`, `--output-jacobian` *image*
:   Output the Jacobian determinant map.

`-r`, `--true-field` *field*
:   True deformation field for validation.

`-i`, `--num-iterations` *UINTxUINTxUINT*
:   Number of iterations per resolution level (default: 15x10x5).

`-s`, `--vel-field-sigma` *float*
:   Gaussian smoothing sigma for the velocity field (default: 1.5).

`-g`, `--up-field-sigma` *float*
:   Gaussian smoothing sigma for the update field (default: 0.0).

`-l`, `--max-step-length` *float*
:   Maximum step length for the demons force (default: 2.0).

`-a`, `--update-rule` *int*
:   Update rule: 0 = log-domain, 1 = symmetric log-domain (default: 1).

`-t`, `--gradient-type` *int*
:   Gradient computation type: 0 = symmetrized (default), 1 = fixed image,
    2 = warped moving image, 3 = mapped moving image.

`-c`, `--num-bch-terms` *int*
:   Number of BCH terms for velocity field composition: 2, 3, or 4 (default: 2).

`-e`, `--use-histogram-matching`
:   Use histogram matching to normalize intensities before registration.

`-d`, `--verbose` *level*
:   Set debug/verbosity level.

## EXAMPLES

    # Symmetric log-domain registration
    LogDomainDemonsRegistration -f fixed.mnc -m moving.mnc \
        -o warped.mnc -O deformation.mnc -V velocity.mnc

    # With histogram matching and custom iterations
    LogDomainDemonsRegistration -f fixed.mnc -m moving.mnc \
        -o warped.mnc -O deformation.mnc -i 30x20x10 -e

    # Output inverse deformation and Jacobian
    LogDomainDemonsRegistration -f fixed.mnc -m moving.mnc \
        -O forward.mnc -I inverse.mnc -J jacobian.mnc \
        -c 3 -s 2.0

## AUTHOR

Florence Dru, Tom Vercauteren, Vladimir S. Fonov - INRIA & Mauna Kea Technologies, McConnell Brain Imaging Centre.

## COPYRIGHTS

Copyright &copy; 2008 by Florence Dru, Tom Vercauteren, INRIA & Mauna Kea Technologies

## SEE ALSO

[DemonsRegistration](DemonsRegistration) ,
[grid_2_log](grid_2_log) ,
[grid_proc](grid_proc)
