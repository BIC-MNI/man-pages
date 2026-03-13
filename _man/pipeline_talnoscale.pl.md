---
section: 1
title: pipeline_talnoscale.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_talnoscale.pl

remove scaling from Talairach transform and resample

`pipeline_talnoscale.pl <input.mnc> <input.xfm> <output.xfm> <output.mnc> [options]`

## DESCRIPTION

**pipeline_talnoscale.pl** creates a Talairach-like transform with the scaling
component removed. The standard Talairach transform includes a scaling factor
that normalizes brain size, but for certain analyses (such as volumetric
measurements in native space or deformation-based morphometry) it is
desirable to have a rigid-body alignment without the scaling.

The script decomposes the input Talairach transform, removes the scale
parameters, recomposes the transform, and resamples the input volume using
the no-scale transform. This produces a volume aligned to Talairach
orientation but preserving the original brain size.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--model_dir <dir>`
:   Path to the directory containing the reference model files used to
    define the output sampling grid.

`--model_name <name>`
:   Base name of the reference model.

## EXAMPLES

Remove scaling from a Talairach transform:

    pipeline_talnoscale.pl input.mnc tal.xfm noscale.xfm noscale.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

Remove scaling with clobber:

    pipeline_talnoscale.pl input.mnc tal.xfm noscale.xfm noscale.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[xfmdecomp](xfmdecomp), [pipeline_mritotal.pl](pipeline_mritotal.pl)
