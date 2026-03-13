---
section: 1
title: minc_to_rgb
author: David MacDonald
group: Image Composition and Visualization
---
# minc_to_rgb

convert a MINC volume to an RGB image

`minc_to_rgb input.mnc output.rgb`

## DESCRIPTION

**minc_to_rgb** converts a MINC volume to an RGB image file. The program
reads the volume data and maps voxel intensity values to RGB colour values,
producing an output image suitable for viewing with image display tools.

This is a simple conversion utility for creating 2D RGB image
representations from MINC volumetric data.

## EXAMPLES

    minc_to_rgb brain.mnc brain.rgb

## SEE ALSO

[rgb_to_minc](rgb_to_minc), [labels_to_rgb](labels_to_rgb),
[make_slice](make_slice)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
