---
section: 1
title: classify
author: Jason Lerch
group: Classification
---
# classify

classify voxels in MRI volumes into tissue classes

`classify [options] <input_volumes> <output.mnc>`

## DESCRIPTION

**classify** classifies voxels in one or more MINC input volumes into tissue
classes using a variety of supervised and unsupervised classification
algorithms. Supported classifiers include minimum distance, K-nearest
neighbours (KNN), artificial neural network (ANN), hard C-means (HCM), fuzzy
C-means (FCM), and Bayesian classification. Training data can be provided via
tag files. Fuzzy classification outputs can be written as separate volumes for
each tissue class.

## OPTIONS

`-verbose`
:   Print progress information.

`-debug`
:   Print debugging information.

`-clobber`
:   Overwrite an existing output file.

`-byte`
:   Store output with 8-bit integer voxels.

`-short`
:   Store output with 16-bit integer voxels.

`-long`
:   Store output with 32-bit integer voxels.

`-float`
:   Store output with 32-bit floating point voxels.

`-double`
:   Store output with 64-bit floating point voxels.

`-signed`
:   Store output with signed integer voxels.

`-unsigned`
:   Store output with unsigned integer voxels.

`-output_range`
:   Specify the output intensity range.

`-tagfile`
:   Specify a tag file containing training samples.

`-volume`
:   Specify the volume index for training.

`-class_names`
:   Specify class names for the classifier.

`-load_train`
:   Load a previously saved training set.

`-save_train`
:   Save the training set for later use.

`-train_only`
:   Only perform training; do not classify.

`-parameter`
:   Specify classifier parameters.

`-apriori`
:   Specify a priori probability volumes for each class.

`-fuzzy`
:   Enable fuzzy classification output.

`-fprefix`
:   Set the prefix for fuzzy output filenames.

`-fpath`
:   Set the path for fuzzy output files.

`-fuzzy_voxel_min`
:   Set the minimum fuzzy membership for a voxel.

`-fuzzy_voxel_max`
:   Set the maximum fuzzy membership for a voxel.

`-fuzzy_image_min`
:   Set the minimum fuzzy membership for an image.

`-fuzzy_image_max`
:   Set the maximum fuzzy membership for an image.

`-fbyte`
:   Store fuzzy output with 8-bit integer voxels.

`-fshort`
:   Store fuzzy output with 16-bit integer voxels.

`-flong`
:   Store fuzzy output with 32-bit integer voxels.

`-ffloat`
:   Store fuzzy output with 32-bit floating point voxels.

`-fdouble`
:   Store fuzzy output with 64-bit floating point voxels.

`-mask`
:   Specify a mask volume for restricting classification.

`-user_mask_value`
:   Set the mask value for voxel inclusion.

`-user_mask_class`
:   Set the mask class for voxel inclusion.

`-nocache`
:   Do not use volume caching.

`-max_cache_size`
:   Set the maximum cache size in bytes.

`-block_sizes`
:   Set the block sizes for caching.

`-min`
:   Use the minimum distance classifier.

`-knn`
:   Use the K-nearest neighbours classifier.

`-ann`
:   Use the artificial neural network classifier.

`-hcm`
:   Use the hard C-means classifier.

`-fcm`
:   Use the fuzzy C-means classifier.

`-bayes`
:   Use the Bayesian classifier.

## EXAMPLES

    classify -tagfile training.tag t1.mnc classified.mnc

    classify -knn -tagfile training.tag -mask brain_mask.mnc t1.mnc t2.mnc pd.mnc classified.mnc

    classify -fcm -fuzzy -fprefix fuzzy_ t1.mnc classified.mnc

## AUTHOR

Jason Lerch - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2002 by Jason Lerch

## SEE ALSO

[nu_correct](nu_correct), [inormalize](inormalize), [mincmath](mincmath), [volume_stats](volume_stats)
