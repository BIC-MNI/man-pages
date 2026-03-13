---
section: 1
title: create_2d_surface
author: David MacDonald
group: Surface and Geometry Tools
---
# create_2d_surface

create a 2D surface representation of a 3D surface object

`create_2d_surface input.obj output.obj`

## DESCRIPTION

`create_2d_surface` reads a 3D surface object and creates a 2D surface
representation. This projects the surface into two dimensions while
preserving topological relationships between vertices.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input 3D surface object file.

`output.obj`
:   The output 2D surface object file.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[create_2d_sheet](create_2d_sheet) [flatten_to_sphere](flatten_to_sphere)
