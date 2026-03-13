---
section: 1
title: sharpness_estimate
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# sharpness_estimate

Estimate image sharpness based on median gradient magnitude.

`sharpness_estimate [options] <input>`

## DESCRIPTION

**sharpness_estimate** estimates the sharpness of a MINC volume by computing
the median gradient magnitude across the image. Higher values indicate
sharper images with well-defined edges, while lower values indicate blurry
images. This metric is useful for quality control of MRI acquisitions and
for evaluating the effects of denoising or blurring operations.

## OPTIONS

`--mask` *mask*
:   Restrict the sharpness computation to voxels within the specified binary
    mask.

## EXAMPLES

Estimate sharpness of a T1 volume:

    sharpness_estimate t1.mnc

Estimate sharpness within a brain mask:

    sharpness_estimate --mask brainmask.mnc t1.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[noise_estimate](noise_estimate), [fast_blur](fast_blur)
