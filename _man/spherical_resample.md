---
section: 1
title: spherical_resample
author: David MacDonald
group: Surface and Geometry Tools
---
# spherical_resample

resample a surface using spherical parameterization

`spherical_resample surface.obj sphere.obj output.obj n`

## DESCRIPTION

**spherical_resample** resamples a surface object using spherical
parameterization. The input surface is mapped to the provided sphere
parameterization, and a new surface is generated with **n** vertices
distributed according to the spherical mapping. The resampled surface is
written to the output file.

This tool is useful for creating surfaces with a standardized number of
vertices for inter-subject comparison or statistical analysis.

## SEE ALSO

[sphere_resample_obj](sphere_resample_obj),
[two_surface_resample](two_surface_resample),
[apply_sphere_transform](apply_sphere_transform)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
