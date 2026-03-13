---
section: 1
title: transform_tags
author: David MacDonald
group: Tag Point Tools
---
# transform_tags

apply a spatial transformation to a tag point file

`transform_tags input.tag input.xfm [output.tag] [invert]`

## DESCRIPTION

**transform_tags** applies a spatial transformation to all tag points in the
input tag file. The transformation is read from an MNI transform (.xfm) file.

If **output.tag** is specified, the transformed tags are written to that file.
Otherwise, the input tag file is overwritten.

If a fourth argument is present (any string, e.g. "invert"), the inverse of
the transform is applied instead.

## EXAMPLES

    transform_tags landmarks.tag linear.xfm transformed.tag

    transform_tags landmarks.tag nonlinear.xfm output.tag invert

## SEE ALSO

[transform_objects](transform_objects), [transform_volume](transform_volume),
[transformtags](transformtags), [xfminvert](xfminvert)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
