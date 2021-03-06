---
section: 1
title: minclookup
author: Peter Neelin
---
# minclookup

minclookup - perform lookup table conversions on minc files
`minclookup <options> <in1>.mnc <out>.mnc`

## DESCRIPTION

*Minclookup* will perform a lookup table operation on each voxel of a minc file. A lookup table consists of a list of input values with matching output values. Each voxel of the input file is found in the lookup table and the corresponding output value is written out. These output values can be either scalar or vector values so, for example, a colour lookup table would have four columns: one column for input values and one column for each of red, green and blue output values.

Lookup tables can take one of two forms: *continuous* or *discrete*.

A continuous lookup table is for treating voxel values as continuous (real) values and converting values by doing interpolation between the values given in the lookup table. A discrete lookup table treats input values as integers and deals with them as completely independent entries, doing no interpolation.

The most common use of continuous lookup tables is for converting intensity values into RGB colours. To make the lookup tables simpler, the input values are all rescaled into the range zero to one. By default, the smallest value in the file maps to zero and the largest maps to one. This value is then found in the lookup table, usually between two entries in the table (the table is always sorted in ascending order of input values). Linear interpolation is then done on each output column and the resultant value (or values) is written to the output file. If there is more than one output value per input value, then the dimension vector_dimension is added to the output file with length equal to the number of output columns in the lookup table. For input values outside the range zero to one, the nearest table value is used.

Discrete lookup tables are usually used for remapping label values. Each input value is treated as an integer (it is not rescaled) and if it is found in the lookup table, then the corresponding value (or values) is written to the output file. If it is not found, then a null value is written out (zero by default). No interpolation is done with discrete lookup tables - to get a non-null output value, there must be an entry in the table.

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

`-buffer_size size`
Specify the maximum size of the internal buffers (in kbytes). Default is 10 MB.

`-filetype`  
Create an output file with the same type as the first input file (default).

`-byte`  
Store each voxel as an 8-bit integer.

`-short`  
Store each voxel as a 16-bit integer.

`-int`  
Store each voxel as a 32-bit integer.

`-long`  
Superseded by `-int`.

`-float`  
Store each voxel in 32-bit floating point format.

`-double`  
Store each voxel in 64-bit floating point format.

`-signed`  
Create an output file with data stored in a signed type. This option is meaningless when used with floating point data formats, which are always signed.

`-unsigned`  
Create an output file with data stored in an unsigned type. This option is meaningless when used with floating point data formats.

`-valid_range` min max  
Scale integer voxel values to fall between the values *min* and *max*. By default integer voxel values will be scaled to use the entire range of the base type. This option is meaningless when used with floating point data formats.

## Lookup table options

`-gray`  
Use a gray lookup table to write out RGB values (default).

`-grey`  
Synonym for `-gray`.

`-hotmetal`  
Use a hot-metal lookup table to write out RGB values.

`-spectral`  
Use a spectral (rainbow) lookup table to write out RGB values.

`-invert`  
Invert the lookup table so that the maximum value maps to zero and the minimum value maps to one. Applies only to continuous lookup tables.

`-noinvert`  
Do not invert the lookup table - the minimum maps to zero and the maximum maps to one (default).

`-range min max`  
Specify the range of values that should map to the range of the lookup table (default is the full range of the input file).

`-minimum min`  
Specify the input value that maps to the minimum value in the lookup table.

`-maximum max`  
Specify the input value that maps to the maximum value in the lookup table.

`-lookup_table [file|-]`
Specify the name of a file containing the lookup table. If `-` is given, the lookup table is read from the standard input. The file must have at least two columns: The first column gives the input values; the other columns give the corresponding output values. For a continuous lookup table, the first column should contain a value between zero and one inclusive Explicit entries for both zero and one should usually be given. For a discrete lookup table, the first column should contain integer values. If more than one output column is given, then the output file will have the dimension *vector_dimension* with a length equal to the number of output columns. The lines of the table will be sorted if necessary so that the first column is in ascending order.

`-lut_string lookup-table-string`  
Specify the complete lookup table as a single string. The semicolon character ";" is used to separate lines.

`-continuous`  
The lookup table is continuous (see description above): Input values are treated as continuous (real) values and are rescaled to the range zero to one before being looked up; interpolation is done between values in the table. This is the default behaviour.

`-discrete`  
The lookup table is discrete (see description above): Input values are treated as integers and no interpolation is done between input values.

`-null_value null-value-string`
Specify a null value to be used with discrete lookup tables when a value is not found in the lookup table. This value must be specified as a comma-separated list of values, with the same number of values as output columns in the lookup table.

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES

To get hot-metal RGB images from an MRI file:

`minclookup -hotmetal input.mnc output.mnc`

To convert the labels in a minc label file, use `-discrete`:

`minclookup -discrete -lookup_table lookupfile in_labels.mnc out_labels.mnc`

where lookupfile is a file containing entries to map label 2 to 4 and label 3 to 5:

```
2 4 
3 5
```

You could also specify this lookup table on the command line:

`minclookup -discrete -lut_string '2 4;3 5' in_labels.mnc out_labels.mnc`

To get a grey RGB file, with red for values less than the minimum and green for values greater than the minimum, you can give two zero entries and two one entries. The first zero is used for negative values, the second zero is used for interpolation to the next entry. There is no ambiguity about how to handle a value of exactly zero because the first and last values of the table are handled in a special way to make sure that they are treated as within range if this sort of two-entry situation occurs.

`minclookup -lookup_table - input.mnc output.mnc <<EOF 0 1 0 0 0 0 0 0 1 1 1 1 1 0 1 0 EOF`

To invert a scalar image, you could use minclookup:

`minclookup -lut_string '0 1;1 0' in.mnc out.mnc`

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin
