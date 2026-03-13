---
section: 1
title: print_axis_angles
author: David MacDonald
group: Statistical and Analysis Tools
---
# print_axis_angles

print angles between native and Talairach axes

`print_axis_angles input.mnc to_tal.xfm`

## DESCRIPTION

**print_axis_angles** displays the angles in degrees between the native
space axes and the Talairach axes in Talairach space. The program reads
a MINC volume and a linear transformation to Talairach space and computes
the angular deviation of each native axis from the corresponding Talairach
axis.

This is useful for assessing how tilted or rotated a scan is relative to
the standard Talairach coordinate system, which can indicate positioning
issues during acquisition.

## EXAMPLES

    print_axis_angles brain.mnc to_talairach.xfm

## SEE ALSO

[mritotal](mritotal), [xfm2param](xfm2param)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
