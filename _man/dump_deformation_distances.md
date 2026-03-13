---
section: 1
title: dump_deformation_distances
author: David MacDonald
group: Statistical and Analysis Tools
---
# dump_deformation_distances

dump deformation distances from a non-linear transformation

`dump_deformation_distances src.obj xform.xfm output.txt`

## DESCRIPTION

`dump_deformation_distances` applies a transform to a surface object and
computes the per-vertex displacement distances. For each vertex of the
source surface, the Euclidean distance between the original position and the
transformed position is calculated and written to the output text file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`src.obj`
:   The source surface object file.

`xform.xfm`
:   The XFM transform file to apply.

`output.txt`
:   The output text file containing per-vertex deformation distances.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[transform_objects](transform_objects) [dump_rms](dump_rms)
