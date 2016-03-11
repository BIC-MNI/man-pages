# MINCMATH

mincmath perform simple math operations on minc files

`mincmath <options> <in1>.mnc <in2>.mnc <out>.mnc`

## DESCRIPTION

*Mincmath* will perform simple, voxel-by-voxel math operations, on one or more minc files of the same shape and having the same coordinate sampling, producing a single output file. Operations can be unary (operate on one file), binary (two input files) or cumulative (operate on two or more input files). Cumulative operations can also be performed across a specified dimension of the input files.

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

`-debug`  
Print out debugging information.

`-filelist` filename  
Specify a file containing a list of input file names. If "-" is given, then file names are read from the standard input. If this option is given, then there should be no input file names specified on the command line. Empty lines in the input file are ignored.

`-copy_header`  
Copy all of the header information from the first input file (default for one input file).

`-nocopy_header`  
Do not copy all of the header from the first input file; copy only coordinate information (default for more than one input file).

`-filetype`  
Create an output file with the same type as the first input file (default).

`-byte`  
Store output voxels in 8-bit integer format.

`-short`  
Store output voxels in 16-bit integer format.

`-int`  
Store output voxels in 32-bit integer format.

`-long`  
Superseded by `-int`.

`-float`  
Store output voxels in 32-bit floating point format.

`-double`  
Store output voxels in 64-bit floating point format.

`-signed`  
Use signed, two's complement integer format. Applies only if the output voxel type is specified to be an integer type (one of `-byte`, `-short`, `-int` or `-long`).

`-unsigned`  
Use unsigned integer format. Applies only if the output voxel type is specified to be an integer type (one of `-byte`, `-short`, `-int` or `-long`).

`-range` min max  
Restrict the valid range of integer data. Applies only if one of the `-byte`, `-short`, `-int` or `-long` options is specified.

`-max_buffer_size_in_kb` size  
Specify the maximum size of the internal buffers (in kbytes). Default is 4096 (4MB).

`-dimension` dimname  
Specify a dimension along which we wish to perform a cumulative operation.

`-check_dimensions`  
Check that all input files have matching sampling in world dimensions (default).

`-nocheck_dimensions`  
Ignore any differences in world dimensions sampling for input files .

`-propagate_nan`  
Invalid data (Not-A-Number or NaN) at a voxel in any of the input files will produce invalid data in the output file at that voxel (default).

`-ignore_nan`  
For cumulative operations, invalid data (NaN) in an input file is ignored, ie. treated as though it is not present.

`-nan`  
When an illegal operation is attempted at a voxel (such as divide by zero), invalid data (NaN) is stored in the output file (default). Having no valid input data for a cumulative operation is also considered an illegal operation when `-ignore_nan` is used.

`-zero`  
When an illegal operation is attempted at a voxel (such as divide by zero), value zero is stored in the output file.

`-illegal_value` value  
When an illegal operation is attempted at a voxel (such as divide by zero), the specified value is stored in the output file.

## Options for specifying constants

`-constant` value  
Specify a single constant.

`-const` value  
Synonym for `-constant`.

`-const2` value1 value2  
Specify two constants.

## Operations

`-add`  
Cumulatively add two or more volumes, or add a volume and a constant.

`-sub`  
Subtract two volumes or a volume minus a constant.

`-mult`  
Cumulatively multiply two or more volumes, or multiply a volume and a constant.

`-div`  
Divide two volumes or a volume divided by a constant.

`-invert`  
Calculate 1/x at each voxel, where x is the input voxel value. If a constant c is specified (with -constant), then calculate c/x at each voxel.

`-sqrt`  
Calculate the square root of a volume.

`-square`  
Calculate the square of a volume.

`-abs`  
Calculate the absolute value of a volume.

`-maximum`  
Calculate the maximum of a series of volumes.

`-minimum`  
Calculate the minimum of a series of volumes.

`-exp`  
Calculate *c2\*exp(c1\*x)* at each voxel of a volume, where *x* is the voxel value and *c1* and *c2* are constants specified by `-constant c1` or `-const2 c1 c2`. The default value for these constants is 1.0.

`-log`  
Calculate *log(x/c2)/c1* for each voxel of a volume, where *x* is the voxel value and *c1* and *c2* are constants specified by `-constant c1` or `-const2 c1 c2`. The default value for these constants is 1.0.

`-scale`  
Scale a volume either by multiplying by a single constant (use -constant) or by multiplying by the first constant and adding the second (use -const2).

`-clamp`  
Clamp a volume to lie between two values specified with `-const2`.

`-segment`  
Segment (binarize) a volume so that values within the range specified by `-const2` give value 1 and those outside it give value 0.

`-nsegment`  
Opposite of `-segment`: values within the range specified by `-const2` give value 0 and those outside it give value 1.

`-percentdiff`  
Calculate the percent difference between two volumes (normalized to the first volume). If the first volume is less than a threshold (or zero), then the value specified by `-nan` or `-zero` is used. The threshold is specified using `-constant`, with a default of zero.

`-pd`  
Synonym for `-percentdiff`.

`-eq`  
Test for equality of two volumes or a volume and a constant. Values are rounded to the nearest integer before performing the test. Output 1 for true and 0 for false at each voxel.

`-ne`  
Test for inequality of two volumes or a volume and a constant. Values are rounded to the nearest integer before performing the test. Output 1 for true and 0 for false at each voxel.

`-gt`  
Test for volume 1 > volume 2 or a volume > a constant. Output 1 for true and 0 for false at each voxel.

`-ge`  
Test for volume 1 >= volume 2 or a volume >= a constant. Output 1 for true and 0 for false at each voxel.

`-lt`  
Test for volume 1 < volume 2 or a volume < a constant. Output 1 for true and 0 for false at each voxel.

`-le`  
Test for volume 1 <= volume 2 or a volume <= a constant. Output 1 for true and 0 for false at each voxel.

`-and`  
Test for volume 1 && volume 2 or a volume && a constant. Values are rounded to the nearest integer before performing the test. Output 1 for true and 0 for false at each voxel.

`-or`  
Test for volume 1 || volume 2 or a volume || a constant. Values are rounded to the nearest integer before performing the test. Output 1 for true and 0 for false at each voxel.

`-not`  
Perform logical negation on a volume: convert non-zero to zero and zero to one. Values are rounded to the nearest integer before the negation.

`-isnan`  
Test a volume for invalid values (NaN). Output 1 for invalid values and 0 for valid values.

`-nisnan`  
Opposite of -isnan. Output 0 for invalid values and 1 for valid values.

`-count_valid`  
Count the number of valid voxels across a series of volumes. If none of the volumes has valid data, then zero is written out (ie. `-zero` and `-ignore_nan` are always assumed, unlike other cumulative operations).

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin

## SEE ALSO

[minccalc](minccalc)
