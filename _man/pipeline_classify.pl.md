---
section: 1
title: pipeline_classify.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_classify.pl

brain tissue classification using classify_clean

`pipeline_classify.pl <t1> [t2] [pd] <output> --model_dir <dir> --model_name <name> [options]`

## DESCRIPTION

**pipeline_classify.pl** performs brain tissue classification on MRI volumes
using the **classify_clean** tool. It classifies voxels into white matter (WM),
grey matter (GM), and cerebrospinal fluid (CSF) tissue classes based on T1-weighted
input, with optional T2-weighted and proton-density (PD) volumes for improved
accuracy.

The script requires a model directory and model name that specify the atlas
priors used during classification. An optional brain mask can restrict
classification to the brain region, and an optional linear transform can place
the input into stereotaxic space prior to classification. Markov Random Field
(MRF) regularization can be enabled for spatially smoother results.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--mask <file>`
:   Brain mask in stereotaxic space to restrict classification to brain tissue.

`--xfm <xfm>`
:   Linear transformation file mapping the input volume to stereotaxic space.

`--mrf`
:   Enable Markov Random Field regularization for spatially smoother
    classification results.

`--model_dir <dir>`
:   Path to the directory containing the atlas model files used for
    classification priors.

`--model_name <name>`
:   Base name of the atlas model files within the model directory.

## EXAMPLES

Classify brain tissue using T1 only:

    pipeline_classify.pl t1_tal.mnc classified.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

Classify with T1, T2, and PD inputs and a brain mask:

    pipeline_classify.pl t1_tal.mnc t2_tal.mnc pd_tal.mnc classified.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --mask brain_mask.mnc

Classify with MRF regularization:

    pipeline_classify.pl t1_tal.mnc classified.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --mrf --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[classify](classify), [pipeline_em_classify.pl](pipeline_em_classify.pl)
