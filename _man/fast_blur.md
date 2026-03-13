---
section: 1
title: fast_blur
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# fast_blur

Fast Gaussian blurring of a MINC volume.

`fast_blur [options] <input> <output>`

## DESCRIPTION

**fast_blur** performs fast Gaussian blurring on a MINC volume. The blurring
kernel is specified by its full width at half maximum (FWHM) in millimeters.
Different FWHM values can be set independently for each spatial axis. In
addition to simple blurring, the tool can compute first-order spatial
derivatives, the gradient vector field, or the gradient magnitude.

## OPTIONS

`--clobber`
:   Overwrite existing output files.

`--verbose`
:   Print progress information during processing.

`--fwhm` *f*
:   Set the global Gaussian FWHM in millimeters, applied equally to all axes.

`--fwhm_x` *fx*
:   Set the Gaussian FWHM in millimeters for the X axis.

`--fwhm_y` *fy*
:   Set the Gaussian FWHM in millimeters for the Y axis.

`--fwhm_z` *fz*
:   Set the Gaussian FWHM in millimeters for the Z axis.

`--dx`
:   Compute the first derivative (differentiate) along the X axis.

`--dy`
:   Compute the first derivative (differentiate) along the Y axis.

`--dz`
:   Compute the first derivative (differentiate) along the Z axis.

`--grad`
:   Calculate the gradient vector field. The output will be a vector volume
    with components for each spatial direction.

`--gmag`
:   Calculate the gradient magnitude (scalar).

`--float`
:   Write output in floating-point format.

## EXAMPLES

Blur a volume with 4 mm FWHM:

    fast_blur --fwhm 4 input.mnc blurred.mnc

Compute gradient magnitude with 2 mm FWHM smoothing:

    fast_blur --fwhm 2 --gmag input.mnc gradient_mag.mnc

Blur with different widths per axis:

    fast_blur --fwhm_x 2 --fwhm_y 4 --fwhm_z 6 input.mnc blurred.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mincblur](mincblur)
