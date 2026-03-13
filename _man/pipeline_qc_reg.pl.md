---
section: 1
title: pipeline_qc_reg.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc_reg.pl

generate QC image for nonlinear registration quality

`pipeline_qc_reg.pl <nl_t1w> <candID> <visit> <age> <output>`

## DESCRIPTION

**pipeline_qc_reg.pl** generates a quality control image to assess the quality
of nonlinear registration. The script takes the nonlinearly registered
T1-weighted volume and produces a QC image that allows visual comparison of
the registered brain with the template anatomy.

The output image is annotated with candidate ID, visit label, and age. Poor
registration will be visible as anatomical misalignment with the expected
template appearance.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate a placeholder QC image without performing actual rendering.

`--clobber`
:   Overwrite the output file if it already exists.

## EXAMPLES

Generate a nonlinear registration QC image:

    pipeline_qc_reg.pl nl_t1_tal.mnc CAND001 V1 25 qc_nlreg.jpg

Generate with verbose output:

    pipeline_qc_reg.pl nl_t1_tal.mnc CAND001 V1 25 qc_nlreg.jpg --verbose

Generate a placeholder image for testing:

    pipeline_qc_reg.pl nl_t1_tal.mnc CAND001 V1 25 qc_nlreg.jpg --fake

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[minc_qc.pl](minc_qc.pl)
