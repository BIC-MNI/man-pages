---
section: 1
title: flip_tags
author: David MacDonald
group: Tag Point Tools
---
# flip_tags

flip tags about the left-right centre of a volume

`flip_tags example.mnc input.tags output.tags`

## DESCRIPTION

`flip_tags` flips tag point positions about the left-right centre of a
reference volume. The reference volume is used to determine the centre
axis, and each tag point's position is mirrored across that axis. The
flipped tags are written to the output tag file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`example.mnc`
:   The reference MINC volume used to determine the left-right centre.

`input.tags`
:   The input tag file containing the tag points to flip.

`output.tags`
:   The output tag file containing the flipped tag points.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[flip_volume](flip_volume) [transform_tags](transform_tags) [interpolate_tags](interpolate_tags)
