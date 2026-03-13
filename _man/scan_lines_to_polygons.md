---
section: 1
title: scan_lines_to_polygons
author: David MacDonald
group: Surface and Geometry Tools
---
# scan_lines_to_polygons

scan line objects and map them to polygon surfaces producing MINC output volumes

`scan_lines_to_polygons polygons.obj dist scan_step [input1.obj output1.mnc] [input2.obj output2.mnc] ...`

## DESCRIPTION

**scan_lines_to_polygons** takes a polygon surface and one or more line objects,
scanning the lines onto the surface at the specified distance and scan step
parameters. For each pair of input line object and output MINC file, the tool
maps the line geometry to the polygon surface and produces a corresponding
MINC output volume.

The **dist** parameter controls the maximum distance from the surface used
for scanning, and **scan_step** controls the sampling step size along the
scan direction.

## SEE ALSO

[scan_object_to_volume](scan_object_to_volume), [marching_cubes](marching_cubes)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
