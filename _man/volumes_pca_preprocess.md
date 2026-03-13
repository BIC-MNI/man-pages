---
section: 1
title: volumes_pca_preprocess
author: Vladimir S. Fonov
group: EZminc PCA and Linear Modelling
---
# volumes_pca_preprocess

Preprocess volumes for PCA analysis.

`volumes_pca_preprocess [options] <training_list> <output_prefix>`

## DESCRIPTION

**volumes_pca_preprocess** preprocesses a set of MINC volumes listed in a
training file in preparation for principal component analysis. The tool
computes the mean volume and subtracts it from each input, writing the
centered volumes and preprocessing data using the specified output prefix.

This preprocessing step is typically run before **volumes_pca** to prepare
the data for efficient PCA computation on large datasets.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--threshold` *f*
:   Set the variance threshold for preprocessing. Default: 0.98.

## EXAMPLES

Preprocess volumes for PCA:

    volumes_pca_preprocess training_list.txt preprocessed_

Preprocess with verbose output:

    volumes_pca_preprocess --verbose training_list.txt preprocessed_

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volumes_pca](volumes_pca), [volumes_lm](volumes_lm), [grids_pca](grids_pca)
