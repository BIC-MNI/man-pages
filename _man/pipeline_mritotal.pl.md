---
section: 1
title: pipeline_mritotal.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_mritotal.pl

stereotaxic registration pipeline with BEaST brain masking

`pipeline_mritotal.pl <input.mnc> <output.xfm> <output.mnc> [options]`

## DESCRIPTION

**pipeline_mritotal.pl** performs stereotaxic registration of an MRI volume to
a standard template space (typically ICBM 152), combined with brain extraction
using the BEaST algorithm. The pipeline produces a linear transformation file
mapping the input to Talairach space and a resampled volume in stereotaxic
coordinates.

The script uses **bestlinreg_s2** for robust linear registration and
**mincbeast** for brain mask extraction. An initial transform can be provided
to seed the registration, and intensity correction can be applied. The
**--fallback** option enables a fallback registration strategy if the primary
registration fails. Nonlinear masking (**--nlmask**) can improve brain
extraction accuracy.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--fallback`
:   Enable a fallback registration strategy if the primary registration
    fails or produces poor results.

`--correct`
:   Apply intensity correction to the input volume before registration.

`--model_dir <dir>`
:   Path to the directory containing the reference model files.

`--model_name <name>`
:   Base name of the reference model to use for registration.

`--initial <xfm>`
:   An initial linear transform to seed the registration, useful when an
    approximate alignment is already known.

`--nlmask`
:   Use nonlinear registration to improve brain mask accuracy.

`--beastlib <dir>`
:   Path to the BEaST brain masking library directory.

## EXAMPLES

Register a volume to stereotaxic space:

    pipeline_mritotal.pl input.mnc output.xfm output_tal.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152

Register with intensity correction and BEaST library:

    pipeline_mritotal.pl input.mnc output.xfm output_tal.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --correct \
      --beastlib /opt/minc/share/beast-library-1.1

Register with an initial transform and fallback:

    pipeline_mritotal.pl input.mnc output.xfm output_tal.mnc \
      --model_dir /opt/minc/share/icbm152_model_09c \
      --model_name icbm_avg_152 --initial init.xfm --fallback

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[bestlinreg_s2](bestlinreg_s2), [mincbeast](mincbeast), [mritotal](mritotal)
