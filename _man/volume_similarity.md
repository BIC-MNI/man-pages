---
section: 1
title: volume_similarity
author: Vladimir S. Fonov
group: EZminc Volume Similarity
---
# volume_similarity

Calculate volume similarity metrics for binary label volumes.

`volume_similarity [options] <ground_truth.mnc> <test.mnc>`

## DESCRIPTION

**volume_similarity** calculates overlap-based similarity metrics between two
binary label volumes, typically a ground truth segmentation and an automated
segmentation result. The tool computes Cohen's kappa, sensitivity (true
positive rate), specificity (true negative rate), and Jaccard index.

The method is based on Feuerman and Miller (2008) for kappa computation.

## OPTIONS

`--kappa`
:   Report Cohen's kappa coefficient.

`--sensitivity`
:   Report sensitivity (true positive rate).

`--specificity`
:   Report specificity (true negative rate).

`--jaccard`
:   Report the Jaccard index (intersection over union).

`--verbose`
:   Print all available similarity metrics.

`--csv`
:   Output results in CSV format.

## EXAMPLES

Compute all similarity metrics:

    volume_similarity --verbose ground_truth.mnc test_seg.mnc

Compute kappa in CSV format:

    volume_similarity --kappa --csv ground_truth.mnc test_seg.mnc

Compute Jaccard and sensitivity:

    volume_similarity --jaccard --sensitivity ground_truth.mnc test_seg.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volume_gtc_similarity](volume_gtc_similarity), [fuzzy_volume_similarity](fuzzy_volume_similarity)
