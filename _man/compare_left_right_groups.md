---
section: 1
title: compare_left_right_groups
author: David MacDonald
group: Statistical and Analysis Tools
---
# compare_left_right_groups

compare left-right hemisphere differences between groups of surface objects

`compare_left_right_groups output.mnc ni nj input1.obj input2.obj + ...`

## DESCRIPTION

`compare_left_right_groups` compares left and right hemisphere asymmetry
differences between groups of cortical surface objects. Groups of surface
files are separated by a `+` delimiter on the command line. The results
are written to a MINC output volume on a grid of dimensions `ni` by `nj`.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`output.mnc`
:   The output MINC volume containing group comparison results.

`ni`
:   Number of grid divisions in the first dimension.

`nj`
:   Number of grid divisions in the second dimension.

`input1.obj input2.obj + ...`
:   Surface object files for each group, with groups separated by `+`.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compare_left_right](compare_left_right) [group_diff](group_diff)
