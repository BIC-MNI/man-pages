---
section: 1
title: chop_tags
author: David MacDonald
group: Tag Point Tools
---
# chop_tags

clip tag points to those within specified coordinate ranges

`chop_tags input.tag output.tag [x|y|z min max] [x|y|z min max] ...`

## DESCRIPTION

`chop_tags` reads a tag point file and writes a new tag file containing
only those tag points that fall within all of the specified axis-aligned
bounding limits. Any number of axis/min/max triples can be given to
constrain the x, y, and/or z coordinates.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`x|y|z`
:   The axis along which to apply the clipping limit.

`min`
:   The minimum coordinate value along the specified axis.

`max`
:   The maximum coordinate value along the specified axis.

## EXAMPLES

Keep only tags with x between -50 and 50:

    chop_tags input.tag output.tag x -50 50

Keep tags within x and z ranges:

    chop_tags input.tag output.tag x -50 50 z -30 30

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[clip_tags](clip_tags) [transformtags](transformtags)
