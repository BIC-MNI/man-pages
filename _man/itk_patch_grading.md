---
section: 1
title: itk_patch_grading
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_patch_grading

Patch-based non-local grading using SVM, NNLS, or exponential weighting.

`itk_patch_grading <input> [output_labels] [options]`

## DESCRIPTION

**itk_patch_grading** performs patch-based grading of a MINC volume using a
library of pre-segmented training images. The grading score at each voxel
reflects how similar the local patch is to patches from training subjects in
different diagnostic groups (e.g., healthy controls vs. patients).

Three weighting schemes are available: exponential (default), non-negative
least squares (NNLS), and support vector machine (SVM). The method is based
on the non-local means framework, where patches from the input image are
compared to patches from the training library and weighted by similarity.

This tool is commonly used for patch-based morphological grading in
neurodegeneration studies.

## OPTIONS

`--train` *data*
:   Training library specification file containing image paths and labels.

`--train2`
:   Use a secondary training library format.

`--nnls`
:   Use non-negative least squares (NNLS) weighting.

`--svm`
:   Use support vector machine (SVM) weighting.

`--exp`
:   Use exponential weighting (default).

`--verbose`
:   Print progress information during processing.

`--quiet`
:   Suppress all output messages.

`--clobber`
:   Overwrite the output file if it already exists.

`--mask` *file*
:   Restrict processing to voxels within the specified mask.

`--patch` *n*
:   Patch radius in voxels (default: 1).

`--search` *n*
:   Search radius in voxels (default: 1).

`--cls` *output*
:   Write the discrete classification output to the specified file.

`--beta` *f*
:   Smoothing parameter for exponential weighting (default: 0.125).

`--scaling` *f*
:   Apply intensity scaling factor to patches before comparison.

`--threshold` *d*
:   Threshold for minimum patch similarity.

`--discrete` *n*
:   Number of discrete classes (default: 2).

`--confidence`
:   Output confidence (weight) maps.

`--adist`
:   Output average distance maps.

`--grading`
:   Output grading score maps.

`--iter` *n*
:   Number of iterations for iterative refinement (default: 50).

`--extract` *n*
:   Extract features from the specified label.

`--top` *n*
:   Use only the top *n* most similar training patches.

`--float`
:   Store output voxels as single-precision floating point.

`--short`
:   Store output voxels as short integer.

`--byte`
:   Store output voxels as unsigned byte.

`--box`
:   Use a box-shaped (cubic) search neighbourhood.

`--ball`
:   Use a ball-shaped (spherical) search neighbourhood.

`--prelabel`
:   Use pre-existing labels to guide the grading.

`--prob` *prefix*
:   Write per-class probability maps with the given filename prefix.

`--groups` *n*
:   Number of training groups.

## EXAMPLES

    # Patch-based grading with exponential weighting
    itk_patch_grading input.mnc grading.mnc --train library.csv \
        --mask brain_mask.mnc

    # Grading with SVM weighting
    itk_patch_grading input.mnc grading.mnc --train library.csv \
        --svm --mask brain_mask.mnc --patch 2 --search 2

    # Output classification and probability maps
    itk_patch_grading input.mnc --train library.csv \
        --cls classification.mnc --prob prob_ --float

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_patch_morphology](itk_patch_morphology) ,
[itk_patch_segmentation](itk_patch_segmentation)
