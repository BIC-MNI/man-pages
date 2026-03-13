---
section: 1
title: random_volume
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# random_volume

generate a random volume matching a sample volume geometry

`random_volume <like.mnc> <output.mnc> [options]`

## DESCRIPTION

**random_volume** generates a MINC volume filled with random noise, using the
geometry (dimensions, voxel sizes, orientation, and coordinate system) of a
reference "like" volume. This is useful for simulation studies, statistical
testing, and generating null distributions.

The output volume has the same spatial dimensions and sampling as the reference
volume, but voxel values are replaced with random numbers drawn from either a
Gaussian (normal) or uniform distribution.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--float`
:   Store output voxels as 32-bit floating point values.

`--double`
:   Store output voxels as 64-bit double precision floating point values.

`--gauss`
:   Fill the volume with Gaussian (normally distributed) random noise. This is
    the default noise type.

`--uniform`
:   Fill the volume with uniformly distributed random noise.

## EXAMPLES

Generate a Gaussian noise volume matching the geometry of a template:

    random_volume template.mnc noise.mnc

Generate a uniform noise volume with float precision:

    random_volume --uniform --float template.mnc uniform_noise.mnc

Generate a Gaussian noise volume, overwriting existing output:

    random_volume --clobber --gauss template.mnc noise.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[make_phantom](make_phantom)
