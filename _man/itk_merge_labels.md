---
section: 1
title: itk_merge_labels
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_merge_labels

Merge multiple probability maps into a single label image by maximum probability voting.

`itk_merge_labels i input_i.mnc [j input_j.mnc ...] <output.mnc>`

## DESCRIPTION

**itk_merge_labels** combines multiple probability map volumes into a single
discrete label image. Each input consists of a label number paired with a
probability map volume. At each voxel, the label with the highest probability
is assigned to the output.

This tool is typically used after probabilistic segmentation or patch-based
classification to produce a final hard segmentation from a set of per-class
probability maps. Input pairs can also be specified via a CSV file.

## OPTIONS

`--csv` *input*
:   Read label-number and probability-map pairs from a CSV file instead of
    the command line. Each row should contain a label number and a file path.

`--clobber`
:   Overwrite the output file if it already exists.

`--byte`
:   Store output voxels as unsigned byte.

`--short`
:   Store output voxels as short integer.

## EXAMPLES

    # Merge three probability maps into a label image
    itk_merge_labels 1 prob_csf.mnc 2 prob_gm.mnc 3 prob_wm.mnc output.mnc

    # Merge using a CSV file
    itk_merge_labels --csv label_list.csv output.mnc

    # Store result as byte
    itk_merge_labels 1 prob_csf.mnc 2 prob_gm.mnc 3 prob_wm.mnc \
        output.mnc --byte

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_merge_discrete_labels](itk_merge_discrete_labels) ,
[itk_split_labels](itk_split_labels)
