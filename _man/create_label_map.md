---
section: 1
title: create_label_map
author: David MacDonald
group: Label and Classification Tools
---
# create_label_map

create a label map volume from a template

`create_label_map template.mnc output.mnc`

## DESCRIPTION

`create_label_map` creates a label volume positioned at the first slice of
the template volume. The output contains all possible label values
arranged in a square grid pattern. This is useful for visualizing or
verifying label colour mappings.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`template.mnc`
:   The template MINC volume providing the spatial sampling grid.

`output.mnc`
:   The output MINC volume containing the label map.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[add_labels](add_labels) [lookup_labels](lookup_labels) [labels_to_rgb](labels_to_rgb)
