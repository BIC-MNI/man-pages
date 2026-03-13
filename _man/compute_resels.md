---
section: 1
title: compute_resels
author: David MacDonald
group: Statistical and Analysis Tools
---
# compute_resels

compute resolution elements (resels) from cortical surface meshes

`compute_resels [surfA1.obj] [surfA2.obj] ... + [surfB1.obj] [surfB2.obj] ...`

## DESCRIPTION

`compute_resels` computes the number of resolution elements (resels) from
one or more cortical surface meshes. Resels are a measure of the
effective number of independent observations on the surface, accounting
for spatial smoothness. Two groups of surfaces can be separated by a `+`
delimiter on the command line for group comparisons.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`surfA1.obj surfA2.obj ...`
:   Surface object files for the first group.

`+`
:   Delimiter separating the two groups of surface files.

`surfB1.obj surfB2.obj ...`
:   Surface object files for the second group.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compare_left_right_groups](compare_left_right_groups) [group_diff](group_diff)
