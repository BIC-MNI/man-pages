---
section: 1
title: evaluate
author: David MacDonald
group: Volume Operations
---
# evaluate

evaluate a volume at the vertices of a surface object

`evaluate volume.mnc input.obj output.txt`

## DESCRIPTION

`evaluate` samples a MINC volume at each vertex position of a surface
object and writes the interpolated values to a text file. Each line of the
output contains the volume value at the corresponding vertex of the input
surface.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume.mnc`
:   The input MINC volume to sample.

`input.obj`
:   The surface object file whose vertex positions are used as sample points.

`output.txt`
:   The output text file containing per-vertex volume values.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[volume_object_evaluate](volume_object_evaluate) [print_world_values](print_world_values)
