---
section: 1
title: check_scale
author: Louis Collins
group: Registration
---
# check_scale

check and correct the Z-scale of a MNI linear transform

`check_scale <input.xfm> <result.xfm> [<file.mnc>]`

## DESCRIPTION

`check_scale` reads a linear MNI `.xfm` transform file, extracts its
parameters (translation, rotation, scale, shear), and checks whether the
Z-scale is disproportionately large relative to the X and Y scales. If
the Z-scale exceeds 1.15 times the average of the X and Y scales, it is
clamped to that average value.

The corrected transformation matrix is then rebuilt from the adjusted
parameters and written to a new `.xfm` file.

An optional MINC volume can be provided as a third argument; when given,
the center of gravity of the volume is used as the center of rotation and
scaling for the decomposition.

This is a quality-control tool for linear registration results where the
Z-scale factor may become unreliable, for example due to limited sampling
along the Z dimension.

## OPTIONS

This tool uses positional arguments only. There are no named options.

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Louis Collins

## SEE ALSO

[xfm2param](xfm2param) [param2xfm](param2xfm) [minctracc](minctracc)
