---
section: 1
title: extract_tag_slice
author: David MacDonald
group: Tag Point Tools
---
# extract_tag_slice

extract tag points lying on a specified slice of a volume

`extract_tag_slice volume output.tag x|y|z slice_mm [min] [max]`

## DESCRIPTION

`extract_tag_slice` creates a tag file from a volume by extracting only
the tag points that lie on the specified slice. The slice is given as a
position in millimetres along the chosen axis (x, y, or z). An optional
range of label values can be specified to select only tags with labels in
that range. If no range is given, all non-zero labels are output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume`
:   The input MINC volume.

`output.tag`
:   The output tag file.

`x|y|z`
:   The axis along which to select the slice.

`slice_mm`
:   The slice position in millimetres along the chosen axis.

`min`
:   Optional minimum label value. Only tags with labels at or above this
    value are included.

`max`
:   Optional maximum label value. Only tags with labels at or below this
    value are included.

## EXAMPLES

Extract tags from the z=10mm slice:

    extract_tag_slice volume.mnc output.tag z 10

Extract tags from the x=0mm slice with labels between 3 and 5:

    extract_tag_slice volume.mnc output.tag x 0 3 5

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[extracttag](extracttag) [clip_tags](clip_tags) [chop_tags](chop_tags)
