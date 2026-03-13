---
section: 1
title: pipeline_face.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_face.pl

FACE anatomical feature extraction pipeline

`pipeline_face.pl <t1_tal> <mask_tal> <cls_tal> <labels_tal> <xfm_tal> <nlxfm_tal> <output>`

## DESCRIPTION

**pipeline_face.pl** extracts anatomical features using the FACE (Feature
Anatomical Classification and Extraction) method. It takes a T1-weighted
volume in Talairach space along with a brain mask, tissue classification,
lobe labels, and both linear and nonlinear transforms, and produces a set of
anatomical feature measurements.

The output contains quantitative measurements of various brain structures
derived from the combination of classification, segmentation, and registration
results.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Extract FACE features from a fully processed subject:

    pipeline_face.pl t1_tal.mnc mask_tal.mnc cls_tal.mnc \
      labels_tal.mnc tal.xfm nl.xfm face_output

Run with verbose output:

    pipeline_face.pl t1_tal.mnc mask_tal.mnc cls_tal.mnc \
      labels_tal.mnc tal.xfm nl.xfm face_output --verbose

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[make_face.pl](make_face.pl), [pipeline_qc_face.pl](pipeline_qc_face.pl)
