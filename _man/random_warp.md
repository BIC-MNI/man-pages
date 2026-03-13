---
section: 1
title: random_warp
author: David MacDonald
group: Volume Operations
---
# random_warp

create a random warp (deformation) transform from a surface object

`random_warp src.obj dest.xfm [domain_factor] [warp_distance] [seed]`

## DESCRIPTION

**random_warp** creates a random non-linear warp (deformation) transform
from a surface object. The output *dest.xfm* is an XFM transformation file
containing a random deformation field.

The optional *domain_factor* controls the spatial extent of the deformation.
The optional *warp_distance* controls the magnitude of the displacements.
The optional *seed* sets the random number generator seed for reproducible
results.

This tool is useful for generating synthetic deformations for testing
registration algorithms, creating simulated data, or performing
perturbation analyses.

## EXAMPLES

    random_warp brain.obj random.xfm

    random_warp brain.obj random.xfm 1.0 5.0 42

## SEE ALSO

[minctracc](minctracc), [transform_volume](transform_volume)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
