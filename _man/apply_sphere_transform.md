---
section: 1
title: apply_sphere_transform
author: David MacDonald
group: Surface and Geometry Tools
---
# apply_sphere_transform

apply a spherical transform to a surface object

`apply_sphere_transform surface.obj u.txt v.txt output.obj [alternate]`

## DESCRIPTION

**apply_sphere_transform** applies a spherical coordinate transform to a
surface object. The transform is specified by two text files containing the
**u** and **v** coordinate maps, which define the remapping of spherical
coordinates for each vertex on the surface.

The transformed surface is written to **output.obj**.

If the optional **alternate** argument is specified, an alternate method of
applying the transform is used.

## SEE ALSO

[spherical_resample](spherical_resample),
[make_sphere_transform](make_sphere_transform),
[flatten_to_sphere](flatten_to_sphere)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
