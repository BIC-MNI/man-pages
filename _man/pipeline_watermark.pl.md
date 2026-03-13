---
section: 1
title: pipeline_watermark.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_watermark.pl

apply a visible watermark to an MRI volume

`pipeline_watermark.pl <input.mnc> <output.mnc> --model_dir <dir> [--no_int_norm]`

## DESCRIPTION

**pipeline_watermark.pl** applies a visible watermark pattern to an MRI
volume. This is typically used as part of the defacing pipeline to indicate
that a volume has been processed for anonymization. The watermark is embedded
directly into the image data, making it visible when the volume is displayed.

The watermark pattern is loaded from a template in the model directory. By
default, the input volume is intensity normalized before the watermark is
applied; this can be disabled with the **--no_int_norm** option.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--model_dir <dir>`
:   Path to the directory containing the watermark template and model files.

`--no_int_norm`
:   Disable intensity normalization of the input volume before applying
    the watermark.

## EXAMPLES

Apply a watermark to a volume:

    pipeline_watermark.pl input.mnc watermarked.mnc \
      --model_dir /opt/minc/share/model

Apply a watermark without intensity normalization:

    pipeline_watermark.pl input.mnc watermarked.mnc \
      --model_dir /opt/minc/share/model --no_int_norm

Apply with verbose output and clobber:

    pipeline_watermark.pl input.mnc watermarked.mnc \
      --model_dir /opt/minc/share/model --verbose --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[deface_minipipe.pl](deface_minipipe.pl)
