---
section: 1
title: flatten_sheet3
author: David MacDonald
group: Surface and Geometry Tools
---
# flatten_sheet3

flatten a surface sheet to a 2D plane using topological or physical method

`flatten_sheet3 input.obj output.obj t|p [n_iters] [initfile] [fixedfile]`

## DESCRIPTION

`flatten_sheet3` flattens a surface sheet to a 2D representation. The
method is selected by specifying `t` for topological flattening or `p` for
physical flattening. An optional initial configuration file and a file
specifying fixed vertices may be provided to constrain the flattening.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input surface object file.

`output.obj`
:   The output flattened surface object file.

`t|p`
:   The flattening method: `t` for topological or `p` for physical.

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

[flatten_sheet](flatten_sheet) [flatten_polygons](flatten_polygons) [flatten_to_sphere](flatten_to_sphere)
