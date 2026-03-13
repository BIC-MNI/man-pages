---
section: 1
title: volume_patches
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# volume_patches

legacy non-local patch-based segmentation using MINC1 I/O

`volume_patches <input> [output_labels] [options]`

## DESCRIPTION

**volume_patches** performs non-local patch-based segmentation using MINC1 I/O.
It compares local image patches between the input volume and a set of training
volumes (atlases with known labels) to determine the most likely label for each
voxel.

The tool uses a non-local means approach where each voxel's label is determined
by a weighted vote from similar patches found in the training library. Patch
similarity is computed within a search neighbourhood, and the weights are
derived from the patch distance using an exponential kernel controlled by the
beta parameter.

This is the legacy MINC1 implementation. For the more capable ITK-based version
that supports additional label fusion methods and file formats, see
**itk_patch_segmentation**.

## OPTIONS

`--train <file>`
:   Specify a training library file listing atlas volumes and their labels.

`--train2 <file>`
:   Specify a second training library for two-level segmentation.

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

`--dist`
:   Output the distance map instead of labels.

`--cls <n>`
:   Number of classes for segmentation.

`--beta <value>`
:   Regularization parameter controlling the exponential weighting kernel
    (default: 1.0).

`--scaling`
:   Enable intensity scaling between input and training volumes.

## EXAMPLES

Segment using a training library:

    volume_patches input.mnc output_labels.mnc --train library.txt --mask brain_mask.mnc

Segment with larger patch and search radii:

    volume_patches input.mnc labels.mnc --train library.txt --patch 2 --search 2

Segment with custom beta and verbose output:

    volume_patches input.mnc labels.mnc --train library.txt --beta 0.5 --verbose

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2012 by Vladimir S. Fonov

## SEE ALSO

[itk_patch_morphology](itk_patch_morphology) [itk_patch_segmentation](itk_patch_segmentation)
