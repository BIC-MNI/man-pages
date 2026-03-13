---
section: 1
title: make_face.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# make_face.pl

extract a face surface from an MRI volume

`make_face.pl <input.mnc> <output_image> [options]`

## DESCRIPTION

**make_face.pl** creates a rendered face image from an MRI volume. The tool
extracts an isosurface from the input volume using marching cubes, then renders
it using **ray_trace** to produce a 2D image. This is useful for visual QC of
defacing results or for generating face images for subject identification
verification.

The tool supports control over the smoothing kernel, isosurface threshold,
rotation angle, and can optionally accept a pre-computed stereotaxic
transformation.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--fwhm <f>`
:   Full-width at half-maximum (in mm) of the smoothing kernel applied to the
    volume before isosurface extraction. Default: 2.

`--rotate <f>`
:   Rotation angle (in degrees) applied to the rendered view.

`--threshold <f>`
:   Isosurface threshold value for the marching cubes extraction. Default: 1.0.

`--stx <xfm>`
:   Supply a pre-computed stereotaxic transformation to orient the volume
    before rendering.

## EXAMPLES

Generate a face image from a T1 volume:

    make_face.pl subject_t1.mnc face.png

Generate a face image with custom threshold and smoothing:

    make_face.pl --fwhm 3 --threshold 0.8 subject_t1.mnc face.png

Render using a stereotaxic transformation with rotation:

    make_face.pl --stx subject_to_tal.xfm --rotate 15 \
        --clobber subject_t1.mnc face.png

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**pipeline_qc_face.pl**(1), **ray_trace**(1), **marching_cubes**(1)
