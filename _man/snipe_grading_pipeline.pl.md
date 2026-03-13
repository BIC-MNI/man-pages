---
section: 1
title: snipe_grading_pipeline.pl
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# snipe_grading_pipeline.pl

SNIPE grading pipeline for Alzheimer's disease classification

`snipe_grading_pipeline.pl <input_t1.mnc> <output_prefix> --model-dir <dir> [options]`

## DESCRIPTION

**snipe_grading_pipeline.pl** runs the SNIPE (Scoring by Non-local Image Patch
Estimation) grading pipeline for hippocampal analysis and Alzheimer's disease
classification, as described by Coupé et al. (2012). The pipeline registers the
input T1-weighted MRI volume to a set of atlas templates and computes a grading
score based on non-local patch comparison against libraries of Alzheimer's
disease (AD) patients and normal controls (NC).

The grading score reflects the degree to which the hippocampal region resembles
AD or NC patterns. The model directory containing the atlas templates and
subject libraries must be specified. Preprocessing steps such as non-uniformity
correction can be enabled.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--nuc`
:   Apply N3 non-uniformity correction during preprocessing.

`--model-dir <dir>`
:   Path to the model directory containing the atlas templates and grading
    libraries. This option is required.

`--subject <id>`
:   Specify a subject identifier string for output naming.

`--3t`
:   Use parameters optimized for 3T MRI scanners.

`--exclude <id>`
:   Exclude a specific atlas subject from the library (e.g. for leave-one-out
    validation).

`--select <n>`
:   Number of most similar templates to select from the library for grading.
    Default: 50.

`--preprocess`
:   Run preprocessing steps (intensity normalization, brain masking) before
    grading.

`--ad_lib <file>`
:   Specify a custom Alzheimer's disease subject library file.

`--nc_lib <file>`
:   Specify a custom normal control subject library file.

`--variant <name>`
:   Name of the grading variant to use from the model directory.

`--manual`
:   Use manual segmentations from the atlas library instead of automatic ones.

`--use_mmse`
:   Incorporate MMSE (Mini-Mental State Examination) scores into the grading
    model.

## EXAMPLES

Run SNIPE grading with the required model directory:

    snipe_grading_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/snipe_model --verbose

Run with 3T-optimized parameters and preprocessing:

    snipe_grading_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/snipe_model --3t --preprocess --nuc

Run with custom libraries and leave-one-out validation:

    snipe_grading_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/snipe_model \
        --ad_lib custom_ad.lst --nc_lib custom_nc.lst \
        --exclude subject_01 --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**itk_patch_grading**(1), **hcag_segmentation_pipeline.pl**(1)
