---
section: 1
title: ventricles_segmentation_pipeline.pl
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# ventricles_segmentation_pipeline.pl

ventricle segmentation pipeline using patch-based methods

`ventricles_segmentation_pipeline.pl <input_t1.mnc> <output_prefix> --model-dir <dir> [options]`

## DESCRIPTION

**ventricles_segmentation_pipeline.pl** runs a patch-based segmentation pipeline
specifically designed for segmenting the lateral ventricles from T1-weighted MRI
volumes. The pipeline registers the input volume to an atlas library and uses
non-local patch-based label fusion to produce a binary ventricle mask.

The model directory containing the atlas library must be specified.
Preprocessing steps such as non-uniformity correction (N3) and NUYL intensity
normalization can be enabled. A nonlinear brain mask constraint and manual
initial transformations can be supplied for difficult cases.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--qc`
:   Generate quality control images.

`--clobber`
:   Overwrite existing output files.

`--model-dir <dir>`
:   Path to the model directory containing the ventricle atlas library. This
    option is required.

`--nuc`
:   Apply N3 non-uniformity correction during preprocessing.

`--cleanup`
:   Remove temporary files after processing.

`--nuyl`
:   Apply NUYL intensity normalization during preprocessing.

`--whole-head`
:   Use the whole head (not just the brain) for registration and segmentation.

`--subject <id>`
:   Specify a subject identifier string for output naming.

`--nlmask <mask.mnc>`
:   Provide a nonlinear brain mask to constrain the segmentation region.

`--manual-xfm <xfm>`
:   Provide a manually created initial transformation for registration.

`--search <n>`
:   Search radius in voxels for the patch-based label fusion. Default: 1.

`--reference <file>`
:   Specify a reference volume for comparison or validation.

`--nonbrainconstraint`
:   Apply a constraint that prevents labels from being assigned outside the
    brain region.

## EXAMPLES

Segment ventricles with the required model directory:

    ventricles_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/ventricle_model --verbose

Segment with preprocessing and quality control output:

    ventricles_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/ventricle_model --nuc --nuyl --qc --cleanup

Segment with a manual initial transform and non-brain constraint:

    ventricles_segmentation_pipeline.pl subject_t1.mnc output_prefix \
        --model-dir /path/to/ventricle_model \
        --manual-xfm initial.xfm --nonbrainconstraint --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**itk_patch_morphology**(1), **hcag_segmentation_pipeline.pl**(1)
