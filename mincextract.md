MINCEXTRACT
1
$Date: 2004-05-20 21:52:08 $
mincextract
dump a hyperslab of MINC file data
mincextract
options
mincfile
DESCRIPTION
===========

`mincextract` dumps a chunk of MINC file data to standard output in the format of your choice.

OPTIONS
=======

`-ascii`  
Write out data as ascii strings (default)

`-byte`  
Write out data as 8-bit integers

`-short`  
Write out data as 16-bit integers

`-int`  
Write out data as 32-bit integers

`-long`  
Superseded by `-int`

`-float`  
Write out data as single precision floating-point values

`-double`  
Write out data as double precision floating-point values

`-filetype`  
Write out data in the type of the file

`-signed`  
Write out signed data (applies only to integer types)

`-unsigned`  
Write out unsigned data (applies only to integer types)

`-range` low high  
Specify the range of output values

`-normalize`  
Normalize integer pixel values to file max and min (Default)

`-nonormalize`  
Turn off pixel normalization

`-big-endian`  
Request big-endian (most significant byte first) format.

`-little-endian`  
Request little-endian (least significant byte first) format.

`-image_range` low high  
Specify the range of real image values for normalization

`-image_minimum` min  
Specify the minimum real image value for normalization

`-image_maximum` max  
Specify the maximum real image value for normalization

`-start` indexvector  
Specifies corner of hyperslab (C conventions for indices). Indices are either separated by spaces (enclosed by quotes) or commas (no quotes required).

`-count` indexvector  
Specifies edge lengths of hyperslab to read. Indices are either separated by spaces (enclosed by quotes) or commas (no quotes required).

`-positive_direction`  
Flip images to always have positive direction.

`-negative_direction`  
Flip images to always have negative direction.

`-any_direction`  
Do not flip images (Default).

*+xdirection*  
Flip images to give positive xspace:step value (left-to-right).

`-xdirection`  
Flip images to give negative xspace:step value (right-to-left).

`-xanydirection`  
Don't flip images along x-axis (default).

*+ydirection*  
Flip images to give positive yspace:step value (post-to-ant).

`-ydirection`  
Flip images to give negative yspace:step value (ant-to-post).

`-yanydirection`  
Don't flip images along y-axis (default).

*+zdirection*  
Flip images to give positive zspace:step value (inf-to-sup).

`-zdirection`  
Flip images to give negative zspace:step value (sup-to-inf).

`-zanydirection`  
Don't flip images along z-axis (default).

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

AUTHOR
======

Peter Neelin

COPYRIGHTS
==========

Copyright © 1993 by Peter Neelin

SEE ALSO
========

minctoraw1
