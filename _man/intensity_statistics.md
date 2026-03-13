---
section: 1
title: intensity_statistics
author: David MacDonald
group: Statistical and Analysis Tools
---
# intensity_statistics

compute intensity statistics within labelled regions of a volume

`intensity_statistics volume.mnc input.tag|input.mnc|none [dump_file|none] [median]`

## DESCRIPTION

`intensity_statistics` computes statistics (mean, standard deviation, min,
max, and optionally the median) for the voxel intensities in a MINC volume.
If an input tag file or label volume is specified, only voxels within the
defined region of interest are considered. If `none` is given as the input,
all voxels are included. If a dump file is specified, all individual
intensity values are written to that file. If `median` is specified as the
last argument, the median is also computed and reported.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume.mnc`
:   The input MINC volume.

`input.tag|input.mnc|none`
:   A tag file or label volume defining the region of interest, or `none`
    for the whole volume.

`dump_file|none`
:   An output file for dumping all intensity values, or `none` to skip.

`median`
:   Optional keyword to also compute the median.

## EXAMPLES

Compute statistics for the entire volume:

    intensity_statistics volume.mnc none

Compute statistics within a labelled region including the median:

    intensity_statistics volume.mnc labels.mnc none median

Dump all intensity values from a tag-defined region:

    intensity_statistics volume.mnc region.tag intensities.txt

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincstats](mincstats) [histogram_volume](histogram_volume) [get_tic](get_tic)
