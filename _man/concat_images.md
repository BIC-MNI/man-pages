---
section: 1
title: concat_images
author: David MacDonald
group: Image Composition and Visualization
---
# concat_images

concatenate two RGB images into one

`concat_images input1.rgb input2.rgb output.rgb`

## DESCRIPTION

`concat_images` reads two RGB image files and concatenates them into a
single output RGB image. The images are joined side by side.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input1.rgb`
:   The first input RGB image file.

`input2.rgb`
:   The second input RGB image file.

`output.rgb`
:   The output concatenated RGB image file.

## EXAMPLES

Concatenate two images:

    concat_images left.rgb right.rgb combined.rgb

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[composite_images](composite_images) [place_images](place_images)
