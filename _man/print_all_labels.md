---
section: 1
title: print_all_labels
author: David MacDonald
group: Label and Classification Tools
---
# print_all_labels

print voxel counts for each label in a MINC volume

`print_all_labels labels.mnc [min_value max_value]`

## DESCRIPTION

**print_all_labels** displays the number of voxels for each distinct label
value found in a labelled MINC volume. For each label, the output includes
the label value and its voxel count.

Optional *min_value* and *max_value* arguments restrict the output to labels
within the specified range.

## EXAMPLES

Print counts for all labels:

    print_all_labels atlas.mnc

Print counts for labels 1 through 10:

    print_all_labels atlas.mnc 1 10

## SEE ALSO

[print_all_label_bounding_boxes](print_all_label_bounding_boxes),
[lookup_labels](lookup_labels), [mincstats](mincstats)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
