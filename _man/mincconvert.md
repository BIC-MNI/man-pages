# MINCCONVERT

mincconvert convert between MINC 1 to MINC 2 format.

`mincconvert -clobber -2 infile outfile`
`mincconvert -help`

## DESCRIPTION

`mincconvert` copies the input file to the output file, possibly converting the file from MINC 1 to MINC 2 format, or vice versa.

With the `-template` flag, `mincconvert` creates a "template" volume from the input MINC volume. The template volume preserves all of the structure (dimensions, variables, and attributes) of the input MINC volume but omits all data. Any attempt to read data will return zeroes.

The resulting file is typically much shorter than a normal MINC volume, and may be useful for scripts which want to carry such structural information forward into their output files. As a hint to future programmers and users, this program places a special global attribute in the file, with the name *class* and the value *template*.

## OPTIONS

`-2`  
Create a MINC 2 format file

`-clobber`  
Overwrite a pre-existing output file. `-help` Print a summary of command line options and exit

`-template`  
Create a template file.

`-compress` N  
Compress file with compression level *N*. Valid compression levels are 0 for no compression to 9 for maximum compression. The option has no effect if the output file is a MINC 1 file.

`-chunk` M  
Store file in a block-structured arrangement, using hypercubes of edge length *M*. The option has no effect if the output file is a MINC 1 file.

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Bert Vincent - bert@bic.mni.mcgill.ca

## COPYRIGHTS

Copyright © 2003 by Robert Vincent and the Montreal Neurological Institute.
