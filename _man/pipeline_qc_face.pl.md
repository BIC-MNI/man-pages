---
section: 1
title: pipeline_qc_face.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_qc_face.pl

generate QC face renderings from three angles

`pipeline_qc_face.pl <native> <candID> <visit> <age> <output> [--stx <xfm>]`

## DESCRIPTION

**pipeline_qc_face.pl** generates quality control images showing face
renderings from three different viewing angles (typically front, left, and
right profiles). These images are used to verify the quality of defacing or
to inspect the facial surface reconstruction.

The script takes a native-space volume and produces a composite QC image. An
optional stereotaxic transform can be provided with **--stx** to align the
rendering to standard orientation. The output is annotated with candidate ID,
visit label, and age.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Generate placeholder QC images without performing actual rendering.

`--clobber`
:   Overwrite the output file if it already exists.

`--stx <xfm>`
:   Stereotaxic transformation file to align the volume to standard
    orientation before rendering.

## EXAMPLES

Generate face QC images:

    pipeline_qc_face.pl native_t1.mnc CAND001 V1 25 qc_face.jpg

Generate with a stereotaxic transform:

    pipeline_qc_face.pl native_t1.mnc CAND001 V1 25 qc_face.jpg \
      --stx tal.xfm

Generate placeholder images for testing:

    pipeline_qc_face.pl native_t1.mnc CAND001 V1 25 qc_face.jpg --fake

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[make_face.pl](make_face.pl)
