---
section: 1
title: patch_segmentation_pipeline.pl
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# patch_segmentation_pipeline.pl

RASCAL patch-based label fusion segmentation pipeline

`patch_segmentation_pipeline.pl <input_t1.mnc> <output_prefix> --model-dir <dir> [options]`

## DESCRIPTION

**patch_segmentation_pipeline.pl** runs the RASCAL (Rapid Automatic Segmentation
of the human Cerebral cortex using an Atlas Library) patch-based label fusion
segmentation pipeline as described by Weier et al. (2014). The pipeline
registers an input T1-weighted MRI volume to a set of pre-labelled atlas
templates, then uses non-local patch-based label fusion to propagate anatomical
labels from the atlas library to the subject.

The pipeline supports multiple registration backends including **minctracc** and
**ANTs**. Preprocessing steps such as non-uniformity correction (N3/N4) and
intensity normalization (NUYL) can be enabled. Graph-cut optimization (GCO) can
be applied for spatial regularization of the segmentation. The model directory,
which contains the atlas library, must be specified.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--qc`
:   Generate quality control images.

`--clobber`
:   Overwrite existing output files.

`--cleanup`
:   Remove temporary files after processing.

`--model-dir <dir>`
:   Path to the model directory containing the atlas library. This option is
    required.

`--subject <id>`
:   Specify a subject identifier string for output naming.

`--search <n>`
:   Search radius in voxels for the patch-based label fusion. Default: 2.

`--patch <n>`
:   Patch radius in voxels for the patch-based label fusion. Default: 1.

`--exclude <id>`
:   Exclude a specific atlas subject from the library (e.g. for leave-one-out
    validation).

`--classes <n>`
:   Number of label classes in the atlas library. Default: 36.

`--variant <name>`
:   Name of the label variant to use from the model directory. Default: labels.

`--threshold <f>`
:   Confidence threshold for label assignment.

`--compare <file>`
:   Provide a manual segmentation for comparison and overlap statistics.

`--short`
:   Store output labels in short integer format.

`--preprocess`
:   Run preprocessing steps (intensity normalization, brain masking) before
    segmentation.

`--minctracc`
:   Use **minctracc** for nonlinear registration to the atlas templates.

`--ants`
:   Use **ANTs** for nonlinear registration to the atlas templates.

`--build`
:   Build the atlas library from the model directory.

`--symmetric`
:   Use symmetric registration.

`--resample_labels_order <n>`
:   Interpolation order for resampling label volumes. Default: 1.

`--preselect`
:   Preselect atlas subjects most similar to the input before label fusion.

`--pairwise`
:   Use pairwise label fusion strategy.

`--refine`
:   Refine the segmentation with additional iterations.

`--qc_lut <file>`
:   Specify a colour lookup table for quality control visualisation.

`--nuc`
:   Apply N3 non-uniformity correction during preprocessing.

`--nuc3T`
:   Apply non-uniformity correction optimised for 3T MRI scanners.

`--no_nuyl`
:   Disable NUYL intensity normalization.

`--no_gco`
:   Disable graph-cut optimization for label regularization.

`--no_nl`
:   Disable nonlinear registration.

`--baa`
:   Use BEaST-based brain mask for the analysis.

`--list <file>`
:   Specify the atlas sample list file within the model directory. Default:
    samples.lst.

`--nomask`
:   Do not apply a brain mask during processing.

`--patch_normalize`
:   Normalize patch intensities before comparison.

## EXAMPLES

Run segmentation with the required model directory:

    patch_segmentation_pipeline.pl subject_t1.mnc output_prefix --model-dir /path/to/atlas

Run with ANTs registration, QC output, and cleanup:

    patch_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/atlas --ants --qc --cleanup --verbose

Run with custom patch parameters and compare to manual labels:

    patch_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/atlas --search 3 --patch 2 \
        --compare manual_labels.mnc --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**itk_patch_morphology**(1), **hcag_segmentation_pipeline.pl**(1)
