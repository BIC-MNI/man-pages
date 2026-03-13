---
section: 1
title: map_sheets
author: David MacDonald
group: Surface and Geometry Tools
---
# map_sheets

map surface sheets between spherical and flat representations

`map_sheets sphere.obj sphere_flat.obj input.obj output_flat.obj output_fixed dist`

## DESCRIPTION

**map_sheets** maps surface sheets between spherical and flat
representations. Given a spherical surface (*sphere.obj*), its flat
representation (*sphere_flat.obj*), and an input surface (*input.obj*), the
program computes corresponding flat and corrected output surfaces.

The *output_flat.obj* is the flattened version of the input surface, and
*output_fixed* is a corrected version. The *dist* parameter controls the
mapping distance used in the correspondence computation.

This tool is used in cortical surface analysis for transforming between
3D cortical surfaces and 2D flat map representations while preserving
topological relationships.

## SEE ALSO

[map_surface_to_sheet](map_surface_to_sheet),
[flatten_sheet](flatten_sheet), [flatten_to_sphere](flatten_to_sphere)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
