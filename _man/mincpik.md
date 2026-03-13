---
section: 1
title: mincpik
author: Andrew Janke
group: MINC Core Tools
---
# mincpik

generate image files from MINC volumes

`mincpik [options] <input.mnc> [output.png]`

## DESCRIPTION

**mincpik** is a Perl script that generates a picture (PNG or other image format)
from a MINC volume file. It can produce single-slice images in any of the three
orthogonal planes (sagittal, coronal, axial) or a triplanar montage showing all
three planes simultaneously.

The tool is commonly used for quality control, producing quick visual summaries
of MINC volumes for review. It automatically selects reasonable default slice
positions and intensity ranges, but these can be overridden with command-line
options.

If the output filename is omitted, the image is written to standard output or
a default filename based on the input.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--slice <n>`
:   Select the slice number to display in the chosen orientation.

`--scale <n>`
:   Scale factor for the output image size.

`--width <n>`
:   Set the output image width in pixels.

`--depth 8|16`
:   Set the bit depth of the output image (8 or 16 bits per channel).

`--sagittal`
:   Display a sagittal slice.

`--axial`
:   Display an axial slice.

`--coronal`
:   Display a coronal slice.

`--triplanar`
:   Generate a triplanar montage showing sagittal, coronal, and axial views.

`--horizontal`
:   Arrange triplanar views horizontally.

`--vertical`
:   Arrange triplanar views vertically.

`--anot_bar`
:   Include an annotation colour bar in the output image.

`--lookup`
:   Apply a colour lookup table to the image.

`--image_range <min> <max>`
:   Set the image intensity range for display mapping.

`--auto_range`
:   Automatically determine the intensity range from the volume data.

## EXAMPLES

Generate a default axial slice image:

    mincpik brain.mnc brain.png

Generate a triplanar montage:

    mincpik --triplanar brain.mnc brain_triplanar.png

Generate a sagittal view at slice 80 with a specific intensity range:

    mincpik --sagittal --slice 80 --image_range 0 100 brain.mnc sagittal.png

Generate a triplanar image with a colour bar, scaled to 4x:

    mincpik --triplanar --anot_bar --scale 4 brain.mnc qc_image.png

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[mincinfo](mincinfo) [minclookup](minclookup)
