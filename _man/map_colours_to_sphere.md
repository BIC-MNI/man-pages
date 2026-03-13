---
section: 1
title: map_colours_to_sphere
author: David MacDonald
group: Surface and Geometry Tools
---
# map_colours_to_sphere

map colours from a volume onto a spherical surface object

`map_colours_to_sphere src.obj src.mnc dest.obj`

## DESCRIPTION

**map_colours_to_sphere** maps colour values from a MINC volume onto a
spherical surface object. The source surface *src.obj* defines the geometry,
and the volume *src.mnc* provides the colour or intensity data. The
resulting coloured sphere is written to *dest.obj*.

For each vertex on the destination sphere, the program samples the volume
at the corresponding position derived from the source surface and assigns
the resulting colour. This is useful for visualizing volumetric data on a
standardized spherical representation of the cortical surface.

## EXAMPLES

    map_colours_to_sphere cortex.obj t1.mnc sphere_coloured.obj

## SEE ALSO

[make_sphere_transform](make_sphere_transform),
[apply_sphere_transform](apply_sphere_transform),
[map_surface_to_sheet](map_surface_to_sheet)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
