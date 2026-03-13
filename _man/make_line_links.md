---
section: 1
title: make_line_links
author: David MacDonald
group: Surface and Geometry Tools
---
# make_line_links

create line segments linking two input line objects

`make_line_links input_lines1.obj input_lines2.obj output_lines.obj n_links`

## DESCRIPTION

**make_line_links** creates a set of line segments that connect corresponding
points between two input line objects. The *n_links* parameter specifies the
number of linking line segments to generate between *input_lines1.obj* and
*input_lines2.obj*.

The output *output_lines.obj* contains the generated linking lines, which
are useful for visualizing correspondences between two curves or contours,
such as sulcal lines on different cortical surfaces.

## EXAMPLES

    make_line_links contour1.obj contour2.obj links.obj 20

## SEE ALSO

[coalesce_lines](coalesce_lines), [reparameterize_line](reparameterize_line)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
