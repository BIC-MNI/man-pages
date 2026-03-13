---
section: 1
title: pipeline_jacobian.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_jacobian.pl

compute Jacobian determinant from a nonlinear deformation grid

`pipeline_jacobian.pl <grid.mnc> <output_jacobian.mnc>`

## DESCRIPTION

**pipeline_jacobian.pl** computes the Jacobian determinant map from a nonlinear
deformation grid file. The Jacobian determinant at each voxel represents the
local volume change induced by the nonlinear transformation: values greater
than 1 indicate local expansion, values less than 1 indicate local contraction,
and a value of exactly 1 indicates no volume change.

The input is a MINC deformation grid file (typically the grid component of a
nonlinear transform produced by **minctracc** or **nlfit_s**), and the output
is a scalar MINC volume containing the determinant values. This map is used
in deformation-based morphometry (DBM) and for Jacobian modulation of tissue
probability maps.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Compute the Jacobian determinant from a nonlinear grid:

    pipeline_jacobian.pl nl_grid.mnc jacobian.mnc

Compute with verbose output and overwrite existing file:

    pipeline_jacobian.pl nl_grid.mnc jacobian.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_dbm.pl](pipeline_dbm.pl), [mincblob](mincblob)
