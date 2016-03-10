MINCMAKESCALAR
1
$Date: 2004-05-20 21:52:08 $
mincmakescalar
convert vector minc files to scalar
mincmakescalar
&lt;options&gt;
&lt;in&gt;.mnc
&lt;out&gt;.mnc
DESCRIPTION
===========

*Mincmakescalar* converts vector minc files to scalar minc files. A vector minc file is one that contains the dimension *vector\_dimension* as the fastest varying dimension of the image data and represents vector data at each voxel such as RGB images or gradient volumes. A scalar minc file does not contain the vector dimension and represents grayscale or intensity data.

A variety of conversion schemes are possible. The simplest is an average of the components of the vector. The magnitude of the vector at each voxel can also be computed. RGB volumes can be converted to greyscale by a standard linear combination. Finally, the user can supply a list of coefficients for a linear combination of vector components.

Some options will require a specific number of components on the input vectors (RGB data should have 3 components and the number of coefficients supplied for the linear combination should match the number of components on the input vectors), but the program will also accept input scalar data and will copy it through without modification.

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

General options
===============

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

Conversion options
==================

`-magnitude`  
Compute the magnitude of each vector (default).

`-average`  
Compute the average of the components of each vector.

`-rgbtogrey`  
Convert RGB (3-component) files to greyscale using a linear combination with standard set of weighting coefficients.

`-rgbtogray`  
Synonym for `-rgbtogrey`.

`-linear` c1,c2,c3,...  
Compute a linear combination of the components of each vector using the specified coefficients (these weights must be given as a comma or space-separated list of numbers in a single command-line argument). The number of coefficients must match the number of components on the input vectors.

Generic options for all commands:
=================================

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

EXAMPLES
========

To convert an RGB file to an grayscale file:

mincmakescalar -rgbtogrey rgb.mnc gray.mnc

To compute the gradient magnitude from a gradient volume

mincmakescalar -magnitude gradient.mnc magnitude.mnc

To convert an RGB file to a grayscale file using a different set of weighting factors for red, green and blue:

mincmakescalar -linear '0.2,0.5,0.3' rgb.mnc gray.mnc

AUTHOR
======

Peter Neelin

COPYRIGHTS
==========

Copyright © 1997 by Peter Neelin
