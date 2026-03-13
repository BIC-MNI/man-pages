---
section: 1
title: dump_transform
author: David MacDonald
group: Statistical and Analysis Tools
---
# dump_transform

dump the voxel-to-world transform of a MINC volume to an .xfm file

`dump_transform input1.mnc output.xfm`

## DESCRIPTION

`dump_transform` reads the voxel-to-world transformation matrix stored in
a MINC volume header and writes it to an XFM transform file. This is
useful for extracting the spatial mapping information embedded in a MINC
file for use with other tools that operate on transforms.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input1.mnc`
:   The input MINC volume from which to extract the transform.

`output.xfm`
:   The output XFM transform file.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[xfm2param](xfm2param) [param2xfm](param2xfm) [mincinfo](mincinfo)
