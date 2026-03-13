---
section: 1
title: composite_minc_images
author: David MacDonald
group: Image Composition and Visualization
---
# composite_minc_images

composite two MINC images

`composite_minc_images input1.mnc input2.mnc [add|composite] output.mnc`

## DESCRIPTION

`composite_minc_images` combines two MINC image volumes into a single
output volume. The combination method can be specified as `add` (sum the
voxel values) or `composite` (overlay one image on another).

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input1.mnc`
:   The first input MINC image.

`input2.mnc`
:   The second input MINC image.

`add|composite`
:   The compositing method. Use `add` to sum voxel values or `composite`
    to overlay images. Optional.

`output.mnc`
:   The output MINC image.

## EXAMPLES

Add two MINC images:

    composite_minc_images input1.mnc input2.mnc add output.mnc

Composite two MINC images:

    composite_minc_images input1.mnc input2.mnc composite output.mnc

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[composite_images](composite_images) [composite_volumes](composite_volumes)
