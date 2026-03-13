---
section: 1
title: dump_rms
author: David MacDonald
group: Statistical and Analysis Tools
---
# dump_rms

compute and dump RMS distance between two surfaces

`dump_rms input1.obj input2.obj output.txt`

## DESCRIPTION

`dump_rms` computes the root mean square (RMS) distance between
corresponding vertices of two surface objects and writes the result to an
output text file. The two surfaces must have the same number of vertices.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input1.obj`
:   The first input surface object file.

`input2.obj`
:   The second input surface object file.

`output.txt`
:   The output text file containing the RMS distance.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compare_lengths](compare_lengths) [dump_deformation_distances](dump_deformation_distances) [diff_mahalanobis](diff_mahalanobis)
