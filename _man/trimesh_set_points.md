---
section: 1
title: trimesh_set_points
author: David MacDonald
group: Surface and Geometry Tools
---
# trimesh_set_points

set vertex positions in a triangular mesh from another mesh or object

`trimesh_set_points dest.msh|obj src.mesh|obj output.obj`

## DESCRIPTION

**trimesh_set_points** replaces the vertex positions in the destination mesh
with the vertex positions from the source mesh or object file. The topology
(connectivity) of the destination mesh is preserved, but all vertex coordinates
are taken from the source. The result is written to the output .obj file.

This is useful for transferring vertex positions between meshes that share the
same topology but have different vertex locations.

## SEE ALSO

[trimesh_resample](trimesh_resample),
[trimesh_to_polygons](trimesh_to_polygons)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
