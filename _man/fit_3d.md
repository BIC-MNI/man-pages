---
section: 1
title: fit_3d
author: David MacDonald
group: Surface and Geometry Tools
---
# fit_3d

fit a deformable model to a MINC volume using surface deformation

`fit_3d input.obj output.obj model.obj model_weight centroid_weight volume.mnc threshold +|-|0 tangent_weight out_dist in_dist float/nofloat oversample [n_iters] [n_between] [max_step] [values_file min max]`

## DESCRIPTION

`fit_3d` fits a 3D surface to a volume using a deformable model approach.
The input surface is iteratively deformed towards the boundary defined by
the volume threshold. The deformation is controlled by a model surface
(with `model_weight`), a centroid constraint (`centroid_weight`), and a
tangent weight. The direction of deformation is specified as `+` (outward),
`-` (inward), or `0` (both). The `out_dist` and `in_dist` parameters limit
the search range. The `float/nofloat` option controls whether vertices
float freely. An optional `values_file` with a min/max range can further
constrain the deformation.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`model.obj`
:   The model surface object used as a shape prior.

`model_weight`
:   Weight of the model shape constraint.

`centroid_weight`
:   Weight of the centroid constraint.

`threshold`
:   Volume intensity threshold defining the target boundary.

`+|-|0`
:   Direction of deformation: `+` for outward, `-` for inward, `0` for both.

`tangent_weight`
:   Weight of the tangential smoothness constraint.

`out_dist`
:   Maximum outward search distance.

`in_dist`
:   Maximum inward search distance.

`float/nofloat`
:   Whether vertices float freely (`float`) or are constrained (`nofloat`).

`oversample`
:   Oversampling factor for the deformation.

`n_iters`
:   Optional number of deformation iterations.

`n_between`
:   Optional number of iterations between convergence checks.

`max_step`
:   Optional maximum step size per iteration.

`values_file min max`
:   Optional per-vertex values file with a valid range to constrain deformation.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[marching_cubes](marching_cubes) [surface_mask](surface_mask) [close_surface](close_surface)
