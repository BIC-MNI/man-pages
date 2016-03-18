# VOXELTOWORLD

voxeltoworld convert voxel coordinates to world coordinates

`voxeltoworld filename v1 v2 v3`

## DESCRIPTION

Transform coordinates of a point between voxel and world coordinate systems. The voxel coordinate system is aligned with the sampling grid of the image volume.

## OPTIONS

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES

To get the start positions of all three spatial coordinate axes in world coordinates:

voxeltoworld file.mnc 0 0 0

## AUTHOR

Peter Neelin

## COPYRIGHT

Copyright © 1993 by Peter Neelin

## See also

[worldtovoxel](worldtovoxel.md)
