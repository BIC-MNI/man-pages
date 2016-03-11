MINCHEADER
1
$Date: 2004-05-20 21:52:08 $
mincheader
prints out header information for a minc file
mincheader
-data
<infile>
DESCRIPTION
===========

*Mincheader* prints out the header information for a minc file in cdl format (the netCDF text format). *Mincheader* simply calls *mincdump*, writing out all information except the image data. If the input file is compressed, then its header is decompressed and only the header is printed. If the `-data` option is given, then the whole file is decompressed and all data (except the image) is dumped.

AUTHOR
======

Peter Neelin

COPYRIGHTS
==========

Copyright © 1993 by Peter Neelin
