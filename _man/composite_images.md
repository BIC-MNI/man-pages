---
section: 1
title: composite_images
author: David MacDonald
group: Image Composition and Visualization
---
# composite_images

composite multiple RGB images into a single output

`composite_images output.rgb [-add] input1.rgb -xy [input2.rgb] ...`

## DESCRIPTION

`composite_images` composites multiple RGB image files into a single
output RGB image. Input images are specified along with layout directives
(`-xy` and similar flags) that control their spatial arrangement. The
optional `-add` flag causes pixel values to be summed rather than
composited.

## OPTIONS

`-add`
:   Add pixel values from input images rather than compositing them.

`-xy`
:   Layout directive specifying the arrangement of the following input
    image in the output.

## EXAMPLES

Composite two images side by side:

    composite_images output.rgb input1.rgb -xy input2.rgb

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[concat_images](concat_images) [composite_minc_images](composite_minc_images) [place_images](place_images)
