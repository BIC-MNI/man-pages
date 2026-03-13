---
section: 1
title: pipeline_t2tot1.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_t2tot1.pl

register T2/PD to T1 in Talairach space

`pipeline_t2tot1.pl <xfm> <t1> <t2> <out_xfm> <out_t2> [options]`

## DESCRIPTION

**pipeline_t2tot1.pl** registers a T2-weighted (or proton-density) volume to
a T1-weighted volume in Talairach stereotaxic space. The script uses
intra-subject cross-modality registration to align the T2 volume to the T1,
producing a transformation file and a resampled T2 volume in Talairach space.

The input T1 Talairach transform is used to bring both volumes into
stereotaxic space. Intensity correction can be applied independently to the
T1 and T2 volumes using the **--correct_t1w** and **--correct_t2w** options.
A model directory and name must be specified for the registration reference.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--correct_t1w`
:   Apply intensity correction to the T1-weighted volume.

`--correct_t2w`
:   Apply intensity correction to the T2-weighted volume.

`--model_dir <dir>`
:   Path to the directory containing the reference model files.

`--model_name <name>`
:   Base name of the reference model.

## EXAMPLES

Register T2 to T1 in Talairach space:

    pipeline_t2tot1.pl tal.xfm t1_native.mnc t2_native.mnc \
      t2_to_t1.xfm t2_tal.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

Register with intensity correction on both modalities:

    pipeline_t2tot1.pl tal.xfm t1_native.mnc t2_native.mnc \
      t2_to_t1.xfm t2_tal.mnc --correct_t1w --correct_t2w \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[mritoself](mritoself), [pipeline_mritotal.pl](pipeline_mritotal.pl)
