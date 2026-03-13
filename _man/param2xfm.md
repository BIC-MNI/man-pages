---
section: 1
title: param2xfm
author: Louis Collins
group: Registration
---
# param2xfm

create a MNI transform file from rotation, translation, scale, and shear parameters

`param2xfm [options] <result.xfm>`

## DESCRIPTION

`param2xfm` creates a MNI `.xfm` linear transform file from user-specified
transformation parameters. The user can specify translations, rotations (in
degrees), scaling factors, shears, and the center of rotation/scaling.

The resulting transform is constructed by composing the individual
transformations (translation, rotation about center, scaling about center,
and shearing) into a single 4x4 affine transformation matrix, which is
written out in MNI `.xfm` format.

This is the inverse operation of [xfm2param](xfm2param), which extracts
parameters from an existing transform file.

## OPTIONS

`-center` x y z
:   Set the center of rotation and scaling. Default: 0 0 0.

`-translation` x y z
:   Set the translation in millimetres along the X, Y, and Z axes. Default: 0 0 0.

`-rotations` rx ry rz
:   Set the rotation angles in degrees about the X, Y, and Z axes. Default: 0 0 0.

`-scales` sx sy sz
:   Set the scaling factors along the X, Y, and Z axes. Default: 1 1 1.

`-shears` shx shy shz
:   Set the shear parameters along the X, Y, and Z axes. Default: 0 0 0.

`-clobber`
:   Overwrite the output file if it already exists.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXAMPLES

Create an identity transform:

    param2xfm identity.xfm

Create a transform with a 5mm translation along X:

    param2xfm -translation 5 0 0 shift.xfm

Create a transform with 10-degree rotation about the Z axis:

    param2xfm -rotations 0 0 10 rotate.xfm

Create a transform that scales by 1.1 in all dimensions around a specified center:

    param2xfm -scales 1.1 1.1 1.1 -center 0 0 0 scale.xfm

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Louis Collins

## SEE ALSO

[xfm2param](xfm2param) [xfmconcat](xfmconcat) [xfminvert](xfminvert)
[minctracc](minctracc)
