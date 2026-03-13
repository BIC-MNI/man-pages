---
section: 1
title: rgb_to_minc
author: David MacDonald
group: Image Composition and Visualization
---
# rgb_to_minc

convert RGB images to a MINC volume

`rgb_to_minc output.mnc 3|4|23|24 input1.rgb input2.rgb ...`

## DESCRIPTION

**rgb_to_minc** converts one or more RGB image files into a MINC volume.
The mode argument specifies the output dimensionality and organization:

- **3** — Create a 3D volume from the input images (stacked as slices).
- **4** — Create a 4D volume from the input images.
- **23** — Create a 2D+colour (3D with vector dimension) volume.
- **24** — Create a 2D+colour+time (4D with vector dimension) volume.

Multiple input RGB images can be specified and are assembled into the output
volume according to the selected mode.

## EXAMPLES

Stack RGB images into a 3D volume:

    rgb_to_minc output.mnc 3 slice01.rgb slice02.rgb slice03.rgb

Create a 2D colour volume from a single image:

    rgb_to_minc output.mnc 23 image.rgb

## SEE ALSO

[minc_to_rgb](minc_to_rgb), [make_slice](make_slice),
[place_images](place_images)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
