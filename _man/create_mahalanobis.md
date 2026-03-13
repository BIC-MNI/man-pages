---
section: 1
title: create_mahalanobis
author: David MacDonald
group: Label and Classification Tools
---
# create_mahalanobis

compute Mahalanobis distance between a sample and a mean surface

`create_mahalanobis avg.obj variance.txt sample.obj output.txt`

## DESCRIPTION

`create_mahalanobis` computes the Mahalanobis distance between a sample
surface and a mean (average) surface with known variance. The mean surface
is provided as an object file, the per-vertex variance is read from a text
file, and the sample surface is another object file. The resulting
per-vertex Mahalanobis distances are written to the output text file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`avg.obj`
:   The mean (average) surface object file.

`variance.txt`
:   A text file containing per-vertex variance values.

`sample.obj`
:   The sample surface object file to compare against the mean.

`output.txt`
:   The output text file containing per-vertex Mahalanobis distances.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[diff_mahalanobis](diff_mahalanobis) [compare_lengths](compare_lengths)
