---
section: 1
title: volumes_pca
author: Vladimir S. Fonov
group: EZminc PCA and Linear Modelling
---
# volumes_pca

Perform principal component analysis on a set of MINC volumes.

`volumes_pca [options] <training_list> <output_prefix>`

## DESCRIPTION

**volumes_pca** performs Principal Component Analysis (PCA) on a set of MINC
volumes specified in a training list file. Each line of the training list
contains the path to a volume. The tool computes the mean volume and the
principal components of variation across the set, writing the results
with the specified output prefix.

This is useful for building statistical shape or appearance models from
a population of brain images.

## OPTIONS

`--mask` *mask.mnc*
:   Restrict PCA computation to voxels within the specified binary mask.

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--normalize`
:   Normalize the input volumes before PCA.

`--nobias`
:   Do not apply bias correction during PCA.

`--threshold` *f*
:   Set the variance threshold for retaining principal components. Components
    are retained until the cumulative explained variance reaches this fraction.
    Default: 0.98.

## EXAMPLES

Compute PCA on a set of volumes:

    volumes_pca training_list.txt pca_output_

Compute PCA with normalization and a mask:

    volumes_pca --normalize --mask brainmask.mnc training_list.txt pca_output_

Retain 95% of variance:

    volumes_pca --threshold 0.95 training_list.txt pca_output_

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volumes_pca_preprocess](volumes_pca_preprocess), [volumes_lm](volumes_lm), [grids_pca](grids_pca)
