---
section: 1
title: pipeline_volumes_nl.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_volumes_nl.pl

compute brain and lobe volumes from nonlinear registration

`pipeline_volumes_nl.pl <mask> <cls> <lobes> <xfm> <output.txt> [options]`

## DESCRIPTION

**pipeline_volumes_nl.pl** computes brain tissue volumes on a per-lobe basis
using nonlinear registration results. In addition to the global tissue volumes
computed by **pipeline_volumes_lin.pl**, this script uses the lobe segmentation
to break down volumes by anatomical region (frontal, temporal, parietal,
occipital lobes, etc.).

The script takes a brain mask, tissue classification, lobe segmentation
volume, and the nonlinear transform, and produces a text file with detailed
volumetric measurements. Volumes are corrected using the Jacobian determinant
of the nonlinear transform to report values in native-space cubic millimetres.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--age <n>`
:   Subject age in years, included as metadata in the output file.

`--gender <M|F>`
:   Subject gender, included as metadata in the output file.

`--scanner <name>`
:   Scanner model or identifier, included as metadata in the output file.

`--scanner_id <id>`
:   Scanner serial number or unique identifier, included as metadata in the
    output file.

`--t1 <file>`
:   Path to the T1-weighted input volume, recorded in the output file.

`--t2 <file>`
:   Path to the T2-weighted input volume, recorded in the output file.

`--pd <file>`
:   Path to the proton-density input volume, recorded in the output file.

## EXAMPLES

Compute lobe-based tissue volumes:

    pipeline_volumes_nl.pl brain_mask.mnc classified.mnc lobes.mnc \
      nl.xfm volumes_nl.txt

Compute volumes with demographic metadata:

    pipeline_volumes_nl.pl brain_mask.mnc classified.mnc lobes.mnc \
      nl.xfm volumes_nl.txt --age 65 --gender F \
      --scanner GE_Discovery --scanner_id G001

Compute volumes with input file references and clobber:

    pipeline_volumes_nl.pl brain_mask.mnc classified.mnc lobes.mnc \
      nl.xfm volumes_nl.txt \
      --t1 t1_native.mnc --t2 t2_native.mnc --pd pd_native.mnc --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_volumes_lin.pl](pipeline_volumes_lin.pl), [lobes_to_volumes.pl](lobes_to_volumes.pl)
