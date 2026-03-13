---
section: 1
title: mincbbox
author: Louis Collins
group: Registration
---
# mincbbox

calculate the bounding box of non-zero data in a MINC volume

`mincbbox [<options>] <inputfile>`

## DESCRIPTION

`mincbbox` calculates the bounding box of the data in a MINC volume and
returns the coordinates of the box in terms of start position and width in
millimetres along each spatial axis.

The program iterates over all voxels in the input volume and finds the
minimum and maximum world coordinates of voxels whose value exceeds a
configurable threshold (default 0). The output can be formatted for direct
use with other MINC tools such as [mincresample](mincresample) or
[mincreshape](mincreshape).

## OPTIONS

`-threshold` value
:   Set the real-value threshold for determining the bounding box. Voxels
    with values greater than this threshold are considered to be inside the
    bounding box. Default: 0.

`-one_line`
:   Output on one line (default): `start_x start_y start_z width_x width_y width_z`.

`-two_lines`
:   Output on two lines: start coordinates on the first line, widths on the
    second.

`-mincresample`
:   Output in a format suitable for passing directly to
    [mincresample](mincresample): `-step x y z -start x y z -nelements x y z`.

`-mincreshape`
:   Output in a format suitable for passing directly to
    [mincreshape](mincreshape): `-start x,y,z -count dx,dy,dz`.

`-minccrop`
:   Output in a format suitable for autocropping:
    `-xlim x1 x2 -ylim y1 y2 -zlim z1 z2`.

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

Print the bounding box of a volume:

    mincbbox input.mnc

Print the bounding box using a threshold of 10:

    mincbbox -threshold 10 input.mnc

Resample a volume to its bounding box:

    mincresample input.mnc output.mnc $(mincbbox -mincresample input.mnc)

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1994 by Louis Collins

## SEE ALSO

[mincresample](mincresample) [mincreshape](mincreshape) [autocrop](autocrop)
