---
section: 1
title: plane_polygon_intersect
author: David MacDonald
group: Surface and Geometry Tools
---
# plane_polygon_intersect

compute the intersection of a plane with a polygonal surface

`plane_polygon_intersect src_polygons dest_lines x|y|z|[nx ny nz x y z] [position]`

## DESCRIPTION

**plane_polygon_intersect** computes the intersection of a plane with a
polygonal surface, producing line output. The input *src_polygons* is a
BIC .obj polygon file and the output *dest_lines* is a BIC .obj lines file.

The cutting plane can be specified either as one of the principal axes
(**x**, **y**, or **z**) with an optional *position* along that axis, or
as an arbitrary plane defined by a normal vector (*nx*, *ny*, *nz*) and a
point (*x*, *y*, *z*) on the plane.

This is useful for extracting contour lines from surfaces at specific
cross-sections.

## EXAMPLES

Cut with a coronal plane at y=0:

    plane_polygon_intersect brain.obj contour.obj y 0

Cut with an arbitrary plane:

    plane_polygon_intersect brain.obj contour.obj 0 0 1 0 0 50

## SEE ALSO

[contour_slice](contour_slice), [marching_cubes](marching_cubes)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
