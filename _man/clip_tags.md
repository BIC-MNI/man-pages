---
section: 1
title: clip_tags
author: David MacDonald
group: Tag Point Tools
---
# clip_tags

clip tag points based on distance from a reference plane

`clip_tags 3_tags_file input.tag output.tag -distance +distance [mnc_file] [angle_increment] [angle_offset] [plane_filename]`

## DESCRIPTION

`clip_tags` clips tag points based on their distance from a plane defined
by three reference tag points. Points within the specified negative and
positive distance from the plane are retained. If an optional MINC file is
given, it can be used for additional spatial reference. Angle increment
and offset parameters control the orientation of the clipping plane, and
an optional plane filename can be provided to output the plane geometry.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`3_tags_file`
:   A tag file containing exactly three points that define the reference
    plane.

`input.tag`
:   The input tag point file to be clipped.

`output.tag`
:   The output tag file containing only the retained tag points.

`-distance`
:   The negative distance limit from the plane (tags closer to the plane
    than this on the negative side are excluded).

`+distance`
:   The positive distance limit from the plane (tags closer to the plane
    than this on the positive side are excluded).

`mnc_file`
:   An optional MINC volume for spatial reference.

`angle_increment`
:   Optional angle increment for plane orientation (in degrees).

`angle_offset`
:   Optional angle offset for plane orientation (in degrees).

`plane_filename`
:   Optional output file to write the clipping plane geometry.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[chop_tags](chop_tags) [transformtags](transformtags)
