---
section: 1
title: volumes_lsq
author: Vladimir S. Fonov
group: EZminc PCA and Linear Modelling
---
# volumes_lsq

Compute per-voxel least-squares decomposition using linear model components.

`volumes_lsq [options] <file> <lm_file_1> ... <lm_file_n>`

## DESCRIPTION

**volumes_lsq** performs per-voxel least-squares decomposition of a MINC
volume using a set of linear model component volumes (typically produced by
**volumes_lm** or **volumes_pca**). The tool finds the least-squares
coefficients that best reconstruct the input volume from the provided
basis components, and outputs the coefficients.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask` *mask.mnc*
:   Restrict the computation to voxels within the specified binary mask.

`--fixed` *n*
:   Treat the first *n* components as fixed with weight 1 (e.g., for the
    mean component).

## EXAMPLES

Decompose a volume using linear model components:

    volumes_lsq subject.mnc model_comp1.mnc model_comp2.mnc model_comp3.mnc

Decompose with a mask and fixed mean component:

    volumes_lsq --mask brainmask.mnc --fixed 1 subject.mnc mean.mnc pc1.mnc pc2.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volumes_lm](volumes_lm), [volumes_pca](volumes_pca)
