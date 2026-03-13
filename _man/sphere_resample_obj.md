---
section: 1
title: sphere_resample_obj
author: David MacDonald
group: Registration Scripts
---
# sphere_resample_obj

resample a surface object onto a standard sphere tessellation

`sphere_resample_obj [options] input.obj output.obj`

## DESCRIPTION

**sphere_resample_obj** is a Perl script that resamples a surface object onto
a standard sphere tessellation. It uses spherical parameterization to map the
input surface to a sphere and then resamples it at regularly distributed
vertices. This is useful for normalizing surface meshes to a common topology
for group comparisons or statistical analysis.

This script requires the Perl module **Getopt::Tabular**.

## SEE ALSO

[spherical_resample](spherical_resample), [two_surface_resample](two_surface_resample)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
