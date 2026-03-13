---
section: 1
title: blur_surface
author: David MacDonald
group: Surface and Geometry Tools
---
# blur_surface

blur a surface object using a Gaussian kernel

`blur_surface input.obj output.obj fwhm dist_ratio [values]`

## DESCRIPTION

**blur_surface** smooths a surface object by applying a Gaussian blur kernel
with the specified full width at half maximum (**fwhm**). The **dist_ratio**
parameter controls the ratio of the search distance to the FWHM, determining
how far neighbouring vertices contribute to the smoothing.

If **values** are provided, the per-vertex values are blurred rather than the
vertex positions themselves.

The blurred surface (or values) is written to the output file.

## SEE ALSO

[mincblur](mincblur), [fast_blur](fast_blur),
[spherical_resample](spherical_resample)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
