---
section: 1
title: trimesh_resample
author: David MacDonald
group: Surface and Geometry Tools
---
# trimesh_resample

subdivide and coalesce a triangular mesh

`trimesh_resample input.obj|input.msh input.obj output.msh output.obj output.mid subdivide_values min_value max_value min_size max_size coalesce_values min_value max_value min_size max_size`

## DESCRIPTION

**trimesh_resample** adaptively resamples a triangular mesh by subdividing and
coalescing triangles based on associated vertex values and size constraints.

Triangles are subdivided where the vertex values fall within the specified
subdivide range (**min_value** to **max_value**) and the triangle size is
between **min_size** and **max_size**. Similarly, triangles are coalesced where
vertex values fall within the coalesce range and size constraints.

The tool reads a mesh from the input file (in .obj or .msh format) along with
a reference .obj file, and produces an output .msh file, .obj file, and .mid
file containing the resampled mesh data.

## SEE ALSO

[trimesh_to_polygons](trimesh_to_polygons),
[trimesh_set_points](trimesh_set_points),
[marching_cubes](marching_cubes)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
