---
section: 1
title: print_volume_value
author: David MacDonald
group: Statistical and Analysis Tools
---
# print_volume_value

print the voxel value at a given world coordinate in a volume

`print_volume_value volume.mnc x y z`

## DESCRIPTION

**print_volume_value** prints the interpolated voxel value at the specified
world coordinates (*x*, *y*, *z*) in a MINC volume. The program converts
the world coordinates to voxel coordinates and evaluates the volume at that
position.

## EXAMPLES

    print_volume_value brain.mnc 0 -25 10

## SEE ALSO

[print_world_value](print_world_value),
[print_world_values](print_world_values),
[volume_object_evaluate](volume_object_evaluate)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
