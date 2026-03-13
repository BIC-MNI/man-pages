---
section: 1
title: fdr_threshold
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# fdr_threshold

Compute False Discovery Rate (FDR) threshold for statistical maps.

`fdr_threshold [options] <input> <df> <significance %> [output]`

## DESCRIPTION

**fdr_threshold** computes the False Discovery Rate (FDR) threshold for a
statistical map (t-statistic or F-statistic volume). The method is based on
Genovese, Lazar, and Nichols (2002), "Thresholding of Statistical Maps in
Functional Neuroimaging Using the False Discovery Rate" (NeuroImage, 15:870-878).

The tool reads an input statistical map, the degrees of freedom, and the
desired significance level (as a percentage), and outputs the corresponding
FDR threshold value. Optionally, it can write a corrected p-value volume.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask` *mask*
:   Restrict computation to voxels within the specified binary mask.

`--twosided`
:   Perform a two-sided test (consider both tails of the distribution).

`--negative`
:   Invert t-statistics for single-sided tests (use negative tail).

`--pval`
:   Print the corrected p-value rather than the threshold.

`--fstats`
:   Treat the input as F-statistics instead of t-statistics.

`--df2` *n*
:   Specify the second degree of freedom (for F-statistics).

`--independent`
:   Use the less conservative independence assumption for FDR correction.

`--out` *output-pval.mnc*
:   Write a corrected p-value volume to the specified file.

## EXAMPLES

Compute FDR threshold at 5% significance for a t-map with 20 degrees of freedom:

    fdr_threshold tmap.mnc 20 5

Compute two-sided FDR threshold with a brain mask:

    fdr_threshold --twosided --mask brainmask.mnc tmap.mnc 20 5

Compute threshold for F-statistics with two degrees of freedom:

    fdr_threshold --fstats --df2 100 fmap.mnc 3 5

Save corrected p-value map:

    fdr_threshold --out pval_corrected.mnc tmap.mnc 20 5

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mincstats](mincstats), [minccalc](minccalc)
