---
section: 1
title: find_tag_outliers
author: David MacDonald
group: Tag Point Tools
---
# find_tag_outliers

identify tag points that deviate significantly from expected positions

`find_tag_outliers avg_tags.mnc avg_threshold tag_threshold input_tags.tag`

## DESCRIPTION

`find_tag_outliers` identifies outlier tag points that deviate from the
average by more than the specified thresholds. The average tag positions
are derived from a volume, and any tag point whose distance from the
average exceeds the `tag_threshold` is flagged as an outlier.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`avg_tags.mnc`
:   The input MINC volume representing average tag positions.

`avg_threshold`
:   The threshold applied to the average volume.

`tag_threshold`
:   The distance threshold above which a tag point is considered an outlier.

`input_tags.tag`
:   The input tag file containing the tag points to evaluate.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[stats_tag_file](stats_tag_file) [clip_tags](clip_tags) [match_tags](match_tags)
