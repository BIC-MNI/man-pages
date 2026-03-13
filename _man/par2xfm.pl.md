---
section: 1
title: par2xfm.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# par2xfm.pl

convert distortion parameters to an XFM grid transform

`par2xfm.pl <par_in> <xfm_out> [options]`

## DESCRIPTION

**par2xfm.pl** converts a spherical-harmonic distortion parameter file into an
XFM transformation file containing a nonlinear grid transform. The parameter
file typically comes from a phantom distortion fitting procedure (e.g.
**phantomfit.pl**). The script evaluates the parametric distortion model on a
regular grid and writes the result as a MINC `.xfm` file that can be applied
with standard tools such as **mincresample**.

Options control the grid spacing, the maximum distortion magnitude, the spatial
extent of the grid, and whether the transform should be inverted. A cylindric
coordinate mode is available for use with cylindrical phantoms.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--spacing <f>`
:   Grid spacing in millimetres for the output deformation field. Default: 2.

`--max <f>`
:   Maximum allowed distortion magnitude in millimetres. Values exceeding this
    are clipped. Default: 5.0.

`--noinvert`
:   Do not invert the transformation. By default the transform is inverted so
    that it can be used to correct the distortion.

`--extent <f>`
:   Spatial extent (half-width) of the output grid in millimetres. Default: 300.

`--step <f>`
:   Evaluation step size used when sampling the parametric model onto the grid.

`--scaling <f>`
:   Apply a global scaling factor to the distortion field.

`--cylindric`
:   Use cylindrical coordinate representation for the distortion model. This is
    appropriate when the distortion was fit using a cylindrical phantom.

## EXAMPLES

Convert a parameter file to an XFM with default settings:

    par2xfm.pl distortion.par correction.xfm

Create a grid transform with finer spacing and larger extent:

    par2xfm.pl distortion.par correction.xfm --spacing 1 --extent 400

Convert without inverting and using cylindrical coordinates:

    par2xfm.pl distortion.par correction.xfm --noinvert --cylindric --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**param2grid**(1), **c_param2grid**(1), **phantomfit.pl**(1)
