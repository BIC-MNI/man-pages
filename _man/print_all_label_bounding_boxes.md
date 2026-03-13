---
section: 1
title: print_all_label_bounding_boxes
author: David MacDonald
group: Label and Classification Tools
---
# print_all_label_bounding_boxes

print voxel counts and bounding boxes for each label in a MINC volume

`print_all_label_bounding_boxes labels.mnc [min_value max_value]`

## DESCRIPTION

**print_all_label_bounding_boxes** displays the number of voxels and the
bounding box for each distinct label value found in a labelled MINC volume.
For each label, the output includes the label value, the voxel count, and
the minimum and maximum world coordinates defining the bounding box.

Optional *min_value* and *max_value* arguments restrict the output to labels
within the specified range.

## EXAMPLES

Print bounding boxes for all labels:

    print_all_label_bounding_boxes atlas.mnc

Print bounding boxes for labels 1 through 10:

    print_all_label_bounding_boxes atlas.mnc 1 10

## SEE ALSO

[print_all_labels](print_all_labels), [mincstats](mincstats),
[find_image_bounding_box](find_image_bounding_box)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
