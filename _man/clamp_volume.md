---
section: 1
title: clamp_volume
author: David MacDonald
group: Volume Operations
---
# clamp_volume

clamp voxel values in a MINC volume to a specified range

`clamp_volume input.mnc output.mnc min max`

## DESCRIPTION

`clamp_volume` reads a MINC volume and produces a new volume where all
voxel values are clamped to lie within the specified range. Values below
`min` are set to `min`, and values above `max` are set to `max`.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`min`
:   The minimum value of the output range. Input values below this are set
    to this value.

`max`
:   The maximum value of the output range. Input values above this are set
    to this value.

## EXAMPLES

Clamp volume values to the range 0 to 100:

    clamp_volume input.mnc output.mnc 0 100

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[threshold_volume](threshold_volume) [mincmath](mincmath)
