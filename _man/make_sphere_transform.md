---
section: 1
title: make_sphere_transform
author: David MacDonald
group: Surface and Geometry Tools
---
# make_sphere_transform

create a spherical transform mapping for a surface

`make_sphere_transform surface.obj pairs.tag output.txt [alternate]`

## DESCRIPTION

**make_sphere_transform** creates a spherical coordinate transformation
mapping for a surface object. Given a surface and a set of corresponding
tag point pairs, the program computes a mapping between the surface and a
spherical representation.

The *surface.obj* is the input polygonal surface. The *pairs.tag* file
contains landmark correspondences used to define the mapping. The result
is written to *output.txt*.

An optional *alternate* argument can be specified to select an alternative
mapping method.

This tool is used in cortical surface analysis for establishing
correspondence between surfaces via spherical parameterization.

## SEE ALSO

[apply_sphere_transform](apply_sphere_transform),
[flatten_to_sphere](flatten_to_sphere),
[map_colours_to_sphere](map_colours_to_sphere)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
