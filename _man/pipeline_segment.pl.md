---
section: 1
title: pipeline_segment.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_segment.pl

lobe segmentation using atlas templates

`pipeline_segment.pl <classified> <lin_xfm> <nl_xfm> <output_lobes> [options]`

## DESCRIPTION

**pipeline_segment.pl** performs brain lobe segmentation by propagating atlas
labels through linear and nonlinear transformations to the subject space. The
script takes a tissue classification volume and both linear and nonlinear
transforms mapping the subject to the atlas, then produces a lobe segmentation
volume where each voxel is labelled with its anatomical lobe (frontal,
temporal, parietal, occipital, etc.).

The segmentation is constrained by the tissue classification so that only
brain voxels receive lobe labels. A custom template can be specified with the
**--template** option to use alternative atlas definitions.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--model-dir <dir>`
:   Path to the directory containing the atlas model and template files.

`--template <file>`
:   Atlas lobe template file to use for segmentation. If not specified,
    the default template from the model directory is used.

## EXAMPLES

Segment brain lobes with default template:

    pipeline_segment.pl classified.mnc tal.xfm nl.xfm lobes.mnc \
      --model-dir /opt/minc/share/icbm152_model_09c

Segment with a custom template:

    pipeline_segment.pl classified.mnc tal.xfm nl.xfm lobes.mnc \
      --model-dir /opt/minc/share/icbm152_model_09c \
      --template custom_lobes.mnc

Segment with verbose output and clobber:

    pipeline_segment.pl classified.mnc tal.xfm nl.xfm lobes.mnc \
      --model-dir /opt/minc/share/icbm152_model_09c --verbose --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[lobe_segment.pl](lobe_segment.pl)
