---
section: 1
title: pipeline_launch_pve.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_launch_pve.pl

launch all partial volume estimation pipeline variants

`pipeline_launch_pve.pl <subject_visit>`

## DESCRIPTION

**pipeline_launch_pve.pl** is a convenience script that launches all partial
volume estimation (PVE) pipeline variants for a given subject visit. It
automates the execution of the PVE processing steps, which estimate the
fractional tissue content of each voxel — accounting for the fact that a single
voxel may contain a mixture of white matter, grey matter, and cerebrospinal
fluid.

The script takes a subject visit identifier and runs the PVE pipeline using
the standard pipeline conventions for file naming and directory structure.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite output files if they already exist.

`-noresample`
:   Skip resampling steps, using previously resampled volumes if available.

## EXAMPLES

Launch PVE pipelines for a subject visit:

    pipeline_launch_pve.pl subject01_visit1

Launch with verbose output and overwrite:

    pipeline_launch_pve.pl subject01_visit1 -verbose -clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_pve.pl](pipeline_pve.pl)
