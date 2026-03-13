---
section: 1
title: fit_curve2
author: David MacDonald
group: Surface and Geometry Tools
---
# fit_curve2

fit a piecewise linear curve to a set of points

`fit_curve2 input_lines.tag output_lines.obj n_mm_per_segment [stretch_weight] [smoothness_weight] [disjoint_distance]`

## DESCRIPTION

`fit_curve2` creates a piecewise linear curve that approximates the set of
points in a tag file. The `n_mm_per_segment` parameter sets the length of
each line segment in millimetres, controlling the resolution of the output
curve. Optional stretch and smoothness weights control the fitting
behaviour, and a disjoint distance may be specified to handle gaps in the
input points.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input_lines.tag`
:   The input tag file containing the points to fit.

`output_lines.obj`
:   The output line object file containing the fitted curve.

`n_mm_per_segment`
:   The length of each line segment in millimetres.

`stretch_weight`
:   Optional weight controlling the stretch penalty in the fit.

`smoothness_weight`
:   Optional weight controlling the smoothness of the fit.

`disjoint_distance`
:   Optional distance threshold for treating points as belonging to
    disjoint segments.

## EXAMPLES

Fit a piecewise linear curve with 2mm segments:

    fit_curve2 points.tag curve.obj 2

Fit with stretch weight 0.5 and smoothness weight 0.1:

    fit_curve2 points.tag curve.obj 2 0.5 0.1

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[fit_curve](fit_curve) [reparameterize_line](reparameterize_line) [coalesce_lines](coalesce_lines)
