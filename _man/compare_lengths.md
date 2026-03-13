---
section: 1
title: compare_lengths
author: David MacDonald
group: Surface and Geometry Tools
---
# compare_lengths

compare edge lengths between two polygon meshes

`compare_lengths src_polygons dest_polygons`

## DESCRIPTION

`compare_lengths` reads two polygon mesh object files and compares the
edge lengths between corresponding edges. Statistics about length
differences are printed to standard output. This is useful for evaluating
the distortion introduced by surface deformation or remeshing operations.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`src_polygons`
:   The source polygon mesh object file.

`dest_polygons`
:   The destination polygon mesh object file.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compare_left_right](compare_left_right) [find_surface_distances](find_surface_distances)
