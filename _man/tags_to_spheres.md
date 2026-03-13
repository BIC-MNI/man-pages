---
section: 1
title: tags_to_spheres
author: David MacDonald
group: Tag Point Tools
---
# tags_to_spheres

create sphere objects at tag point positions

`tags_to_spheres input.tag output.obj radius [n_triangles]`

## DESCRIPTION

**tags_to_spheres** creates a set of sphere objects centred at each tag point
position in the input tag file. Each sphere is rendered with the specified
**radius**. If the radius is less than or equal to zero, the weight values
stored in the tag file are used as radii instead.

The optional **n_triangles** argument controls the tessellation resolution of
each sphere. The default value is 80 triangles per sphere.

The output is a BIC object file containing all the generated spheres.

## SEE ALSO

[extracttag](extracttag), [tagtominc](tagtominc),
[stats_tag_file](stats_tag_file)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
