---
section: 1
title: find_image_bounding_box
author: David MacDonald
group: Volume Operations
---
# find_image_bounding_box

find the bounding box of an RGB image excluding the background colour

`find_image_bounding_box input.rgb bg_colour`

## DESCRIPTION

`find_image_bounding_box` scans an RGB image and determines the bounding
box of the non-background content. The background colour is specified as
an argument, and all pixels matching that colour are excluded. The
resulting bounding box coordinates are printed to standard output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.rgb`
:   The input RGB image file.

`bg_colour`
:   The background colour to exclude when computing the bounding box.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[composite_images](composite_images) [place_images](place_images)
