---
section: 1
title: gaussian_blur_peaks
author: David MacDonald
group: Statistical and Analysis Tools
---
# gaussian_blur_peaks

create a volume from Gaussian-blurred peak locations

`gaussian_blur_peaks like_volume.mnc output.mnc [-max_value value] x1 y1 z1 fwhm1 [x2 y2 z2 fwhm2] [-tag filename fwhm]...`

## DESCRIPTION

`gaussian_blur_peaks` creates a volume sampled according to the geometry
of `like_volume.mnc` which contains a Gaussian blurring of the given 3D
points. Each point is specified by a world coordinate (x, y, z) and a
filter size defined by the full width at half maximum (FWHM) in
millimetres. Output values range from 0 to 1 unless overridden by the
`-max_value` option. Points may also be read from a tag file using the
`-tag` option.

## OPTIONS

`-max_value value`
:   Set the maximum output value. Defaults to 1.

`-tag filename fwhm`
:   Read peak locations from a tag file and blur each with the given FWHM.

Positional point arguments:

`x y z fwhm`
:   World coordinates and FWHM of a peak. Multiple peaks may be specified.

## EXAMPLES

Create a volume with one blurred peak at (10, 20, 30) with 6mm FWHM:

    gaussian_blur_peaks template.mnc output.mnc 10 20 30 6

Create with peaks from a tag file:

    gaussian_blur_peaks template.mnc output.mnc -tag peaks.tag 8

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[find_peaks](find_peaks) [mincblur](mincblur)
