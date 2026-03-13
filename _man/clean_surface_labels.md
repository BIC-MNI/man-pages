---
section: 1
title: clean_surface_labels
author: David MacDonald
group: Label and Classification Tools
---
# clean_surface_labels

correct labels on a surface object

`clean_surface_labels surface.obj labels.txt new_labels.txt`

## DESCRIPTION

`clean_surface_labels` reads a surface object and a set of per-vertex
labels, then corrects the labels by smoothing and removing spurious
assignments. The input labels should be in the range 0 to 255. The
corrected labels are written to a new text file.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`surface.obj`
:   The input surface object file.

`labels.txt`
:   A text file containing one label per vertex (values in range 0 to 255).

`new_labels.txt`
:   The output text file containing the corrected labels.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[classify_sulcus](classify_sulcus) [label_sulci](label_sulci)
