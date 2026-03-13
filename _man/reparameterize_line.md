---
section: 1
title: reparameterize_line
author: David MacDonald
group: Surface and Geometry Tools
---
# reparameterize_line

reparameterize a line object by redistributing points evenly

`reparameterize_line input_lines.obj output_lines.obj`

## DESCRIPTION

**reparameterize_line** reparameterizes line objects by redistributing
points evenly along the line. The input *input_lines.obj* contains one or
more line objects, and the output *output_lines.obj* contains the same lines
with points redistributed at uniform arc-length intervals.

This is useful for preparing line objects (such as sulcal curves or contour
lines) for analyses that require evenly spaced sampling, or for improving
the quality of line-based visualizations.

## EXAMPLES

    reparameterize_line sulcal_line.obj even_line.obj

## SEE ALSO

[coalesce_lines](coalesce_lines), [extract_largest_line](extract_largest_line),
[make_line_links](make_line_links)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
