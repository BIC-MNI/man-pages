---
section: 1
title: dim_image
author: David MacDonald
group: Image Composition and Visualization
---
# dim_image

darken an RGB image by a given strength factor

`dim_image input.rgb output.rgb strength`

## DESCRIPTION

`dim_image` dims (darkens) an RGB image by the given strength factor.
The strength controls how much the pixel intensities are reduced, producing
a uniformly darkened version of the input image.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.rgb`
:   The input RGB image file.

`output.rgb`
:   The output dimmed RGB image file.

`strength`
:   The dimming strength factor controlling how much the image is darkened.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[composite_images](composite_images) [scale_minc_image](scale_minc_image)
