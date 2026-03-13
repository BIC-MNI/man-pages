---
section: 1
title: tagtominc
author: David MacDonald
group: Tag Point Tools
---
# tagtominc

convert a tag file to a labelled MINC volume

`tagtominc example_volume.mnc input.tag output.mnc [structure_id|-1] [crop]`

## DESCRIPTION

**tagtominc** converts a tag point file into a MINC volume. Voxels at each tag
point location are set to the structure ID stored in the tag file. An example
MINC volume is required to define the output sampling grid (dimensions, voxel
sizes, and coordinate system).

If **structure_id** is specified, only tag points with that particular structure
ID are included in the output. A value of **-1** includes all tags (the
default behaviour).

If the **crop** argument is specified, the output MINC volume is cropped to the
bounding box of the tag points rather than using the full extent of the example
volume.

## EXAMPLES

    tagtominc template.mnc landmarks.tag output.mnc

    tagtominc template.mnc landmarks.tag output.mnc 3

    tagtominc template.mnc landmarks.tag output.mnc -1 crop

## SEE ALSO

[tag_volume](tag_volume), [extracttag](extracttag),
[tags_to_spheres](tags_to_spheres), [minctotag](minctotag)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
