---
section: 1
title: label_sulci
author: David MacDonald
group: Label and Classification Tools
---
# label_sulci

label sulcal regions on a cortical surface using reference sulcal points and value ranges

`label_sulci surface.obj sulcal_points.obj values.txt min max value_to_set output.txt`

## DESCRIPTION

**label_sulci** labels sulcal regions on a cortical surface object. Given a
surface, a set of reference sulcal points, and a text file of per-vertex
values, the program identifies vertices whose values fall within the specified
range (between *min* and *max*) and assigns them the label *value_to_set*.
The result is written to an output text file containing per-vertex labels.

This tool is typically used in cortical surface analysis pipelines to
classify sulcal regions based on depth or curvature values and anatomical
landmarks.

## SEE ALSO

[classify_sulcus](classify_sulcus), [fill_sulci](fill_sulci),
[clean_surface_labels](clean_surface_labels)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
