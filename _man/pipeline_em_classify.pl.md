---
section: 1
title: pipeline_em_classify.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_em_classify.pl

EM-based brain tissue classification

`pipeline_em_classify.pl <t1_sel> <t2_sel> <pd_sel> <source_list> <t1_tal>`

## DESCRIPTION

**pipeline_em_classify.pl** performs brain tissue classification using an
Expectation-Maximization (EM) algorithm. Unlike the standard classification
pipeline which uses **classify_clean**, this script uses **em_classify** to
iteratively estimate tissue class parameters and assign voxels to white matter,
grey matter, and cerebrospinal fluid.

The script takes T1, T2, and PD selection flags, a source list file describing
the input volumes, and a T1 volume in Talairach space. The EM approach can be
more robust in cases where the standard classifier produces suboptimal results,
particularly with non-standard intensity distributions.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Run EM classification with all three modalities:

    pipeline_em_classify.pl 1 1 1 sources.txt t1_tal.mnc

Run EM classification with T1 only:

    pipeline_em_classify.pl 1 0 0 sources.txt t1_tal.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_classify.pl](pipeline_classify.pl), [em_classify](em_classify)
