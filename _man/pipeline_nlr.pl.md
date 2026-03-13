---
section: 1
title: pipeline_nlr.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_nlr.pl

nonlinear registration pipeline

`pipeline_nlr.pl <t1_tal> <mask> <out_grid> <out_xfm> <out_t1> [options]`

## DESCRIPTION

**pipeline_nlr.pl** performs hierarchical nonlinear registration of a
T1-weighted volume in Talairach space to a standard template model. The
pipeline uses **nlfit_s** or **minctracc** to compute a nonlinear deformation
field that warps the subject anatomy to match the template as closely as
possible.

The output consists of a deformation grid file, a combined nonlinear
transformation file, and the nonlinearly resampled T1 volume. The **--level**
option controls the resolution of the finest registration step, with lower
values producing finer deformation fields at the cost of longer computation
time.

A brain mask is required to restrict the registration to the brain region,
preventing extracranial structures from influencing the result.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--model_dir <dir>`
:   Path to the directory containing the reference model files.

`--model_name <name>`
:   Base name of the reference model to use for nonlinear registration.

`--level <n>`
:   Finest resolution level for the hierarchical nonlinear registration.
    Lower values produce finer deformation fields. Default is 2.

## EXAMPLES

Run nonlinear registration with default settings:

    pipeline_nlr.pl t1_tal.mnc brain_mask.mnc nl_grid.mnc nl.xfm nl_t1.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

Run with finer registration level:

    pipeline_nlr.pl t1_tal.mnc brain_mask.mnc nl_grid.mnc nl.xfm nl_t1.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --level 1

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[nlfit_s](nlfit_s), [minctracc](minctracc)
