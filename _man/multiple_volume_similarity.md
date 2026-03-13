---
section: 1
title: multiple_volume_similarity
author: Vladimir S. Fonov
group: EZminc Volume Similarity
---
# multiple_volume_similarity

calculate multiple volume discrete label similarity (GTC) metrics

`multiple_volume_similarity <input1.mnc> <input2.mnc> ... [options]`

## DESCRIPTION

**multiple_volume_similarity** computes the Generalized Tanimoto Coefficient
(GTC) across two or more label volumes. The GTC is an extension of the Dice
and Jaccard overlap metrics to multiple raters or segmentations simultaneously,
providing a single summary measure of inter-rater agreement for discrete label
maps.

The tool accepts any number of input MINC label volumes. All inputs must share
the same sampling grid (dimensions, voxel sizes, and orientation). By default,
the GTC is computed over all non-zero labels found in the input volumes.
Specific labels of interest can be selected with `--labels`, and the
computation can be restricted to a region of interest with `--mask`.

Output can be formatted as comma-separated values (`--csv`) for easy import
into spreadsheets or statistical software.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--csv`
:   Output results in comma-separated value (CSV) format.

`--labels` *list*
:   Comma-separated list of label values to include in the similarity computation. By default, all non-zero labels are used.

`--mask` *file*
:   Restrict the similarity computation to voxels within the given mask volume. Only voxels with non-zero values in the mask are included.

## EXAMPLES

Compute GTC across three label volumes:

    multiple_volume_similarity seg1.mnc seg2.mnc seg3.mnc

Compute similarity for specific labels in CSV format:

    multiple_volume_similarity seg1.mnc seg2.mnc --labels 1,2,3 --csv

Restrict computation to a brain mask:

    multiple_volume_similarity seg1.mnc seg2.mnc seg3.mnc --mask brain_mask.mnc --verbose

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_similarity](itk_similarity), [minccalc](minccalc), [mincstats](mincstats), [itk_morph](itk_morph)
