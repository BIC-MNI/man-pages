# MINCCONCAT

mincconcat concatenate minc files along a specific dimension
`mincconcat <options> <infile1>.mnc <infile2>.mnc <outfile>.mnc`

## DESCRIPTION

*Mincconcat* will concatenate a number of minc files together, producing a single output file. The concatenation is done along a specified dimension, with the slices being sorted into ascending order. The concatenation dimension can either be a dimension in the file, in which case coordinates for sorting are taken directly from the input files, or it can be a new dimension and the coordinates are specified with a command-line option.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## General options

`-2`  
Create a MINC 2.0 format output file.

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-verbose`  
Print out progress information for each chunk of data copied (default).

`-quiet`  
Do not print out progress information.

`-max_chunk_size_in_kb` size  
Specify the maximum size of the copy buffer (in kbytes). Default is 4096 kbytes.

`-filelist` filename  
Specify a file containing a list of input file names. If "-" is given, then file names are read from stdin. If this option is given, then there should be no input file names specified on the command line. Empty lines in the input file are ignored.

## Output type options

`-filetype`  
Don't do any type conversion (default).

`-byte`  
Write out 8-bit integer voxels.

`-short`  
Write out 16-bit integer voxels.

`-int`  
Write out 32-bit integer voxels.

`-long`  
Superseded by -int.

`-float`  
Write out single-precision floating point values.

`-double`  
Write out double-precision floating point values.

`-signed`  
Write out values as signed integers (default for short and long). Ignored for floating point types.

`-unsigned`  
Write out values as unsigned integers (default for byte). Ignored for floating point types.

`-valid_range` min max  
Specifies the valid range of output voxel values in their integer representation. Default is the full range for the type and sign. This option is ignored for floating point values.

## Concatenation options

`-concat_dimension` name  
Specifies the name of concatenation dimension. If the dimension exists in the input files, then coordinates are taken from those files. If not, then a new dimension is created and the coordinate for each input file is taken from command-line options. The default is to use the slowest varying dimension of the first file.

`-start` start  
Specifies the starting coordinate for the new dimension (default = 0.0).

`-step` step  
Specifies the separation between voxels for the new dimension (default = 1.0).

`-width` width  
Specifies the (constant) width of each sample along the new dimension (default = none).

`-coordlist` c1,c2,...  
Specifies a comma-separated list of coordinates along the new dimension.

`-widthlist` w1,w2,...  
Specifies a comma-separated list of widths along the new dimension.

`-filestarts` s1,s2,...  
Specifies a comma-separated list of offsets to the coordinate origins for each of the files listed on the command line. This option is useful for concatenating files along an existing dimension, for example for concatenating multiple functional runs along a *time* dimension.

`-check_dimensions`  
Check that all input files have matching sampling in world dimensions (default).

`-nocheck_dimensions`  
Ignore any differences between input files in world dimensions sampling.

`-ascending`  
Sort coordinates in ascending order (default).

`-descending`  
Sort coordinates in descending order.

`-interleaved`  
Sort slabs by their dimension coordinate, interleaving if necessary (default).

`-sequential`  
Don't sort slabs, just concatenate them together. WARNING - this will destroy the dimension information along the concatenating dimension, replacing the start and step with zero and one.

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES

To concatenate two volumes with dimensions zspace, yspace, xspace, having interleaved slices along zspace, we can simply use

mincconcat input1.mnc input2.mnc output.mnc

If we have a bunch of compressed (yspace, xspace) images that we wish to concatenate into an evenly spaced volume, then we can type

mincconcat input1.mnc.gz input2.mnc.gz input3.mnc.gz BSOL input4.mnc.gz output.mnc BSOL -concat\_dimension zspace -start -23 -step 2

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin
