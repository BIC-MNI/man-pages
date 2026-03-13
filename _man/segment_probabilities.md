---
section: 1
title: segment_probabilities
author: David MacDonald
group: Volume Operations
---
# segment_probabilities

compute segmentation probabilities on a surface using reference line objects

`segment_probabilities surface.obj output_values.mnc lines.obj [value1] ...`

## DESCRIPTION

**segment_probabilities** computes segmentation probabilities on a surface
object using one or more reference line objects. The tool evaluates probabilities
at each vertex of the input surface based on proximity and relationship to the
provided line objects. Optional value arguments can be specified to assign
specific probability values to each line object.

The output is written to a MINC file containing the computed probability values.

## SEE ALSO

[surface_mask](surface_mask), [label_sulci](label_sulci)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
