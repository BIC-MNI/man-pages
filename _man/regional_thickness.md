---
section: 1
title: regional_thickness
author: David MacDonald
group: Statistical and Analysis Tools
---
# regional_thickness

compute regional cortical thickness statistics from per-vertex data

`regional_thickness input_thickness.txt input_labels.txt output.txt`

## DESCRIPTION

**regional_thickness** computes regional cortical thickness statistics from
per-vertex thickness measurements and a per-vertex label file. For each
distinct label (brain region), the program computes summary statistics
(such as mean thickness) from the thickness values of vertices belonging
to that region.

The *input_thickness.txt* file contains one thickness value per vertex. The
*input_labels.txt* file contains one integer label per vertex, identifying
which brain region each vertex belongs to. The output file contains the
computed regional statistics.

## EXAMPLES

    regional_thickness thickness.txt labels.txt regional_stats.txt

## SEE ALSO

[remap_to_lobes](remap_to_lobes),
[print_all_labels](print_all_labels)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
