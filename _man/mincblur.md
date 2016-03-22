---
section: 1
title: mincblur
author: Louis Collins
---
# mincblur

mincblur - convolve an input volume with a Gaussian blurring kernel.
`mincblur <options> <source> <output_basename>`

## DESCRIPTION

*Mincblur* convolves an input volume with a Gaussian blurring kernel of 
user-defined width. Convolution is accomplished by multiplication in the Fourier 
domain where the blurring kernel is calculated explicitly over the whole field. 
Mincblur can also calculate the first partial derivatives and the gradient 
magnitude volume.

The first command line argument is the name of the 3D input MINC file. The 
second argument is the basename for the output file. The string "_blur.mnc" is 
added automatically to the basename to generate the blurred intensity volume; if 
a gradient volume is calculated (using the -gradient option), then "_dxyz.mnc" 
is added to the basename; and if partial derivative volumes are calculated 
(using the -partial option), then "_dx.mnc", "_dy.mnc", and "_dz.mnc" are added 
to name them. The output volume(s) will have the same size and be of the same 
type as the input volume.

Before blurring, the edges of the data volume are apodized (intensity reduced) 
to minimize edge effects. This process can be skipped with the '-no_apodize' 
flag.

## Specification of blurring kernel.

One of the following options must be used to specify the size of the blurring 
kernel: `-fwhm`, `-standarddev`, `-3Dfwhm`, where

`-fwhm <val>`: Specifies the full-width-half-maximum of the iso-tropic 3D 
Gaussian blurring kernel.

`-standarddev <val>`: Specifies the sigma iso-tropic 3D Gaussian blurring 
kernel.

`-3Dfwhm <valx> <valy> <valz>`: Specifies the full-width-half-maximum in the x, 
y and z directions of the non-isotropic 3D Gaussian blurring kernel.

## Other options

`-dimensions <1|2|3>`: Number of dimensions to blur. -dim 1 blurs only in the z 
direction, useful for simulating thick slices. -dim 2 blurs only in the xy 
plane. -dim 3 blur all 3 dimensions and is the default.

`-gaussian`: Use a gaussian smoothing kernel (default).

`-rect`: Use a rect (box) smoothing kernel.

`-no_apodize`: Do not apodize the data before blurring.

`-no_clobber`: Do not overwrite output file (default).

`-clobber`: Overwrite output file.

`-gradient`: Create the gradient magnitude (_dxyz.mnc) volume as well.

`-partial`: Create the partial derivative (_dx.mnc, _dy.mnc & _dz.mnc) volumes 
as well.

In order to create any gradient data, it is necessary to temporarily store the 
blurred data in floating point representation. By default, the temporary files 
are written in the current directory. If that directory is not available, /tmp 
is used. Both of these possiblities can be overridden by providing an 
environment variable TMPDIR in the user's environment, whose value is the name 
of the desired temporary-file directory. Of course, the temporary files are 
removed by mincblur after processing.

## Options for logging progress.

`-verbose <val>`: Write verbose messages indicating progress (default = 1).

`-quiet`: Do not write log messages

`-debug`: Print out debug info.

## Generic options

`-help`: Print summary of command-line options and abort.

## EXAMPLES

1) Blur an input volume with a 6mm fwhm isotropic Gaussian blurring kernel:

`mincblur -fwhm 6 input.mnc out_6`

mincblur will create out_6_blur.mnc.

2) Calculate the blurred and gradient magnitude data:

`mincblur -fwhm 6 -gradient input.mnc out_6`

mincblur will create out_6_blur.mnc and out_6_dxyz.mnc

3) Calculate the blurred data, the partial derivative volumes and the gradient 
magnitude for the same data:

`mincblur -fwhm 6 -partial input.mnc out_6`

mincblur will create out_6_blur.mnc, out_6_dx.mnc, out_6_dy.mnc, out_6_dz.mnc 
and out_6_dxyz.mnc

## KNOWN BUGS

- The temporary files may not be removed properly if mincblur fails during 
    processing.
- FWHM value smaller then voxel size will lead to incorrect behaviour.

## AUTHOR

Louis Collins

## COPYRIGHT

Copyright (c) 1993-95 by Louis Collins
