---
section: 1
title: make_geodesic_volume
author: David MacDonald
group: Volume Operations
---
# make_geodesic_volume

create a geodesic distance volume from a seed point in a MINC volume

`make_geodesic_volume input.mnc output.mnc threshold x y z [x_size] [y_size] [z_size]`

## DESCRIPTION

**make_geodesic_volume** computes a geodesic distance volume with respect to
a seed point at world coordinates (*x*, *y*, *z*). The geodesic distance is
computed through voxels in the input volume that exceed the specified
*threshold*, measuring the shortest path distance along connected voxels
from the seed point to every other above-threshold voxel.

Optional *x_size*, *y_size*, and *z_size* parameters control the output
volume dimensions. If not specified, the dimensions match the input volume.

The output volume contains the geodesic distance at each voxel, which is
useful for measuring distances along structures such as cortical surfaces
or white matter tracts.

## EXAMPLES

    make_geodesic_volume brain.mnc geodesic.mnc 0.5 0 0 0

    make_geodesic_volume brain.mnc geodesic.mnc 0.5 10 -20 5 64 64 64

## SEE ALSO

[chamfer_volume](chamfer_volume), [make_gradient_volume](make_gradient_volume)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
