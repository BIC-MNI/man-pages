---
section: 1
title: transform_objects
author: David MacDonald
group: Surface and Geometry Tools
---
# transform_objects

apply a spatial transformation to surface or line objects

`transform_objects input.obj input.xfm [output.obj]`

## DESCRIPTION

**transform_objects** applies a spatial transformation (specified as an MNI
transform file) to a BIC object file containing surfaces, lines, or other
geometric objects. All vertex coordinates in the object are transformed
according to the given transform.

If **output.obj** is specified, the transformed object is written to that file.
Otherwise, the input file is overwritten with the transformed result.

## EXAMPLES

    transform_objects brain_surface.obj linear.xfm transformed.obj

    transform_objects brain_surface.obj nonlinear.xfm

## SEE ALSO

[transform_tags](transform_tags), [transform_volume](transform_volume),
[xfmconcat](xfmconcat)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
