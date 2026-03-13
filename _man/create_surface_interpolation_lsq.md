---
section: 1
title: create_surface_interpolation_lsq
author: David MacDonald
group: Surface and Geometry Tools
---
# create_surface_interpolation_lsq

create a least-squares surface interpolation from scattered data

`create_surface_interpolation_lsq surface.obj xyz+values.txt output.txt [smoothness]`

## DESCRIPTION

`create_surface_interpolation_lsq` performs a least-squares interpolation
of scattered data onto a surface mesh. The input data file contains xyz
coordinates and associated values. The surface object provides the mesh
onto which the data is interpolated. An optional smoothness parameter
controls the regularization of the interpolation. The interpolated values
are written to the output text file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`surface.obj`
:   The input surface object file providing the interpolation mesh.

`xyz+values.txt`
:   A text file containing scattered data points with xyz coordinates and
    values.

`output.txt`
:   The output text file containing interpolated values at each surface
    vertex.

`smoothness`
:   An optional smoothness parameter controlling the regularization of
    the least-squares fit. Higher values produce smoother results.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[spline_smooth](spline_smooth) [spherical_resample](spherical_resample)
