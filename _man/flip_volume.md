---
section: 1
title: flip_volume
author: David MacDonald
group: Volume Operations
---
# flip_volume

interchange voxel values with their left-right opposites in a MINC volume

`flip_volume input.mnc output.mnc`

## DESCRIPTION

`flip_volume` interchanges voxel values with their left-right opposites,
effectively mirroring the volume about its left-right axis. The resulting
flipped volume is written to the output file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.mnc`
:   The input MINC volume.

`output.mnc`
:   The output flipped MINC volume.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flip_tags](flip_tags) [mincresample](mincresample)
