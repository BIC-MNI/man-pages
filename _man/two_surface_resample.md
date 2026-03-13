---
section: 1
title: two_surface_resample
author: David MacDonald
group: Surface and Geometry Tools
---
# two_surface_resample

resample a surface using two model surfaces

`two_surface_resample surface.obj surface_model.obj different_model.obj output.obj n`

## DESCRIPTION

**two_surface_resample** resamples a surface using a pair of model surfaces to
establish vertex correspondence. The input **surface.obj** is mapped through
**surface_model.obj** and **different_model.obj** to produce a resampled output
surface with **n** vertices.

This tool is useful when two surfaces share a common parameterization through
different model surfaces, allowing data to be transferred between surface
representations with different tessellations.

## SEE ALSO

[spherical_resample](spherical_resample),
[sphere_resample_obj](sphere_resample_obj),
[apply_sphere_transform](apply_sphere_transform)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
