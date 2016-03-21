---
section: 1
title: mincheader
author: Peter Neelin
---
# mincheader

mincheader prints out complete header information for a minc file

`mincheader -data <infile>`

## DESCRIPTION

*Mincheader* prints out the header information for a minc file in cdl format (the netCDF text format). *Mincheader* simply calls *mincdump*, writing out all information except the image data. If the input file is compressed, then its header is decompressed and only the header is printed. If the `-data` option is given, then the whole file is decompressed and all data (except the image) is dumped.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin


## See also

[mincinfo](mincinfo)
