---
section: 1
title: f_prob
author: David MacDonald
group: Statistical and Analysis Tools
---
# f_prob

compute F-statistic probability values

`f_prob resels D m n t`

## DESCRIPTION

`f_prob` computes the F-probability value for a given number of resolution
elements (resels) and statistical parameters. This is used in random field
theory-based statistical inference for neuroimaging data.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`resels`
:   The number of resolution elements.

`D`
:   The dimensionality of the search region.

`m`
:   The numerator degrees of freedom.

`n`
:   The denominator degrees of freedom.

`t`
:   The F-statistic threshold value.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[compute_resels](compute_resels) [group_diff](group_diff)
