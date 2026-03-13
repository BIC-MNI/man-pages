---
section: 1
title: hcag_segmentation_pipeline.pl
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# hcag_segmentation_pipeline.pl

run hippocampus and amygdala segmentation pipeline

`hcag_segmentation_pipeline.pl <input_t1.mnc> <output_prefix> --model-dir <dir>`

## DESCRIPTION

**hcag_segmentation_pipeline.pl** performs automatic segmentation of the
hippocampus and amygdala (and optionally other structures depending on the
atlas library) using the patch-based segmentation method described in
Coupe et al. (2010). The method compares patches from the input image
against a library of pre-labelled template images and assigns labels using
a non-local means weighting scheme.

The pipeline:

1. Registers the input T1-weighted volume to the model space.
2. Extracts regions of interest around the hippocampus and amygdala.
3. Runs patch-based label fusion using **itk_patch_morphology** to produce
   a segmentation.

A model directory containing pre-labelled template libraries must be provided
via the `--model-dir` option.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--qc`
:   Generate quality control images after segmentation.

`--clobber`
:   Overwrite existing output files.

`--model-dir <dir>`
:   Path to the directory containing pre-labelled atlas templates. This option
    is required.

`--subject <id>`
:   Subject identifier used for output file naming.

`--search <n>`
:   Search radius (in voxels) for patch matching. Default: 2.

`--patch <n>`
:   Half-size of the patch used for matching (in voxels). Default: 1.

`--exclude <id>`
:   Exclude the specified template from the library (e.g. for leave-one-out
    validation).

`--classes <n>`
:   Number of label classes in the segmentation. Default: 18.

`--variant <name>`
:   Name of the label variant to use from the model directory. Default: labels.

`--threshold <f>`
:   Confidence threshold for label assignment.

`--compare <labels.mnc>`
:   Compare segmentation output against the given ground-truth label volume
    and report overlap statistics.

## EXAMPLES

Segment the hippocampus and amygdala:

    hcag_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /opt/models/hcag_library

Segment with custom patch parameters and generate QC:

    hcag_segmentation_pipeline.pl --search 3 --patch 2 --qc \
        --clobber subject_t1.mnc seg_output --model-dir /opt/models/hcag_library

Leave-one-out validation:

    hcag_segmentation_pipeline.pl --exclude template_01 \
        --compare ground_truth.mnc \
        subject_t1.mnc validation_output --model-dir /opt/models/hcag_library

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**itk_patch_morphology**(1), **patch_segmentation_pipeline.pl**(1), **mincbeast**(1)
