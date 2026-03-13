---
section: 1
title: find_surface_distances
author: David MacDonald
group: Surface and Geometry Tools
---
# find_surface_distances

compute distances from a surface to threshold boundaries in a volume

`find_surface_distances volume.mnc surface.obj thresh max_in max_out out.txt`

## DESCRIPTION

`find_surface_distances` computes the distance from each vertex of a
surface to the nearest threshold boundary in a volume. For each vertex,
the search is conducted both inward and outward from the surface, limited
by `max_in` and `max_out` respectively. The threshold value determines
the boundary location. Per-vertex distances are written to the output
text file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume.mnc`
:   The input MINC volume.

`surface.obj`
:   The input surface object file.

`thresh`
:   The intensity threshold defining the boundary.

`max_in`
:   Maximum search distance inward from the surface.

`max_out`
:   Maximum search distance outward from the surface.

`out.txt`
:   The output text file containing per-vertex distances.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[dump_rms](dump_rms) [dump_deformation_distances](dump_deformation_distances) [evaluate](evaluate)
