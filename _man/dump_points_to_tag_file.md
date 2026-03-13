---
section: 1
title: dump_points_to_tag_file
author: David MacDonald
group: Tag Point Tools
---
# dump_points_to_tag_file

write surface object points to a tag file

`dump_points_to_tag_file input1.obj [input2.obj] output.txt`

## DESCRIPTION

`dump_points_to_tag_file` reads the vertex positions from one or two
surface object files and writes them as tag points to a tag file. If two
input surfaces are provided, corresponding vertices from both surfaces are
written as paired tag points.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input1.obj`
:   The first input surface object file.

`input2.obj`
:   An optional second input surface object file for paired tag points.

`output.txt`
:   The output tag file containing the vertex positions.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[extracttag](extracttag) [flip_tags](flip_tags) [interpolate_tags](interpolate_tags)
