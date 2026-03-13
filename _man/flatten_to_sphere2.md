---
section: 1
title: flatten_to_sphere2
author: David MacDonald
group: Surface and Geometry Tools
---
# flatten_to_sphere2

map a surface onto a sphere with curvature and stretch weights

`flatten_to_sphere2 input.obj output.obj [cw] [sw] [n_iters]`

## DESCRIPTION

`flatten_to_sphere2` maps a closed 3D surface onto a sphere using an
iterative relaxation method with additional control parameters. The
curvature weight (`cw`) and stretch weight (`sw`) allow fine-tuning of the
spherical mapping to balance area and angle distortion. An optional number
of iterations may be specified.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input surface object file.

`output.obj`
:   The output spherical surface object file.

`cw`
:   Optional curvature weight parameter.

`sw`
:   Optional stretch weight parameter.

`n_iters`
:   Optional number of iterations.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flatten_to_sphere](flatten_to_sphere) [flatten_polygons](flatten_polygons) [flatten_sheet](flatten_sheet)
