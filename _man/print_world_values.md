---
section: 1
title: print_world_values
author: David MacDonald
group: Statistical and Analysis Tools
---
# print_world_values

evaluate volume values at multiple world coordinates from a file

`print_world_values <glimfile> <coordlist file> <outputfile>`

## DESCRIPTION

**print_world_values** reads world coordinates from a coordinate list file
and evaluates the volumes listed in a glim (general linear model) file at
those positions. The results are written to the output file.

The *glimfile* contains a list of MINC volume filenames. The *coordlist
file* contains a list of world coordinates (one set of x, y, z per line).
For each coordinate, the program evaluates every volume in the glimfile and
writes the values to the output file.

This is useful for extracting values at specific anatomical locations across
multiple volumes, such as in statistical analyses.

## EXAMPLES

    print_world_values volumes.glim coordinates.txt output.txt

## SEE ALSO

[print_volume_value](print_volume_value),
[print_world_value](print_world_value),
[volume_object_evaluate](volume_object_evaluate)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
