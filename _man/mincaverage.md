# MINCAVERAGE

mincaverage average minc files

`mincaverage <options> <in1>.mnc <in2>.mnc <out>.mnc`

## DESCRIPTION

**Mincaverage** averages minc files together. A range of optional behaviour is permitted as well: pre-normalizing volumes, creating a standard deviation volume, averaging over a specified dimension of the input files.

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

`-debug`  
Print extra information (e.g. normalization factors).

`-filelist` filename  
Specify a file containing a list of input file names. If "-" is given, then file names are read from stdin. If this option is given, then there should be no input file names specified on the command line. Empty lines in the input file are ignored.

`-max_buffer_size_in_kb` buffer-size  
Specify the maximum size of the internal buffers (in kbytes). Default is 4096 kbytes.

## Output type options

These options control the storage precision and size of individual voxel values in the output file.

`-filetype`  
Don't do any type conversion (default).

`-byte`  
Write out 8-bit integer values.

`-short`  
Write out 16-bit integer values.

`-int`  
Write out 32-bit integer values.

`-long`  
Superseded by -int.

`-float`  
Write out single-precision floating point values.

`-double`  
Write out double-precision floating point values.

`-signed` Write out values as signed integers (default for short and long). Ignored for floating point types.

`-unsigned`  
Write out values as unsigned integers (default for byte). Ignored for floating point types.

`-range` min max  
specifies the valid range of output voxel values in their integer representation. Default is the full range for the type and sign. This option is ignored for floating point values. For it to have any effect, you must specify a type.

## Averaging options

`-normalize`  
Normalize volumes to their global average before averaging them (based on the mean of voxels with value greater than 2 percent of full range above the minimum).

`-nonormalize`  
Do not normalize volumes (default).

`-sdfile` sdfile.mnc  
Specify the name of an output standard deviation file, to be calculated in addition the mean that is normally calculated.

`-weightfile` weightfile.mnc  
Specify an output cumulative voxel weight file (default=none).

`-copy_header`  
Copy all of the additional header information from the first input file (default for one input file).

`-nocopy_header`  
Do not copy additional header information (default for many input files).

`-avgdim` dimname  
Specify the name of a dimension over which we should be averaging (or calculating standard deviation). If normalization is done, it still only applies to separate files only - no normalization is done within a file.

`-binarize`  
Binarize the input volumes before calculating the average. The binarization is done by specifying a range of values that contribute 1 to the average. Normalization of the input is not permitted when performing binarization.

`-binrange` min max  
Specify the range of values for binarization.

`-binvalue` value  
Specify a single legal value (integer) for binarization. The range is set to be +/- 0.5 around this value to achieve an effective rounding of input values.

`-ignore_below` value  
Do not include voxels below this value in the average and sd

`-ignore_above` value  
Do not include voxels above this value in the average and sd

`-floor` value  
Synonym for `-ignore_below`

`-ignore_above` value  
Synonym for `-ignore_above`

`-weights` `<w1,w2,...>  `
Specify a series of weights for averaging. The number of weighting values must match the number of input files and the values must be provided as a single argument with commas or spaces as separators. The sum of the weights must be non-zero. If weights are used with an averaging dimension, then only one input file can be specified.

`-width_weighted`  
This option can only be used when averaging across a dimension (`-avgdim` option). It specifies that weighting should be done using the width variable that corresponds to the averaging dimension. For example, using `-width_weighted` with `-avgdim` time will use the time-width variable to weight the values.

`-min_weight` value  
This specifies the minimum weight (number of volumes if no weights are specified) needed for calculating a valid average. If the cumulative weight for a voxel is below this threshold, the average and sd reported will be 0. This would typically be useful if values are excluded using any of the `-ignore` options, or by NaN values in the input volume(s).

`-min_weight_fraction` value  
Same as `-min_weight`, but specified as a fraction of the sum of the input weights (or the number of input volumes, if no weight is specified).

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin
