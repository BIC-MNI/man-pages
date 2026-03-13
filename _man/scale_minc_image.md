---
section: 1
title: scale_minc_image
author: David MacDonald
group: Volume Operations
---
# scale_minc_image

scale voxel intensities in a MINC volume by a constant factor

`scale_minc_image input.mnc scale output.mnc`

## DESCRIPTION

**scale_minc_image** multiplies every voxel intensity in the input MINC volume
by the given constant scale factor and writes the result to the output file.
This is useful for normalizing image intensities or adjusting contrast by a
known multiplicative factor.

## SEE ALSO

[mincmath](mincmath), [minccalc](minccalc)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
