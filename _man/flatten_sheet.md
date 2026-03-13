---
section: 1
title: flatten_sheet
author: David MacDonald
group: Surface and Geometry Tools
---
# flatten_sheet

flatten a surface sheet to a 2D plane

`flatten_sheet input.obj output.obj [n_iters] [initfile] [fixedfile]`

## DESCRIPTION

`flatten_sheet` flattens a surface sheet to a 2D representation using an
iterative relaxation method. An optional initial configuration file and a
file specifying fixed vertices may be provided to constrain the flattening.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input surface object file.

`output.obj`
:   The output flattened surface object file.

`n_iters`
:   Optional number of iterations.

`initfile`
:   Optional initial 2D configuration file for the flattening.

`fixedfile`
:   Optional file specifying vertices to hold fixed during flattening.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flatten_sheet3](flatten_sheet3) [flatten_polygons](flatten_polygons) [flatten_to_sphere](flatten_to_sphere)
