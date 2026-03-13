---
section: 1
title: print_world_value
author: David MacDonald
group: Statistical and Analysis Tools
---
# print_world_value

print the voxel value at a given world coordinate in a volume

`print_world_value volume.mnc x y z`

## DESCRIPTION

**print_world_value** prints the voxel value at the specified world
coordinates (*x*, *y*, *z*) in a MINC volume. The program looks up the
value in the volume corresponding to the given world-space position.

This command is similar to **print_volume_value** and provides a convenient
way to query individual voxel values at specific locations.

## EXAMPLES

    print_world_value brain.mnc 0 -25 10

## SEE ALSO

[print_volume_value](print_volume_value),
[print_world_values](print_world_values),
[volume_object_evaluate](volume_object_evaluate)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
