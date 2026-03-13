---
section: 1
title: volumes_lm
author: Vladimir S. Fonov
group: EZminc PCA and Linear Modelling
---
# volumes_lm

Compute per-voxel linear models from a training list of volumes.

`volumes_lm [options] <training_list> <output_prefix>`

## DESCRIPTION

**volumes_lm** builds per-voxel linear models from a set of MINC volumes
specified in a training list file. Each line of the training list contains
the path to a volume and associated covariates. The tool estimates linear
model coefficients at each voxel and writes the resulting coefficient
volumes using the specified output prefix.

This tool is useful for building statistical models of anatomical variation
across a population, where each voxel's intensity is modeled as a linear
function of the provided covariates.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask` *mask.mnc*
:   Restrict the linear model computation to voxels within the specified
    binary mask.

`--buffers` *n*
:   Set the number of I/O buffers for reading input volumes. Default: 1000.

## EXAMPLES

Build a linear model from a training list:

    volumes_lm training_list.txt model_

Build a linear model with a mask:

    volumes_lm --mask brainmask.mnc training_list.txt model_

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volumes_lsq](volumes_lsq), [volumes_pca](volumes_pca)
