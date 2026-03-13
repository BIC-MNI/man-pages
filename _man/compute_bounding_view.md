---
section: 1
title: compute_bounding_view
author: David MacDonald
group: Image Composition and Visualization
---
# compute_bounding_view

compute the world limits of an object in an orthogonal view

`compute_bounding_view input.obj xview yview zview xup yup zup`

## DESCRIPTION

`compute_bounding_view` computes the world coordinate limits of an object
file when projected into the orthogonal view defined by the given view
direction and up vectors. The view direction is specified by (xview,
yview, zview) and the up direction by (xup, yup, zup). The bounding
limits are printed to standard output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.obj`
:   The input object file.

`xview yview zview`
:   The view direction vector components.

`xup yup zup`
:   The up direction vector components.

## EXAMPLES

Compute the bounding view looking along the z-axis with y-up:

    compute_bounding_view brain.obj 0 0 1 0 1 0

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[ray_trace](ray_trace) [Display](Display)
