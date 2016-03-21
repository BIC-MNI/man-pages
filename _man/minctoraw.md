---
section: 1
title: minctoraw
---
# minctoraw

minctoraw copy data from a MINC file

`minctoraw options mincfile`

## DESCRIPTION

`minctoraw` dumps a chunk of MINC file data to standard output in the format of your choice.

This program is largely superceded by [mincextract](mincextract)

## OPTIONS

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

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## SEE ALSO

[mincextract](mincextract)
