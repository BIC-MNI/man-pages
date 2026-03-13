---
section: 1
title: group_diff
author: David MacDonald
group: Statistical and Analysis Tools
---
# group_diff

compute group differences and F-statistics from surface data files

`group_diff output.f_stat [1] [-t] file1 file2 + file3 file4 ..`

## DESCRIPTION

`group_diff` computes group differences and F-statistics from per-vertex
surface data files. Two groups of files are separated by a `+` delimiter.
The resulting per-vertex F-statistic values are written to the output file.
The optional `1` flag modifies the output format, and the `-t` flag may be
used to select an alternative test statistic.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`output.f_stat`
:   The output file containing per-vertex F-statistic values.

`1`
:   Optional flag to modify the output format.

`-t`
:   Optional flag to select an alternative test statistic.

`file1 file2 ...`
:   Per-vertex data files for the first group.

`+`
:   Delimiter separating the two groups.

`file3 file4 ...`
:   Per-vertex data files for the second group.

## EXAMPLES

Compute F-statistics between two groups:

    group_diff result.f_stat group1a.txt group1b.txt + group2a.txt group2b.txt

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[f_prob](f_prob) [compute_resels](compute_resels)
