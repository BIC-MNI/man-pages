---
section: 1
title: pipeline_qc_nl.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc_nl.pl

generate QC images for nonlinear classification and lobe segmentation

`pipeline_qc_nl.pl <t1w> <lc_clean> <nl_lobes> <candID> <visit> <age> <out_lc> <out_nl>`

## DESCRIPTION

**pipeline_qc_nl.pl** generates quality control images for reviewing the
results of nonlinear tissue classification and lobe segmentation. It produces
two output images: one showing the cleaned tissue classification overlaid on
the T1-weighted volume, and another showing the lobe segmentation labels.

These QC images are essential for verifying that the classification and
segmentation pipelines have produced anatomically correct results. The images
are annotated with the candidate ID, visit label, and age for identification
during batch QC review.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate placeholder QC images without performing actual rendering.

`--clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Generate classification and lobe segmentation QC images:

    pipeline_qc_nl.pl t1_tal.mnc cls_clean.mnc lobes.mnc \
      CAND001 V1 25 qc_cls.jpg qc_lobes.jpg

Generate with verbose output:

    pipeline_qc_nl.pl t1_tal.mnc cls_clean.mnc lobes.mnc \
      CAND001 V1 25 qc_cls.jpg qc_lobes.jpg --verbose

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minc_qc.pl](minc_qc.pl), [pipeline_segment.pl](pipeline_segment.pl)
