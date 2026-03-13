---
section: 1
title: find_peaks
author: David MacDonald
group: Statistical and Analysis Tools
---
# find_peaks

find local maxima (peaks) in a MINC volume

`find_peaks [options] in.mnc out.tag`

## DESCRIPTION

`find_peaks` identifies local maxima and minima (peaks) in a MINC volume
and writes their positions as tag points to an output tag file. Positive
peaks are voxels above the positive threshold that are locally maximal,
and negative peaks are voxels below the negative threshold that are
locally minimal. Thresholds default to 80% and 20% of the full intensity
range respectively.

## OPTIONS

`-quiet`
:   Do not print out log messages.

`-verbose`
:   Print out log messages. This is the default.

`-veryverbose`
:   Print out a lot of log messages.

`-exclude_edges`
:   Exclude voxels at the edges of the volume. This is the default.

`-include_edges`
:   Include voxels at the edges of the volume.

`-pos_threshold`
:   Threshold for positive peaks. Defaults to 80% of the full range.

`-neg_threshold`
:   Threshold for negative peaks. Defaults to 20% of the full range.

`-pos_only`
:   Write out only positive peaks.

`-neg_only`
:   Write out only negative peaks.

`-min_distance`
:   Specify the minimum distance between peaks. Defaults to 0.

## EXAMPLES

Find peaks with default settings:

    find_peaks input.mnc peaks.tag

Find only positive peaks above a threshold of 100:

    find_peaks -pos_only -pos_threshold 100 input.mnc peaks.tag

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[gaussian_blur_peaks](gaussian_blur_peaks) [mincstats](mincstats)
