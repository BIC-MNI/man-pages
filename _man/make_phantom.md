---
section: 1
title: make_phantom
author: Louis Collins
group: Registration
---
# make_phantom

create a synthetic MINC volume containing a geometric phantom object

`make_phantom [<options>] output.mnc`

## DESCRIPTION

`make_phantom` creates a synthetic MINC volume containing a geometric
phantom, either a rectangle or an ellipsoid. The user specifies volume
parameters (number of elements, step sizes, start coordinates, data type)
and object parameters (center, width, fill value, edge value, background
value).

For rectangular phantoms, all voxels whose world coordinates fall within
the specified bounding box are set to the fill value. For ellipsoidal
phantoms, the standard ellipsoid equation is used to determine membership,
with optional partial-volume effects computed via sub-voxel sampling.

This tool is primarily used for generating synthetic test data for
registration and other image processing algorithms.

## OPTIONS

### Object definition options

`-rectangle`
:   Build a rectangular object (default).

`-ellipse`
:   Build an ellipsoidal object.

`-center` x y z
:   Center point of the object in world coordinates. Default: 128 128 128.

`-xcenter` value
:   Center of the object in the X dimension. Default: 128.

`-ycenter` value
:   Center of the object in the Y dimension. Default: 128.

`-zcenter` value
:   Center of the object in the Z dimension. Default: 128.

`-width` wx wy wz
:   Width of the object in world millimetres along X, Y, and Z. Default: 60 80 30.

`-xwidth` value
:   Width of the object in the X dimension. Default: 60.

`-ywidth` value
:   Width of the object in the Y dimension. Default: 80.

`-zwidth` value
:   Width of the object in the Z dimension. Default: 30.

`-fill_value` value
:   Real value used to fill the interior of the object. Default: 1.

`-edge_value` value
:   Real value used for edge voxels of the object. Default: 1.

`-background` value
:   Real value used for background voxels. Default: 0.

`-no_partial`
:   Do not account for partial volume effects at object boundaries.

### Volume definition options

`-nelements` nx ny nz
:   Number of elements (voxels) along each dimension. Default: 128 128 128.

`-xnelements` value
:   Number of elements along the X dimension. Default: 128.

`-ynelements` value
:   Number of elements along the Y dimension. Default: 128.

`-znelements` value
:   Number of elements along the Z dimension. Default: 128.

`-step` sx sy sz
:   Step size (voxel spacing in mm) along each dimension. Default: 2 2 2.

`-xstep` value
:   Step size along the X dimension. Default: 2.

`-ystep` value
:   Step size along the Y dimension. Default: 2.

`-zstep` value
:   Step size along the Z dimension. Default: 2.

`-start` ox oy oz
:   Start point (origin) along each dimension. Default: 0 0 0.

`-xstart` value
:   Start point along the X dimension. Default: 0.

`-ystart` value
:   Start point along the Y dimension. Default: 0.

`-zstart` value
:   Start point along the Z dimension. Default: 0.

### Data type options

`-byte`
:   Write out byte data (default).

`-short`
:   Write out short integer data.

`-long`
:   Write out long integer data.

`-float`
:   Write out single-precision floating-point data.

`-double`
:   Write out double-precision floating-point data.

`-signed`
:   Write signed integer data.

`-unsigned`
:   Write unsigned integer data (default).

`-labels`
:   Integer operation on labels.

`-discrete`
:   Synonym for `-labels`.

`-continuous`
:   Continuous operation, opposite of `-labels`.

`-voxel_range` min max
:   Valid voxel range for output data.

`-real_range` min max
:   Valid real range for output data.

### General options

`-clobber`
:   Overwrite the output file if it already exists.

`-no_clobber`
:   Do not overwrite the output file (default).

`-verbose`
:   Write messages indicating progress (default).

`-quiet`
:   Do not write log messages.

`-debug`
:   Print out debugging information.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXAMPLES

Create a default rectangular phantom:

    make_phantom phantom.mnc

Create an ellipsoidal phantom centered at (100, 100, 100):

    make_phantom -ellipse -center 100 100 100 phantom.mnc

Create a high-resolution phantom with 1mm voxels:

    make_phantom -step 1 1 1 -nelements 256 256 256 phantom.mnc

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1994 by Louis Collins

## SEE ALSO

[minctracc](minctracc) [mincresample](mincresample)
