---
section: 1
title: grids_pca
author: Vladimir S. Fonov
group: EZminc PCA and Linear Modelling
---
# grids_pca

Perform principal component analysis on deformation grid files.

`grids_pca [options] <training_list> <output_prefix>`

## DESCRIPTION

**grids_pca** performs Principal Component Analysis (PCA) on a set of
deformation grid files listed in a training file. Each line of the training
list specifies a deformation grid volume. The tool computes the mean
deformation field and the principal components of variation, writing
the results with the specified output prefix.

This is useful for building statistical models of anatomical variability
from a set of non-linear registration results.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask` *mask.mnc*
:   Restrict PCA computation to voxels within the specified binary mask.

`--threshold` *f*
:   Set the variance threshold for retaining principal components. Components
    are retained until the cumulative explained variance reaches this fraction.
    Default: 0.98.

`--nomean`
:   Do not subtract the mean deformation field before computing PCA.

`--cache`
:   Cache input grid files in memory for faster processing.

`--normalize`
:   Normalize the input deformation fields before PCA.

## EXAMPLES

Compute PCA on a set of deformation grids:

    grids_pca training_list.txt output_pca_

Compute PCA with a mask and 95% variance threshold:

    grids_pca --mask brainmask.mnc --threshold 0.95 training_list.txt output_pca_

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volumes_pca](volumes_pca), [volumes_pca_preprocess](volumes_pca_preprocess)
