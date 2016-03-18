# XFM2DEF
xfm2def convert a MNI transform file to a deformation volume
xfm2def
options
input.xfm
def\_vol.mnc
DESCRIPTION
===========

`xfm2def` takes an input transform *input.xfm* that can consist of a series of concatenated transforms in a single xfm file and converts this into a single deformation volume that is output as *def\_vol.mnc*. Note that the output is not a tranform file itself, you can then make use of this volume in a MINC tranform by creating an .xfm file as such:

MNI Transform File Transform\_Type = Grid\_Transform; Displacement\_Volume = def\_vol.mnc;

The output resolution and sampling of the deformation grid must be specified or a default size will be used. (100x100x100 1mm steps centred around the origin).

OPTIONS
=======

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

`-verbose`  
Print out extra progress information while running.

`-clobber`  
Overwrite any existing output file

`-xnelements` nx  
Number of elements along the xspace dimension.

`-ynelements` ny  
Number of elements along the yspace dimension.

`-znelements` nz  
Number of elements along the zspace dimension.

`-xstep` xstep  
Step between voxels along the xspace dimension.

`-ystep` ystep  
Step between voxels along the yspace dimension.

`-zstep` zstep  
Step between voxels along the zspace dimension.

`-xstart` xstart  
Position of centre of first voxel along the xspace dimension.

`-ystart` ystart  
Position of centre of first voxel along the yspace dimension.

`-zstart` zstart  
Position of centre of first voxel along the zspace dimension.

`-xdircos` x1 x2 x3  
Direction cosines for the xspace dimension.

`-ydircos` y1 y2 y3  
Direction cosines for the yspace dimension.

`-zdircos` z1 z2 z3  
Direction cosines for the zspace dimension.

AUTHOR
======

Andrew Janke

COPYRIGHTS
==========

Copyright © 2010 Andrew Janke - a.janke@gmail.com
