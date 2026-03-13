---
section: 1
title: xfm2param
author: Louis Collins
group: Registration
---
# xfm2param

extract rotation, translation, scale, and shear parameters from a MNI transform file

`xfm2param file.xfm [file.mnc] [options]`

## DESCRIPTION

`xfm2param` reads a MNI `.xfm` transform file and decomposes it into
human-readable transformation parameters: center of rotation, translations,
rotations (in degrees), scales, and shears.

For concatenated transforms, each sub-transform is decomposed individually.
For non-linear transforms (grid transforms, thin-plate spline transforms),
the type is reported but only linear transforms are fully decomposed.

An optional MINC volume can be provided as the second argument. When given,
the center of gravity (COG) of the volume is computed and used as the center
of rotation and scaling for the decomposition.

This is the inverse operation of [param2xfm](param2xfm), which creates a
transform file from parameters.

## OPTIONS

`-center` x y z
:   Specify the center of rotation and scaling for the decomposition.
    Default: 0 0 0.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXAMPLES

Decompose a linear transform:

    xfm2param transform.xfm

Decompose a transform using a volume's center of gravity as the rotation center:

    xfm2param transform.xfm brain.mnc

## OUTPUT FORMAT

The output is a set of parameter lines printed to standard output:

    center:      cx cy cz
    translation: tx ty tz
    rotation:    rx ry rz
    scale:       sx sy sz
    shear:       shx shy shz

Rotations are given in degrees.

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[param2xfm](param2xfm) [xfmconcat](xfmconcat) [xfminvert](xfminvert)
[minctracc](minctracc)
