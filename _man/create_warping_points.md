---
section: 1
title: create_warping_points
author: David MacDonald
group: Surface and Geometry Tools
---
# create_warping_points

create warping tag points from surface correspondences

`create_warping_points output.tag n_along surface1.obj surface2.obj A_file1 A_file2 ... B_file1 B_file2 B_file3`

## DESCRIPTION

`create_warping_points` generates a set of warping tag points based on the
correspondences between two surface objects. The parameter `n_along`
controls the number of sampling points along the surface. Additional
input files (A and B groups) provide supplementary data for computing the
warp correspondences. The output tag file can be used with non-linear
registration tools.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`output.tag`
:   The output tag point file.

`n_along`
:   The number of sampling points along the surface.

`surface1.obj`
:   The first surface object file.

`surface2.obj`
:   The second surface object file.

`A_file1 A_file2 ...`
:   Additional input files for the first group.

`B_file1 B_file2 ...`
:   Additional input files for the second group.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[transform_objects](transform_objects) [minctracc](minctracc)
