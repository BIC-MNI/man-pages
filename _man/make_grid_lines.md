---
section: 1
title: make_grid_lines
author: David MacDonald
group: Surface and Geometry Tools
---
# make_grid_lines

create grid lines on a surface object

`make_grid_lines src.obj dest.obj nlong nlat`

## DESCRIPTION

**make_grid_lines** creates a set of grid lines on a surface object with a
specified number of longitude and latitude lines. The source surface
*src.obj* provides the geometry, and the output *dest.obj* contains the
generated grid lines as a lines object.

The *nlong* parameter specifies the number of longitudinal lines and *nlat*
specifies the number of latitudinal lines to generate on the surface. This
is useful for visualizing the parameterization of a surface or for creating
reference grids on spherical or quasi-spherical surfaces.

## EXAMPLES

    make_grid_lines sphere.obj grid.obj 36 18

## SEE ALSO

[create_2d_sheet](create_2d_sheet), [flatten_to_sphere](flatten_to_sphere)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
