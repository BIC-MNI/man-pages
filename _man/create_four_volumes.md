---
section: 1
title: create_four_volumes
author: David MacDonald
group: Volume Operations
---
# create_four_volumes

create four class volumes from multiple input volumes or tag files

`create_four_volumes output_prefix input1.mnc input2.mnc ...`
`create_four_volumes output_prefix example.mnc input1.tag input2.tag ...`

## DESCRIPTION

`create_four_volumes` creates four class volumes from multiple input MINC
volumes or from tag files using an example volume as a spatial reference.
In the first form, the inputs are MINC volumes. In the second form, an
example MINC volume provides the sampling grid and tag point files
provide the class information. The output files are named using the
specified prefix.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`output_prefix`
:   The prefix for the output volume filenames.

`input1.mnc input2.mnc ...`
:   Input MINC volumes (first form).

`example.mnc`
:   An example MINC volume providing the spatial sampling grid (second
    form).

`input1.tag input2.tag ...`
:   Input tag point files (second form).

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[create_landmark_full_volume](create_landmark_full_volume) [tag_volume](tag_volume)
