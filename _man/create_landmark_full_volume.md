---
section: 1
title: create_landmark_full_volume
author: David MacDonald
group: Surface and Geometry Tools
---
# create_landmark_full_volume

create a label volume from landmark tag files

`create_landmark_full_volume example_volume output_volume structure_id|-1 n|0 radius tag_file1 tag_file2 ...`

## DESCRIPTION

`create_landmark_full_volume` creates a label volume from one or more
landmark tag files. Each tag point is expanded into a sphere of the
specified radius and assigned the given structure ID label. If
`structure_id` is -1, the structure IDs are read from the tag files. The
`n` parameter controls how many tag points to use (0 for all). The
example volume provides the sampling grid for the output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`example_volume`
:   The input MINC volume providing the spatial sampling grid.

`output_volume`
:   The output MINC label volume.

`structure_id|-1`
:   The label value to assign to each landmark region, or -1 to use
    structure IDs from the tag files.

`n|0`
:   The number of tag points to use, or 0 for all tag points.

`radius`
:   The radius (in mm) of the sphere placed at each tag point.

`tag_file1 tag_file2 ...`
:   One or more tag point files containing landmark positions.

## EXAMPLES

Create landmarks from a tag file with structure ID 5 and radius 3mm:

    create_landmark_full_volume template.mnc output.mnc 5 0 3.0 landmarks.tag

Use structure IDs from the tag file:

    create_landmark_full_volume template.mnc output.mnc -1 0 2.0 landmarks.tag

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[create_four_volumes](create_four_volumes) [tag_volume](tag_volume) [tagtominc](tagtominc)
