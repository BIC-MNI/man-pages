---
section: 1
title: pipeline_qc_t2t1.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc_t2t1.pl

generate QC image for T1/T2 co-registration overlay

`pipeline_qc_t2t1.pl <t1> <t2> <candID> <visit> <age> <output.jpg>`

## DESCRIPTION

**pipeline_qc_t2t1.pl** generates a quality control image showing the
co-registration between T1-weighted and T2-weighted volumes. The two modalities
are overlaid using a colour scheme that makes misalignment clearly visible,
allowing rapid visual assessment of registration quality.

The output image is annotated with candidate ID, visit label, and age for
identification during batch QC review. Good co-registration will show
anatomical structures in proper alignment across both modalities, while poor
registration will show colour fringing at tissue boundaries.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate a placeholder QC image without performing actual rendering.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Generate a T1/T2 co-registration QC image:

    pipeline_qc_t2t1.pl t1_tal.mnc t2_tal.mnc CAND001 V1 25 qc_t2t1.jpg

Generate with verbose output:

    pipeline_qc_t2t1.pl t1_tal.mnc t2_tal.mnc CAND001 V1 25 qc_t2t1.jpg \
      --verbose

Generate a placeholder image:

    pipeline_qc_t2t1.pl t1_tal.mnc t2_tal.mnc CAND001 V1 25 qc_t2t1.jpg \
      --fake

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minc_qc_t2t1.pl](minc_qc_t2t1.pl)
