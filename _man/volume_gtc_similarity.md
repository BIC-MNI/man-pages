---
section: 1
title: volume_gtc_similarity
author: Vladimir S. Fonov
group: EZminc Volume Similarity
---
# volume_gtc_similarity

Calculate generalized Tanimoto coefficient and overlap metrics for discrete labels.

`volume_gtc_similarity [options] <input1.mnc> <input2.mnc>`

## DESCRIPTION

**volume_gtc_similarity** calculates the generalized Tanimoto coefficient (GTC)
and other overlap metrics between two discrete label volumes. The method is
based on Crum, Camara, and Hill (2006), "Generalized Overlap Measures for
Evaluation and Validation in Medical Image Analysis" (IEEE Transactions on
Medical Imaging).

The tool computes per-label and aggregate similarity metrics, useful for
evaluating segmentation accuracy against a reference.

## OPTIONS

`--background`
:   Include the background label (label 0) in the similarity computation.

`--gkappa`
:   Compute the generalized kappa statistic.

`--gtc`
:   Compute the generalized Tanimoto coefficient.

`--akappa`
:   Compute the average kappa statistic across labels.

`--csv`
:   Output results in CSV format.

`--exclude` *l1[,l2,...]*
:   Exclude the specified labels from the computation.

`--include` *l1[,l2,...]*
:   Include only the specified labels in the computation.

## EXAMPLES

Compute GTC between two label volumes:

    volume_gtc_similarity --gtc labels_auto.mnc labels_manual.mnc

Compute generalized kappa in CSV format:

    volume_gtc_similarity --gkappa --csv labels_auto.mnc labels_manual.mnc

Compute metrics excluding labels 0 and 4:

    volume_gtc_similarity --gtc --exclude 0,4 labels_auto.mnc labels_manual.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volume_similarity](volume_similarity), [fuzzy_volume_similarity](fuzzy_volume_similarity)
