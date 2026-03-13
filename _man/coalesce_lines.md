---
section: 1
title: coalesce_lines
author: David MacDonald
group: Surface and Geometry Tools
---
# coalesce_lines

coalesce shared points in a lines object

`coalesce_lines input.obj output.obj`

## DESCRIPTION

`coalesce_lines` reads a lines object file and coalesces any shared
points, producing a cleaner line representation. Points that are
duplicated across multiple line segments are merged into single shared
vertices in the output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input lines object file.

`output.obj`
:   The output lines object file with shared points coalesced.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[extract_largest_line](extract_largest_line) [scan_lines_to_polygons](scan_lines_to_polygons)
