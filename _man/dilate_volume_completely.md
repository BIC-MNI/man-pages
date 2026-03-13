---
section: 1
title: dilate_volume_completely
author: David MacDonald
group: Volume Operations
---
# dilate_volume_completely

fully dilate regions of a specified value until no further dilation is possible

`dilate_volume_completely input.mnc output.mnc [max_dilations|-1] [6|26] [min_outside max_outside] [min_inside max_inside]`

## DESCRIPTION

`dilate_volume_completely` dilates all regions in a MINC volume
iteratively until there are no voxels remaining in the range specified by
`min_outside` and `max_outside` (defaults to 0 0). The dilation continues
until the maximum number of iterations is reached or no further dilation
is possible. Setting `max_dilations` to -1 means unlimited iterations. An
optional inside range may be specified to control which voxels are treated
as the seed region.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`max_dilations`
:   Maximum number of dilation iterations to perform. Use -1 for
    unlimited. Defaults to -1.

`6|26`
:   Connectivity type. Use 6 for face-connected neighbours or 26 for
    all neighbours. Defaults to 26.

`min_outside`
:   Minimum value of the outside range to be filled. Defaults to 0.

`max_outside`
:   Maximum value of the outside range to be filled. Defaults to 0.

`min_inside`
:   Minimum value of the inside (seed) range.

`max_inside`
:   Maximum value of the inside (seed) range.

## EXAMPLES

Dilate until no zero-valued voxels remain:

    dilate_volume_completely input.mnc output.mnc

Dilate with at most 100 iterations using 6-connectivity:

    dilate_volume_completely input.mnc output.mnc 100 6

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[dilate_volume](dilate_volume) [chamfer_volume](chamfer_volume) [mincmorph](mincmorph)
