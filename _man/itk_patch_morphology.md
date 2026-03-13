---
section: 1
title: itk_patch_morphology
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_patch_morphology

Patch-based segmentation using expert priors (Coupe et al. 2010).

`itk_patch_morphology <input> [output_labels] [options]`

## DESCRIPTION

**itk_patch_morphology** performs patch-based label fusion for anatomical
segmentation using a library of pre-segmented template images. The method
is based on the non-local means framework described by Coupe et al. (2010),
where each voxel in the input image is labelled by comparing its local patch
to patches from the training library and performing a weighted vote.

The similarity between patches is measured using a sum of squared differences,
and the contribution of each training patch is weighted by an exponential
function of the distance. This approach can achieve highly accurate
segmentation when a sufficiently large and representative training library
is available.

## OPTIONS

`--train` *data*
:   Training library specification file containing image paths and labels.

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
:   Use pre-existing labels to guide the segmentation.

`--prob` *prefix*
:   Write per-class probability maps with the given filename prefix.

`--groups` *n*
:   Number of training groups.

## EXAMPLES

    # Patch-based segmentation with a training library
    itk_patch_morphology input.mnc output_labels.mnc --train library.csv \
        --mask brain_mask.mnc

    # Segmentation with larger patch and search radius
    itk_patch_morphology input.mnc output_labels.mnc --train library.csv \
        --mask brain_mask.mnc --patch 2 --search 2

    # Output probability maps for each class
    itk_patch_morphology input.mnc output_labels.mnc --train library.csv \
        --prob prob_ --float

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_patch_grading](itk_patch_grading) ,
[itk_patch_segmentation](itk_patch_segmentation) ,
[itk_patch_morphology_mc](itk_patch_morphology_mc)
