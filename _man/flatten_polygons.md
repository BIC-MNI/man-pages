---
section: 1
title: flatten_polygons
author: David MacDonald
group: Surface and Geometry Tools
---
# flatten_polygons

flatten a polygonal surface into 2D

`flatten_polygons input.obj output.obj [step] [n_iters]`

## DESCRIPTION

`flatten_polygons` flattens a 3D polygon surface to a 2D representation
using an iterative relaxation method. The optional `step` parameter
controls the step size of each iteration, and `n_iters` sets the number
of iterations.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input 3D polygon surface object file.

`output.obj`
:   The output flattened 2D surface object file.

`step`
:   Optional step size for each relaxation iteration.

`n_iters`
:   Optional number of iterations.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flatten_sheet](flatten_sheet) [flatten_to_sphere](flatten_to_sphere) [map_surface_to_sheet](map_surface_to_sheet)
