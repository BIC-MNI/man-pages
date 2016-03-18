---
---
# MINCSAMPLE

mincsample - generate samplings from minc files.
`mincsample <options> <in1.mnc> <in2.mnc> <..>`

## DESCRIPTION

*Mincsample* produces a data sampling on STDOUT from an input series of minc files. The output can be either ascii (-ascii) or as a raw binary stream of doubles (-double). The output data is ordered first by file then voxel. When -ascii is used the data values from each file are separated by a tab and the sampling points with a newline. When using -double, no separators are used.

If -coords is also specified, the world co-ordinate at each sampling point will precede the data from each of the files. An optional -outfile argument can also be used to direct the output to a file and -append used to append the data to the file as opposed to overwriting the file.

By default all data points are written out (-all) the output of points can also be constrained to be points within a mask (-mask and -mask\_val) and further by a random sampling of a sub-set of points via the -random\_samples and -random\_seed arguments

## OPTIONS

`-verbose`  
Print extra information during processing.

`-quiet`  
Print only the ouput sampling data.

`-clobber`  
Overwrite existing output files (when used with -outfile)

`-max_buffer` size  
Specify the maximum size of the internal buffers (in kbytes). Default is 4096 (4MB).

`-mask` mask.mnc  
Specify and input mask, only sampling points within this mask will be used.

`-mask_val` value  
Specify the value to use from the mask (Default: 1).

`-all`  
Sample all the data points.

`-random_seed` value  
Specify the random seed value to use during random sampling, this is to enable reproducible runs. If no seed is given a semi-random seed will be chosen (from time).

`-random_samples` value  
Specify the number of random samples to take from the input files. This value must be smaller than the maximum possible number of samples.

`-sample` sample.mnc  
Output a mask file that corresponds to where samples were taken from.

`-outfile` file  
Output sampling data to a file. (Default: STDOUT).

`-append`  
Append output data to an existing file.

`-ascii`  
Write out data as ascii strings (Default).

`-ascii`  
Write out data as double precision floating-point values.

`-coords`  
Write out world co-ordinates as well as sampling values.

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Andrew Janke and Mark Griffin

## COPYRIGHTS

Copyright © 2004 by Andrew Janke and Mark Griffin
