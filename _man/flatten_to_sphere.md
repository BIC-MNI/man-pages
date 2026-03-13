---
section: 1
title: flatten_to_sphere
author: David MacDonald
group: Surface and Geometry Tools
---
# flatten_to_sphere

map a surface onto a sphere

`flatten_to_sphere input.obj output.obj [n_iters]`

## DESCRIPTION

`flatten_to_sphere` maps a closed 3D surface onto a sphere using an
iterative relaxation method. The resulting spherical parameterization
preserves the topology of the original surface. An optional number of
iterations may be specified.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input surface object file.

`output.obj`
:   The output spherical surface object file.

`n_iters`
:   Optional number of iterations.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flatten_to_sphere2](flatten_to_sphere2) [flatten_polygons](flatten_polygons) [flatten_sheet](flatten_sheet)
