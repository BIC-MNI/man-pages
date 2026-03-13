---
section: 1
title: pipeline_qc.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc.pl

generate QC images for T1/mask and T1/T2 overlays

`pipeline_qc.pl <mask> <t1> <t2> <candID> <visit> <age> <out_t1msk.jpg> <out_t1t2.jpg>`

## DESCRIPTION

**pipeline_qc.pl** generates quality control (QC) images for visual inspection
of processing results. It produces two output images: a T1-weighted volume with
brain mask overlay showing the quality of brain extraction, and a T1/T2
co-registration overlay showing the alignment between modalities.

The images are annotated with the candidate ID, visit label, and age for easy
identification during QC review. The **--fake** option generates placeholder
images without performing actual rendering, useful for pipeline testing.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate placeholder QC images without performing actual rendering.
    Useful for testing pipeline flow.

`--clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Generate QC images for a subject:

    pipeline_qc.pl brain_mask.mnc t1_tal.mnc t2_tal.mnc \
      CAND001 V1 25 qc_t1mask.jpg qc_t1t2.jpg

Generate with verbose output:

    pipeline_qc.pl brain_mask.mnc t1_tal.mnc t2_tal.mnc \
      CAND001 V1 25 qc_t1mask.jpg qc_t1t2.jpg --verbose

Generate placeholder images for testing:

    pipeline_qc.pl brain_mask.mnc t1_tal.mnc t2_tal.mnc \
      CAND001 V1 25 qc_t1mask.jpg qc_t1t2.jpg --fake

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minc_qc.pl](minc_qc.pl)
