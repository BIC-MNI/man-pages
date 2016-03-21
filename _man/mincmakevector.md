---
section: 1
title: mincmakevector
author: Peter Neelin
---
# mincmakevector

mincmakevector - convert a list of scalar minc files into one vector file
` mincmakevector <options> <in>.mnc .\[..\] <out>.mnc`

## DESCRIPTION

*Mincmakevector* converts a list of scalar minc files into one vector minc file. A vector minc file is one that contains the dimension *vector\_dimension* as the fastest varying dimension of the image data and represents vector data at each voxel such as RGB images or gradient volumes. A scalar minc file does not contain the vector dimension and represents grayscale or intensity data.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## General options

`-2`  
Create a MINC 2.0 format output file.

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-no_clobber`  
Synonym for `-noclobber`.

`-verbose`  
Print out progress information for each chunk of data copied (default).

`-quiet`  
Do not print out progress information.

`-buffer_size` size  
Specify the maximum size of the internal buffers (in kbytes). Default is 10 MB.

`-filetype`  
Create an output file with the same type as the first input file (default).

`-byte`  
Store output voxels as 8-bit integers.

`-short`  
Store output voxels as 16-bit integers.

`-int`  
Store output voxels as 32-bit integers

`-long`  
Superseded by `-int`.

`-float`  
Store output voxels as 32-bit floating point numbers.

`-double`  
Store output voxels as 64-bit floating point numbers.

`-signed`  
Create an output file with data stored in a signed type. This only has an effect if the one of the `-byte`, `-short` or `-int` options is specified.

`-unsigned`  
Create an output file with data stored in an unsigned type. This only has an effect if the one of the `-byte`, `-short` or `-int` options is specified.

`-valid_range` min max  
Create an output file with integer data stored in the specified restricted range. This only has an effect if the one of the `-byte`, `-short` or `-int` options is specified.

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES

To convert files containing red, green and blue colour components into an RGB file:

mincmakevector red.mnc green.mnc blue.mnc rgb.mnc

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright 1997 by Peter Neelin
