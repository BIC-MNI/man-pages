---
section: 1
title: pipeline_launch_all_segment.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_launch_all_segment.pl

launch all segmentation pipeline variants for a subject visit

`pipeline_launch_all_segment.pl <subject_visit>`

## DESCRIPTION

**pipeline_launch_all_segment.pl** is a convenience script that launches all
available segmentation sub-pipelines for a given subject visit. This includes
tissue classification, lobe segmentation, and related processing steps. It
automates the sequential execution of the individual segmentation pipeline
components, ensuring consistent processing across subjects.

The script takes a subject visit identifier and runs the full suite of
segmentation tools, including classification and lobe segmentation, using the
standard pipeline conventions for file naming and directory structure.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite output files if they already exist.

`-noresample`
:   Skip resampling steps, using previously resampled volumes if available.

## EXAMPLES

Launch all segmentation pipelines for a subject visit:

    pipeline_launch_all_segment.pl subject01_visit1

Launch with verbose output:

    pipeline_launch_all_segment.pl subject01_visit1 -verbose

Launch with clobber to reprocess:

    pipeline_launch_all_segment.pl subject01_visit1 -clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_segment.pl](pipeline_segment.pl), [pipeline_classify.pl](pipeline_classify.pl)
