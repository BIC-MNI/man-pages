---
section: 1
title: trimesh_to_polygons
author: David MacDonald
group: Surface and Geometry Tools
---
# trimesh_to_polygons

convert a triangular mesh to a polygons file

`trimesh_to_polygons input.msh output.obj output.mid`

## DESCRIPTION

**trimesh_to_polygons** converts a triangular mesh file (.msh format) to a BIC
polygons object file (.obj format). An additional midpoint file (.mid) is also
produced. This conversion allows trimesh data to be used with tools that operate
on standard BIC polygon objects.

## SEE ALSO

[trimesh_resample](trimesh_resample),
[trimesh_set_points](trimesh_set_points),
[marching_cubes](marching_cubes)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
