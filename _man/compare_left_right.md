---
section: 1
title: compare_left_right
author: David MacDonald
group: Statistical and Analysis Tools
---
# compare_left_right

compare left and right hemispheres of surface objects

`compare_left_right output.mnc ni nj input1.obj input2.obj ...`
`compare_left_right output.mnc 0 0 y z input1.obj input2.obj ...`

## DESCRIPTION

`compare_left_right` compares the left and right hemispheres of one or
more cortical surface objects and writes the asymmetry results to a MINC
output file. In the first form, `ni` and `nj` specify the dimensions of
the output grid. In the second form, setting both to 0 and providing y
and z axis labels selects an alternative output mode.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`output.mnc`
:   The output MINC volume containing hemisphere comparison results.

`ni`
:   Number of grid divisions in the first dimension (or 0 for alternative
    mode).

`nj`
:   Number of grid divisions in the second dimension (or 0 for alternative
    mode).

`input1.obj input2.obj ...`
:   One or more surface object files to compare.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compare_left_right_groups](compare_left_right_groups) [compare_lengths](compare_lengths)
