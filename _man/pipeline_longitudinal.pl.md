---
section: 1
title: pipeline_longitudinal.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_longitudinal.pl

longitudinal brain analysis pipeline

`pipeline_longitudinal.pl <candID> <visit1> [visit2] [visit3] [options]`

## DESCRIPTION

**pipeline_longitudinal.pl** runs the BIC longitudinal brain analysis pipeline,
which processes multiple time-point MRI scans from the same subject to track
brain changes over time. The pipeline registers all visits to a common
subject-specific template, performs tissue classification and segmentation at
each time point, and computes longitudinal measures such as atrophy rates.

The script takes a candidate identifier followed by one or more visit
identifiers. Subject ages and gender can be provided for demographic-aware
processing. The pipeline uses both linear and optionally nonlinear registration,
and can incorporate PCA-based normalization for improved longitudinal
consistency.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--prefix <dir>`
:   Base directory prefix for input and output files.

`--model_dir <dir>`
:   Path to the directory containing the reference model files.

`--model <name>`
:   Base name of the reference model to use for registration.

`--ages <age1,age2,...>`
:   Comma-separated list of ages corresponding to each visit, used for
    age-appropriate processing.

`--gender <M|F>`
:   Subject gender, used for gender-specific model selection when available.

`--nonlinear`
:   Enable nonlinear registration for more precise inter-visit alignment.

`--pca`
:   Enable PCA-based intensity normalization across time points for improved
    longitudinal consistency.

## EXAMPLES

Process two visits for a subject:

    pipeline_longitudinal.pl CAND001 V1 V2 \
      --model_dir /opt/minc/share/model --model icbm152

Process three visits with ages and nonlinear registration:

    pipeline_longitudinal.pl CAND001 V1 V2 V3 \
      --ages 65,66,67 --gender M --nonlinear \
      --model_dir /opt/minc/share/model --model icbm152

Process with PCA normalization:

    pipeline_longitudinal.pl CAND001 V1 V2 --pca --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_mritotal.pl](pipeline_mritotal.pl), [pipeline_nlr.pl](pipeline_nlr.pl)
