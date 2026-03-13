---
section: 1
title: preprocess_segmentation
author: David MacDonald
group: Volume Operations
---
# preprocess_segmentation

preprocess a classified volume for cortical segmentation

`preprocess_segmentation input.mnc output.mnc`

## DESCRIPTION

**preprocess_segmentation** preprocesses a classified MINC volume to prepare
it for cortical segmentation. The program cleans up the tissue
classification by applying morphological operations and label corrections
that improve the quality of subsequent segmentation steps.

The input is typically a classified volume with tissue labels (e.g.,
cerebrospinal fluid, grey matter, white matter), and the output is a
corrected version suitable for use with cortical surface extraction and
segmentation pipelines.

## EXAMPLES

    preprocess_segmentation classified.mnc preprocessed.mnc

## SEE ALSO

[classify](classify), [mincdefrag](mincdefrag),
[lobe_segment](lobe_segment)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
