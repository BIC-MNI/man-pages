---
section: 1
title: remap_to_lobes
author: David MacDonald
group: Registration Scripts
---
# remap_to_lobes

remap a detailed segmentation label file to lobe-level labels

`remap_to_lobes segmentation.txt lobes.txt`

## DESCRIPTION

**remap_to_lobes** remaps a detailed per-vertex segmentation label file to
coarser lobe-level labels. The input *segmentation.txt* contains fine-grained
anatomical labels (one per vertex), and the output *lobes.txt* contains the
corresponding lobe-level labels (e.g., frontal, parietal, temporal,
occipital).

This is useful for computing summary statistics at the lobe level from
detailed cortical parcellations.

## EXAMPLES

    remap_to_lobes detailed_labels.txt lobe_labels.txt

## SEE ALSO

[regional_thickness](regional_thickness),
[lobe_segment](lobe_segment), [print_all_labels](print_all_labels)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
