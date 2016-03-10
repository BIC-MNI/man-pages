MINCWINDOW
1
$Date: 2004-05-20 21:52:09 $
mincwindow
limit voxel values to a given range
mincwindow
options
in.mnc
out.mnc
min
max
newvalue
DESCRIPTION
===========

`mincwindow` copies *in.mnc* to *out.mnc*. Each voxel value that lies within the window \[*min*,*max*\] is copied unmodified. If the voxel value is outside that window and *newvalue* is specified, then that voxel is set to *newvalue*. Otherwise, the voxel value is set to *min* if it is less than *min*, and to *max* if it is higher than *max*.

OPTIONS
=======

`-2`  
Create MINC 2.0 format output files.

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-verbose`  
Print out log messages (default).

`-quiet`  
Do not print log messages.

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

SEE ALSO
========

mincmath1, minccalc1
