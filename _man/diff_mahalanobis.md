---
section: 1
title: diff_mahalanobis
author: David MacDonald
group: Label and Classification Tools
---
# diff_mahalanobis

compute the difference in Mahalanobis distances between two groups

`diff_mahalanobis avg1.obj variance1.txt avg2.obj variance2.txt output`

## DESCRIPTION

`diff_mahalanobis` computes the difference between two Mahalanobis distance
maps derived from two mean surfaces with their associated per-vertex
variances. Each group is described by a mean surface object file and a
corresponding text file of per-vertex variance values. The resulting
per-vertex difference in Mahalanobis distances is written to the output file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`avg1.obj`
:   The mean surface object file for the first group.

`variance1.txt`
:   A text file containing per-vertex variance values for the first group.

`avg2.obj`
:   The mean surface object file for the second group.

`variance2.txt`
:   A text file containing per-vertex variance values for the second group.

`output`
:   The output file containing the per-vertex difference in Mahalanobis distances.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[create_mahalanobis](create_mahalanobis) [compare_lengths](compare_lengths)
