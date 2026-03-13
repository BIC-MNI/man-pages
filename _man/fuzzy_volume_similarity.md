---
section: 1
title: fuzzy_volume_similarity
author: Vladimir S. Fonov
group: EZminc Volume Similarity
---
# fuzzy_volume_similarity

Calculate fuzzy volume similarity metrics for tissue probability maps.

`fuzzy_volume_similarity [options] <input1.mnc> <input2.mnc>`

## DESCRIPTION

**fuzzy_volume_similarity** calculates fuzzy volume similarity metrics between
two tissue probability map volumes. Unlike discrete label overlap measures,
this tool operates on continuous-valued volumes where voxel values represent
probabilities or membership values between 0 and 1.

The method is based on Crum, Camara, and Hill (2006), "Generalized Overlap
Measures for Evaluation and Validation in Medical Image Analysis" (IEEE
Transactions on Medical Imaging, 25(11):1451-1461).

## OPTIONS

`--verbose`
:   Print detailed similarity metrics.

`--mask` *mask.mnc*
:   Restrict the similarity computation to voxels within the specified
    binary mask.

## EXAMPLES

Compare two tissue probability maps:

    fuzzy_volume_similarity tissue_prob1.mnc tissue_prob2.mnc

Compare with a mask and verbose output:

    fuzzy_volume_similarity --verbose --mask brainmask.mnc prob1.mnc prob2.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volume_similarity](volume_similarity), [volume_gtc_similarity](volume_gtc_similarity)
