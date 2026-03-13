---
section: 1
title: labels_to_rgb
author: David MacDonald
group: Label and Classification Tools
---
# labels_to_rgb

convert label values to RGB colour values using a lookup table

`labels_to_rgb input.mnc colour_map.txt output.mnc`

## DESCRIPTION

**labels_to_rgb** converts a labelled MINC volume into an RGB colour volume
using a colour map lookup table. Each integer label value in the input volume
is mapped to an RGB colour triplet as defined in the colour map text file.
The output is a MINC volume with vector RGB values suitable for visualization.

The colour map text file should contain one entry per label, mapping label
values to their corresponding red, green, and blue colour components.

## SEE ALSO

[lookup_labels](lookup_labels), [minclookup](minclookup),
[print_all_labels](print_all_labels)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
