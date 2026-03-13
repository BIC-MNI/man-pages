---
section: 1
title: pipeline_deface.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_deface.pl

defacing pipeline for anonymizing MRI data

`pipeline_deface.pl <T1w> [T2w] [PDw] <oT1w> [oT2w] [oPDw] [options]`

## DESCRIPTION

**pipeline_deface.pl** is a wrapper script for the BIC defacing pipeline that
removes identifying facial features from MRI volumes to protect subject
privacy. It supports T1-weighted, T2-weighted, and proton-density (PD)
volumes, and can process them simultaneously to ensure consistent defacing
across modalities.

The pipeline performs linear and optionally nonlinear registration to a
reference model, identifies the facial region, and replaces it with either
zeroed voxels or a random distortion grid. Intensity normalization can be
disabled with **--no-int-norm**, and a visible watermark can be applied to the
defaced output. The BEaST brain masking library can be specified for improved
brain extraction.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--dual-echo`
:   Indicate that the T2 and PD inputs are from a dual-echo acquisition.

`--model-dir <dir>`
:   Path to the directory containing the reference model files.

`--model <name>`
:   Base name of the reference model to use for registration.

`--nonlinear`
:   Use nonlinear registration for more accurate facial region identification.

`--no-int-norm`
:   Disable intensity normalization of the input volumes.

`--watermark`
:   Apply a visible watermark to the defaced output volumes.

`--t1w-xfm <xfm>`
:   Pre-computed linear transform for the T1-weighted volume to stereotaxic
    space.

`--t2w-xfm <xfm>`
:   Pre-computed linear transform for the T2-weighted volume to stereotaxic
    space.

`--pdw-xfm <xfm>`
:   Pre-computed linear transform for the PD-weighted volume to stereotaxic
    space.

`--brain-mask <file>`
:   Pre-computed brain mask to use instead of generating one.

`--keep-tmp`
:   Do not delete temporary files after processing.

`--keep-real-range`
:   Preserve the original real value range in the output MINC files.

`--output <dir>`
:   Directory where output files will be written.

`--beastlib <dir>`
:   Path to the BEaST brain masking library directory.

`--3t`
:   Indicate that the data was acquired on a 3 Tesla scanner, adjusting
    processing parameters accordingly.

## EXAMPLES

Deface a T1-weighted volume:

    pipeline_deface.pl input_t1.mnc defaced_t1.mnc

Deface T1 and T2 volumes with nonlinear registration:

    pipeline_deface.pl input_t1.mnc input_t2.mnc \
      defaced_t1.mnc defaced_t2.mnc --nonlinear

Deface with watermark and custom model:

    pipeline_deface.pl input_t1.mnc defaced_t1.mnc \
      --model-dir /opt/minc/share/model --model icbm152 \
      --watermark --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[deface_minipipe.pl](deface_minipipe.pl)
