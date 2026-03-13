---
section: 1
title: make_gradient_volume
author: David MacDonald
group: Volume Operations
---
# make_gradient_volume

compute gradient magnitude or second derivative of a MINC volume

`make_gradient_volume input.mnc output.mnc [1|2] [1|3]`

## DESCRIPTION

**make_gradient_volume** computes the magnitude of the gradient or the second
derivative of a MINC volume. Two optional numeric arguments control the
computation:

The first optional argument selects the derivative order: **1** computes the
gradient magnitude (first derivative), and **2** computes the second
derivative magnitude. The default is 1.

The second optional argument selects the interpolation method: **1** uses
linear interpolation and **3** uses cubic interpolation. The default is 1.

The output volume contains the computed magnitude at each voxel, which is
useful for edge detection, boundary delineation, and feature extraction in
medical images.

## EXAMPLES

Compute gradient magnitude with linear interpolation:

    make_gradient_volume brain.mnc gradient.mnc

Compute second derivative with cubic interpolation:

    make_gradient_volume brain.mnc second_deriv.mnc 2 3

## SEE ALSO

[make_geodesic_volume](make_geodesic_volume), [mincblur](mincblur)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
