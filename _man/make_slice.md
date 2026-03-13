---
section: 1
title: make_slice
author: David MacDonald
group: Image Composition and Visualization
---
# make_slice

extract a 2D slice from a MINC volume as an image

`make_slice volume_file output_file x|y|z v|w pos [xt] [yt]`

`make_slice - output_file x|y|z pos [min1 max1 min2 max2]`

## DESCRIPTION

**make_slice** creates a 2D slice image from a MINC volume. The slice is
extracted along one of the three principal axes: **x**, **y**, or **z** at
the specified position *pos*.

In the first form, *volume_file* is a MINC volume and the slice coordinate
system is specified as **v** (voxel coordinates) or **w** (world
coordinates). Optional *xt* and *yt* parameters specify translation offsets
for the output image.

In the second form, the volume is read from standard input (specified by
**-**), and optional *min1*, *max1*, *min2*, *max2* parameters define the
bounding region of the slice in the two in-plane dimensions.

The output is written as an RGB image file.

## EXAMPLES

Extract a sagittal slice at world position 0:

    make_slice brain.mnc sagittal.rgb x w 0

Extract an axial slice at voxel position 90:

    make_slice brain.mnc axial.rgb z v 90

## SEE ALSO

[contour_slice](contour_slice), [composite_images](composite_images),
[place_images](place_images)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
