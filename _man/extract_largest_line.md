---
section: 1
title: extract_largest_line
author: David MacDonald
group: Surface and Geometry Tools
---
# extract_largest_line

extract the largest connected line from a line object

`extract_largest_line input_lines.obj output_lines.obj`

## DESCRIPTION

`extract_largest_line` reads a line object file that may contain multiple
disjoint lines and writes only the largest (longest) line to the output
file. All other lines are discarded.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`input_lines.obj`
:   The input line object file potentially containing multiple lines.

`output_lines.obj`
:   The output line object file containing only the largest line.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[coalesce_lines](coalesce_lines) [reparameterize_line](reparameterize_line)
