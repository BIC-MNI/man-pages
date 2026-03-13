---
section: 1
title: em_classify
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# em_classify

Classify voxels using expectation-maximization algorithm.

`em_classify [options] <input_1> ... <input_n> <output>`

## DESCRIPTION

**em_classify** performs tissue classification on one or more input MINC
volumes using the Expectation-Maximization (EM) algorithm. The EM algorithm
iteratively estimates class means, standard deviations, and voxel membership
probabilities to segment the input into a specified number of tissue classes.

Multiple input volumes (e.g., T1, T2, PD) can be provided for multispectral
classification. Initial class parameters can be supplied via command-line
options or estimated from training labels. Spatial prior probability maps
can also be used to guide the classification.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask` *mask.mnc*
:   Restrict classification to voxels within the specified binary mask volume.

`--train` *train.mnc*
:   Use the given label volume to initialize class parameters (means and
    standard deviations) from training data.

`--means` *c1,c2,...,cn*
:   Specify initial class means as a comma-separated list.

`--sigma` *s1,...,sn*
:   Specify initial class standard deviations as a comma-separated list.

`--classes` *n*
:   Set the number of tissue classes for classification.

`--prob` *p1,p2,...*
:   Specify a priori class probabilities as a comma-separated list. Values
    should sum to 1.

`--iter` *n*
:   Set the maximum number of EM iterations.

`--priors` *p1.mnc,p2.mnc,...,pn.mnc*
:   Provide spatial prior probability maps for each class as a comma-separated
    list of MINC files.

`--save_prob` *base*
:   Save posterior class probability maps using the specified base filename.

`--debug`
:   Enable debug output.

`--interpolate`
:   Use interpolation when resampling inputs.

## EXAMPLES

Classify a T1 volume into 3 classes using a brain mask:

    em_classify --classes 3 --mask brainmask.mnc t1.mnc classified.mnc

Classify with initial means and standard deviations:

    em_classify --classes 3 --means 300,700,1000 --sigma 50,80,100 t1.mnc classified.mnc

Classify using spatial priors and save probability maps:

    em_classify --classes 3 --priors csf_prior.mnc,gm_prior.mnc,wm_prior.mnc \
        --save_prob prob_ --mask brainmask.mnc t1.mnc classified.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[classify](classify), [mrfseg](mrfseg), [gamixture](gamixture)
