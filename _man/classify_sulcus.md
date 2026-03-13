---
section: 1
title: classify_sulcus
author: David MacDonald
group: Label and Classification Tools
---
# classify_sulcus

classify sulcal regions on a cortical surface

`classify_sulcus surface.obj output_values.mnc step [prob1.mnc]`

## DESCRIPTION

`classify_sulcus` classifies sulcal regions on a cortical surface object.
Given a surface mesh and a step size, it produces an output volume
containing the classification of sulcal regions. An optional probability
volume can be provided to guide the classification.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`surface.obj`
:   The input cortical surface object file.

`output_values.mnc`
:   The output MINC volume containing sulcal classification values.

`step`
:   The step size used for classification.

`prob1.mnc`
:   An optional probability map volume to guide classification.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[label_sulci](label_sulci) [fill_sulci](fill_sulci) [clean_surface_labels](clean_surface_labels)
