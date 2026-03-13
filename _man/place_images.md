---
section: 1
title: place_images
author: David MacDonald
group: Image Composition and Visualization
---
# place_images

place multiple RGB images at specified positions in an output image

`place_images output.rgb bg_colour input1.rgb x1 y1 input2.rgb x2 y2 ...`

## DESCRIPTION

**place_images** composites multiple RGB images into a single output image
by placing each input image at the specified (x, y) position. The
*bg_colour* argument sets the background colour for areas not covered by
any input image.

Each input image is specified by its filename followed by the x and y
coordinates (in pixels) of where its lower-left corner should be placed
in the output. Any number of input images can be specified.

This tool is useful for creating composite visualizations, montages, or
tiled displays of multiple slice images or renderings.

## EXAMPLES

    place_images montage.rgb black slice1.rgb 0 0 slice2.rgb 256 0 slice3.rgb 512 0

## SEE ALSO

[composite_images](composite_images), [make_slice](make_slice),
[concat_images](concat_images)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
