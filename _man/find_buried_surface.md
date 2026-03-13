---
section: 1
title: find_buried_surface
author: David MacDonald
group: Surface and Geometry Tools
---
# find_buried_surface

find buried regions on a polygon surface based on curvature radius

`find_buried_surface src_polygons dest_polygons radius_of_curvature block_size`

## DESCRIPTION

`find_buried_surface` identifies buried (hidden) regions on a polygon
surface. A surface region is considered buried if it is occluded by
surrounding geometry based on the specified radius of curvature. The
`block_size` parameter controls the spatial resolution of the search. The
result is written to the destination polygon file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`src_polygons`
:   The input polygon surface object file.

`dest_polygons`
:   The output polygon surface object file with buried regions identified.

`radius_of_curvature`
:   The curvature radius used to determine what constitutes a buried region.

`block_size`
:   The block size controlling the spatial resolution of the search.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[close_surface](close_surface) [convex_hull](convex_hull)
