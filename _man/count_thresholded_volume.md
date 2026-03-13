---
section: 1
title: count_thresholded_volume
author: David MacDonald
group: Volume Operations
---
# count_thresholded_volume

count non-zero mask voxels corresponding to volume values within a threshold

`count_thresholded_volume mask_volume.mnc volume.mnc min_threshold max_threshold`

## DESCRIPTION

`count_thresholded_volume` counts the number of voxels where the mask
volume has a non-zero value and the corresponding voxels in the data
volume have values within the specified threshold range (between
`min_threshold` and `max_threshold` inclusive). The count is printed to
standard output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`mask_volume.mnc`
:   The mask MINC volume. Only voxels with non-zero values in this volume
    are considered.

`volume.mnc`
:   The data MINC volume whose values are checked against the threshold.

`min_threshold`
:   The minimum value for the threshold range.

`max_threshold`
:   The maximum value for the threshold range.

## EXAMPLES

Count voxels within the mask where volume values are between 50 and 200:

    count_thresholded_volume mask.mnc data.mnc 50 200

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincstats](mincstats) [mask_volume](mask_volume)
