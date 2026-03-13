---
section: 1
title: map_surface_to_sheet
author: David MacDonald
group: Surface and Geometry Tools
---
# map_surface_to_sheet

map a 3D surface to a flat 2D sheet image

`map_surface_to_sheet surface.obj output.mnc nx ny [volume.mnc [degree]]`

## DESCRIPTION

**map_surface_to_sheet** maps a 3D surface to a flat 2D sheet image. The
output is a MINC volume of dimensions *nx* by *ny* representing the
unfolded surface.

If no volume is specified, the surface curvature is used to assign colour
values to the sheet. If *volume.mnc* is specified, the program samples the
volume at each surface vertex position and maps the interpolated values onto
the sheet. The optional *degree* parameter controls the interpolation
degree: **-1** for nearest-neighbour, **0** for linear, or **2** for
quadratic interpolation.

This tool is useful for creating flat map representations of cortical
surfaces for visualization and analysis.

## EXAMPLES

Map surface curvature to a flat sheet:

    map_surface_to_sheet cortex.obj sheet.mnc 512 256

Map volume values onto the sheet with linear interpolation:

    map_surface_to_sheet cortex.obj sheet.mnc 512 256 t1.mnc 0

## SEE ALSO

[map_sheets](map_sheets), [flatten_sheet](flatten_sheet),
[map_colours_to_sphere](map_colours_to_sphere)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
