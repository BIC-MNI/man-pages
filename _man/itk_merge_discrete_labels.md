---
section: 1
title: itk_merge_discrete_labels
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_merge_discrete_labels

Merge multiple discrete label volumes by overlay (non-zero overwrite).

`itk_merge_discrete_labels input_1.mnc [input_2 ...] <output.mnc>`

## DESCRIPTION

**itk_merge_discrete_labels** merges multiple discrete label volumes into a
single output volume by sequential overlay. Each input volume is applied in
order: non-zero voxels in later volumes overwrite values from earlier ones.
This simple overlay strategy is useful for combining partial segmentations
that cover non-overlapping or priority-ordered regions.

Input files can also be specified via a CSV file. The output data type can be
set to byte or short integer.

## OPTIONS

`--csv` *input*
:   Read input file paths from a CSV file (one path per line).

`--clobber`
:   Overwrite the output file if it already exists.

`--byte`
:   Store output voxels as unsigned byte.

`--short`
:   Store output voxels as short integer.

## EXAMPLES

    # Merge two label volumes (later volumes take priority)
    itk_merge_discrete_labels base_labels.mnc overlay_labels.mnc merged.mnc

    # Merge multiple volumes
    itk_merge_discrete_labels seg1.mnc seg2.mnc seg3.mnc merged.mnc --short

    # Merge from a file list
    itk_merge_discrete_labels --csv file_list.csv merged.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_merge_labels](itk_merge_labels) ,
[itk_split_labels](itk_split_labels)
