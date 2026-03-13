---
section: 1
title: create_2d_sheet
author: David MacDonald
group: Surface and Geometry Tools
---
# create_2d_sheet

create a 2D sheet representation of a surface object

`create_2d_sheet input.obj output.obj`

## DESCRIPTION

`create_2d_sheet` reads a 3D surface object and creates a 2D sheet
representation. This flattens the surface into a planar sheet, which can
be used for surface-based analysis or texture mapping.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input 3D surface object file.

`output.obj`
:   The output 2D sheet object file.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[create_2d_surface](create_2d_surface) [flatten_sheet](flatten_sheet) [map_surface_to_sheet](map_surface_to_sheet)
