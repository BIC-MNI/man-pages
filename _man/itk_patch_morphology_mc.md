---
section: 1
title: itk_patch_morphology_mc
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_patch_morphology_mc

Multi-channel patch-based segmentation.

`itk_patch_morphology_mc <input1> [input2] ... [inputN] [options]`

## DESCRIPTION

**itk_patch_morphology_mc** performs multi-channel patch-based segmentation,
extending the single-channel `itk_patch_morphology` method to use multiple
input contrasts simultaneously. Each input channel provides complementary
information (e.g., T1, T2, PD), and patches are compared across all channels
jointly to improve segmentation accuracy.

Channel contributions can be controlled using the `--weights` option to
assign relative importance to each input. The tool uses the same non-local
means framework as `itk_patch_morphology`, with exponential weighting of
patch similarity across all channels.

## OPTIONS

`--train` *data*
:   Training library specification file containing multi-channel image paths
    and labels.

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

`--output` *labels*
:   Write the output label volume to the specified file.

`--weights` *w1,w2,...*
:   Comma-separated weights for each input channel.

`--groups` *n*
:   Number of training groups.

`--threshold` *d*
:   Threshold for minimum patch similarity.

## EXAMPLES

    # Multi-channel segmentation with T1 and T2
    itk_patch_morphology_mc t1.mnc t2.mnc --train library.csv \
        --output labels.mnc --mask brain_mask.mnc

    # With custom channel weights
    itk_patch_morphology_mc t1.mnc t2.mnc pd.mnc --train library.csv \
        --output labels.mnc --weights 1.0,0.5,0.3

    # Output probability maps
    itk_patch_morphology_mc t1.mnc t2.mnc --train library.csv \
        --output labels.mnc --prob prob_ --float

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_patch_morphology](itk_patch_morphology) ,
[itk_patch_segmentation](itk_patch_segmentation)
