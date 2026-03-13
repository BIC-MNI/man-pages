---
section: 1
title: pipeline_qc_t1w.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc_t1w.pl

generate QC image for T1w in Talairach space with outline overlay

`pipeline_qc_t1w.pl <tal_t1w> <candID> <visit> <age> <output> [--outline <file>]`

## DESCRIPTION

**pipeline_qc_t1w.pl** generates a quality control image of a T1-weighted
volume in Talairach space, optionally with a brain outline overlay. The outline
helps verify that the stereotaxic registration has correctly aligned the brain
to the template coordinate system.

The output image shows representative slices of the T1 volume with the
candidate ID, visit label, and age annotated. When an outline file is provided,
it is rendered on top of the T1 slices to show the expected brain boundaries.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate a placeholder QC image without performing actual rendering.

`--clobber`
:   Overwrite the output file if it already exists.

`--outline <file>`
:   Brain outline file to overlay on the T1-weighted volume for registration
    quality assessment.

## EXAMPLES

Generate a T1w QC image:

    pipeline_qc_t1w.pl t1_tal.mnc CAND001 V1 25 qc_t1w.jpg

Generate with brain outline overlay:

    pipeline_qc_t1w.pl t1_tal.mnc CAND001 V1 25 qc_t1w.jpg \
      --outline icbm_outline.mnc

Generate a placeholder image for testing:

    pipeline_qc_t1w.pl t1_tal.mnc CAND001 V1 25 qc_t1w.jpg --fake

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minc_qc.pl](minc_qc.pl)
