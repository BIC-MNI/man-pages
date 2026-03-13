---
section: 1
title: itk_patch_segmentation
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_patch_segmentation

perform patch-based label fusion segmentation

`itk_patch_segmentation <input> [output_labels] [options]`

## DESCRIPTION

**itk_patch_segmentation** performs patch-based regression segmentation using
ITK-based image I/O. It supports multiple label fusion strategies including
Support Vector Machine (SVM), Non-Negative Least Squares (NNLS), and exponential
weighting for combining multiple atlas segmentations into a consensus
segmentation of the input volume.

The tool compares local image patches between the input volume and a set of
training volumes (atlases with known labels) to determine the most likely label
for each voxel. The patch-based approach provides robust segmentation that is
less sensitive to registration errors than voxel-wise label fusion.

This is the ITK-based version with support for multiple MINC and NIfTI formats.
For the legacy MINC1-only implementation, see **volume_patches**.

## OPTIONS

`--train <file>`
:   Specify a training library file listing atlas volumes and their labels.

`--train2 <file>`
:   Specify a second training library for two-level segmentation.

`--nnls`
:   Use Non-Negative Least Squares for label fusion weighting.

`--svm`
:   Use Support Vector Machine for label fusion.

`--exp`
:   Use exponential weighting for label fusion.

`--verbose`
:   Print detailed progress information.

`--quiet`
:   Suppress all output messages.

`--clobber`
:   Overwrite existing output files.

`--mask <file>`
:   Specify a mask to restrict segmentation to a region of interest.

`--patch <n>`
:   Set the patch radius in voxels (default: 1).

`--search <n>`
:   Set the search radius in voxels for finding matching patches (default: 1).

`--cls <n>`
:   Number of classes for segmentation.

`--beta <value>`
:   Regularization parameter controlling smoothness (default: 0.125).

`--scaling`
:   Enable intensity scaling between input and training volumes.

`--threshold <value>`
:   Set a threshold for patch similarity.

`--discrete <n>`
:   Number of discrete labels (default: 2).

`--confidence`
:   Output a confidence map alongside the segmentation.

`--adist`
:   Use absolute distance weighting.

`--grading`
:   Perform grading instead of segmentation.

`--iter <n>`
:   Maximum number of iterations (default: 50).

`--extract`
:   Extract labels from training library.

`--top <n>`
:   Use only the top N most similar training samples.

`--float`
:   Store output as 32-bit floating point.

`--short`
:   Store output as 16-bit signed integer.

`--byte`
:   Store output as 8-bit unsigned integer.

`--box`
:   Use box-shaped patches.

`--ball`
:   Use ball-shaped patches.

`--prelabel <file>`
:   Specify a pre-labeling volume for initialization.

`--prob`
:   Output probability maps for each label.

`--groups <n>`
:   Number of groups for cross-validation.

## EXAMPLES

Segment using exponential weighting with a training library:

    itk_patch_segmentation input.mnc output_labels.mnc --train library.txt --exp --mask brain_mask.mnc

Segment using SVM with larger patch and search radii:

    itk_patch_segmentation input.mnc labels.mnc --train library.txt --svm --patch 2 --search 2

Segment with confidence output:

    itk_patch_segmentation input.mnc labels.mnc --train library.txt --exp --confidence --beta 0.25

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2012 by Vladimir S. Fonov

## SEE ALSO

[itk_patch_grading](itk_patch_grading) [itk_patch_morphology](itk_patch_morphology)
