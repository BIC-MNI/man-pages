---
section: 1
title: pipeline_tal_mask.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_tal_mask.pl

apply brain mask to T1/T2/PD volumes in Talairach space

`pipeline_tal_mask.pl <mask> <t1> <t2> <pd> <t1_out> <t2_out> <pd_out>`

## DESCRIPTION

**pipeline_tal_mask.pl** applies a brain mask to T1-weighted, T2-weighted,
and proton-density volumes in Talairach stereotaxic space. Voxels outside the
brain mask are set to zero, producing masked versions of each input volume.

This masking step is typically performed after stereotaxic registration and
before tissue classification, to ensure that only brain tissue is included in
subsequent processing steps. All three modalities are masked consistently
using the same brain mask.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Apply a brain mask to all three modalities:

    pipeline_tal_mask.pl brain_mask.mnc t1_tal.mnc t2_tal.mnc pd_tal.mnc \
      t1_masked.mnc t2_masked.mnc pd_masked.mnc

Apply with verbose output:

    pipeline_tal_mask.pl brain_mask.mnc t1_tal.mnc t2_tal.mnc pd_tal.mnc \
      t1_masked.mnc t2_masked.mnc pd_masked.mnc --verbose

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[mincmask](mincmask)
