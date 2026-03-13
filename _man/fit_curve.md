---
section: 1
title: fit_curve
author: David MacDonald
group: Surface and Geometry Tools
---
# fit_curve

fit a smooth cubic spline curve to a set of points

`fit_curve input_lines.tag output_lines.obj n_controls n_intervals [smoothness_weight] [disjoint_distance]`

## DESCRIPTION

`fit_curve` creates a cubic spline curve that approximates the set of
points in a tag file. The `n_controls` parameter sets the number of control
vertices, effectively controlling the smoothness of the spline — fewer
controls produce a smoother curve. The `n_intervals` parameter specifies
the number of intervals between each control vertex in the discretized
line that is finally output. An optional smoothness weight and disjoint
distance may be specified.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input_lines.tag`
:   The input tag file containing the points to fit.

`output_lines.obj`
:   The output line object file containing the fitted curve.

`n_controls`
:   The number of control vertices for the spline. Fewer controls yield a
    smoother curve.

`n_intervals`
:   The number of intervals between each control vertex in the output line.

`smoothness_weight`
:   Optional weight controlling the smoothness of the fit.

`disjoint_distance`
:   Optional distance threshold for treating points as belonging to
    disjoint segments.

## EXAMPLES

Fit a spline with 10 control points and 5 intervals:

    fit_curve points.tag curve.obj 10 5

Fit with a smoothness weight of 0.1:

    fit_curve points.tag curve.obj 10 5 0.1

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[fit_curve2](fit_curve2) [reparameterize_line](reparameterize_line) [coalesce_lines](coalesce_lines)
