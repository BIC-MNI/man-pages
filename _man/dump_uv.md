---
section: 1
title: dump_uv
author: David MacDonald
group: Statistical and Analysis Tools
---
# dump_uv

dump UV texture coordinates of a surface object

`dump_uv input.obj output.txt`

## DESCRIPTION

`dump_uv` reads the UV (texture) coordinates from a surface object file and
writes them to a text file. Each line in the output corresponds to a vertex
and contains its U and V coordinate values.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input surface object file containing UV texture coordinates.

`output.txt`
:   The output text file containing the UV coordinates.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[dump_points_to_tag_file](dump_points_to_tag_file) [evaluate](evaluate)
