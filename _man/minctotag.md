---
section: 1
title: minctotag
author: David MacDonald
group: Tag Point Tools
---
# minctotag

convert labelled voxels in a MINC volume to a tag point file

`minctotag volume output.tag [id]`

`minctotag volume output.tag min_id max_id`

## DESCRIPTION

**minctotag** converts voxels in a MINC volume to a tag point file. Each
selected voxel is output as a tag point at the world coordinate
corresponding to the voxel centre.

When called with a single *id* argument, only voxels with values equal to
*id* are converted to tags. When called with *min_id* and *max_id*, voxels
with values in the range [*min_id*, *max_id*] are converted. When called
without an id argument, all non-zero voxels are converted to tag points.

The output tag file can be used with tools such as **Display** or
**Register** for visualization or further analysis.

## EXAMPLES

Convert all non-zero voxels to tags:

    minctotag labels.mnc output.tag

Convert only voxels with label 3:

    minctotag labels.mnc output.tag 3

Convert voxels with labels 1 through 5:

    minctotag labels.mnc output.tag 1 5

## SEE ALSO

[tagtominc](tagtominc), [extracttag](extracttag),
[dump_points_to_tag_file](dump_points_to_tag_file)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
