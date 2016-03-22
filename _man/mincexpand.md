---
section: 1
author: 
- Peter Neelin
title: mincexpand
---
# mincexpand

mincexpand expands a compressed minc file, if necessary.
`mincexpand <options> <infile> <outfile>`

## DESCRIPTION

*Mincexpand* expands a compressed, packed, gzipped or zipped minc file into a temporary file using gunzip (or zcat or pcat) and prints out the name of the new file. If the input file is not compressed, then nothing is done and the original file name is printed. A second line is printed, indicating whether the name is that of a new temporary file ("Temporary") or that of the original file ("Original"). If no output file name is given, then the program generates its own.

## OPTIONS

`-header_only`  
Expand only enough of the file to be able to read the header.

`-all_data`  
Expand the whole file (default).

`-name_only`  
Print out only the file name, not the status (Temporary or Original).

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin
