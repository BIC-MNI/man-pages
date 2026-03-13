---
section: 1
title: print_2d_coords
author: David MacDonald
group: Statistical and Analysis Tools
---
# print_2d_coords

print 2D coordinates corresponding to a 3D point on a surface

`print_2d_coords input.obj x y z`

## DESCRIPTION

**print_2d_coords** prints the 2D parametric coordinates corresponding to
a given 3D world coordinate point on a surface object. The program finds
the closest point on the surface to the specified (*x*, *y*, *z*) position
and outputs the corresponding 2D parameterization coordinates.

This is useful for mapping between 3D surface space and 2D flat map
representations.

## EXAMPLES

    print_2d_coords cortex.obj 10.5 -20.3 45.0

## SEE ALSO

[map_surface_to_sheet](map_surface_to_sheet),
[find_vertex](find_vertex)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
