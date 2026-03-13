---
section: 1
title: interpolate_tags
author: David MacDonald
group: Tag Point Tools
---
# interpolate_tags

interpolate tag points between two sets by a given ratio

`interpolate_tags input.tag output.tag ratio ...`

## DESCRIPTION

`interpolate_tags` reads a tag file containing two sets of tag points and
interpolates the second set of tags towards the first set by the given
ratio. A ratio of 0 leaves the second set unchanged, while a ratio of 1
moves the second set to match the first. Multiple ratios may be specified.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input.tag`
:   The input tag file containing two sets of tag points.

`output.tag`
:   The output tag file containing the interpolated tag points.

`ratio`
:   The interpolation ratio (0 to 1). Multiple ratios may be given.

## EXAMPLES

Interpolate halfway between two tag sets:

    interpolate_tags input.tag output.tag 0.5

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flip_tags](flip_tags) [transform_tags](transform_tags) [dump_points_to_tag_file](dump_points_to_tag_file)
