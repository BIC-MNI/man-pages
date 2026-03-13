---
section: 1
title: tag_volume
author: David MacDonald
group: Tag Point Tools
---
# tag_volume

create a volume from tag points sampling at specified y-axis intervals

`tag_volume example.mnc input.tags y_min y_max y_step`

## DESCRIPTION

**tag_volume** creates a MINC volume from tag points by sampling at specified
intervals along the y-axis. The output volume uses the same grid as the example
MINC file. Tag points are placed into the volume at y-axis positions ranging
from **y_min** to **y_max** in increments of **y_step**.

## SEE ALSO

[tagtominc](tagtominc), [tags_to_spheres](tags_to_spheres),
[extracttag](extracttag)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
