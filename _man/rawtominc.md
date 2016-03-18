---
---
# RAWTOMINC

rawtominc converts a stream of binary image data to a minc format file
`rawtominc options output.mnc sz4 sz3 sz2 sz1`

## DESCRIPTION


**Rawtominc** reads a stream of binary data (byte, short, long, float or double) 
from standard input (unless the `-input` option is used) and writes it into the 
minc format file `output.mnc`. The user specifies the dimension sizes from 
slowest varying to fastest varying. At least two dimensions must be given (an 
image) but there can be up to four. Options give the user control over dimension 
names, data types and voxel to world coordinate conversion. Vector type data 
(such as RGB pixel data) can be read in as well.

## PIXEL VALUE SPECIFICATION

Pixel values are specified by a type and a sign (e.g. signed short integer). 
They are also characterized by a range of legal values. For example, many 
scanners produce images stored with short integer pixel values. Some have values 
in the range 0 to 4095, others 0 to 32000, others -32768 to 32767. This range is 
the valid range, specified by the `-range` option (for floating point values, 
the valid range is the maximum and minimum of the whole dataset). *Rawtominc* 
allows the user to specify both the input type, sign and range as well as the 
output type, sign and range (read short values, store byte values, for example).

There is a further twist. Integer pixel values are generally taken to be simply 
scaled pixel representations of real (meaningful) physical values. Floating 
point values are taken to be the real value itself. Thus floating point values 
are scanned for the maximum and minimum, since they could be anything (they are 
stored in the MINC variables *image-max* and *image-min*). Integer values, 
however, are not scanned by default, since their range can be given by an 
option. To force scanning of integer values when the maximum and minimum are not 
known (some scanners produce files with variable ranges), use the option 
`-scan_range`.

## WORLD COORDINATES

World coordinates refer to millimetric coordinates relative to some physical 
origin (either the scanner or some anatomical structure). Voxel coordinates are 
simply the indices into the image volume of a given voxel. It is worth 
describing briefly how MINC coordinate conversions work since this will affect 
how successful the new MINC file will be.

Each dimension of MINC image is specified by name - the spatial dimensions are 
*xspace*, *yspace* and *zspace*. The convention is that positive *xspace* 
coordinates run from the patient's left side to right side, positive *yspace* 
coordinates run from patient posterior to anterior and positive *zspace* 
coordinates run from inferior to superior. For each of these spatial dimensions, 
the world coordinate conversion is specified by a pair of attributes: *step* and 
*start*. The *xspace* world coordinate, for example, is calculated using x = 
v\*step + start, where x is the x world coordinate and v is the voxel count 
(starting at zero). Thus the magnitude of the *step* attribute specifies the 
distance between voxels and the sign of the *step* attribute specifies the 
orientation of the axis. Programs will use this information to display images 
with the correct aspect ratio and orientation, so make sure that you get it 
right. Many scanners store transverse images with the first pixel at the 
patient's anterior/right side, so it would be necessary to give negative x and y 
step values. Other conventions have the opposite: first pixel at patient's 
posterior/left, so step values are positive. Sometimes the first slice is 
inferior, so the z step should be positive. Other times it is superior, so z 
step is negative.

The image axes do not have to be aligned with the world coordinate axes. The 
axis directions are recorded in the file as direction cosines - unit vectors - 
one for each spatial axis. In this case, the *step* and *start* attributes 
described in the previous paragraph refer to distances along the axis, not to 
coordinates of the first voxel. This makes them invariant under a change of axis 
direction (the whole coordinate system can in fact be rotated just by changing 
the direction cosines). If the coordinate of the first voxel is known, then it 
can be converted (projected) to a set of start values by using the `-origin` 
option.

## Dimension ordering

`-transverse`  
Transverse images : \[\[time\] z\] y x (Default)

`-sagittal`  
Sagittal images : \[\[time\] x\] z y

`-coronal`  
Coronal images : \[\[time\] y\] z x

`-time`  
Time ordered images : \[\[z\] time\] y x

`-xyz`  
Dimension order : \[\[time\] x\] y z

`-xzy`  
Dimension order : \[\[time\] x\] z y

`-yxz`  
Dimension order : \[\[time\] y\] x z

`-yzx`  
Dimension order : \[\[time\] y\] z x

`-zxy`  
Dimension order : \[\[time\] z\] x y

`-zyx`  
Dimension order : \[\[time\] z\] y x

`-dimorder` dim1,*dim2*\[,*dim3*\[,*dim4*\]\]  
Specify an arbitrary dimension order, given by an comma-separated list of between 2 and 4 dimension names.

`-vector` size  
Gives the size of a vector dimension (always the fastest varying dimension). Default is no vector dimension.

## Input data type and range

`-byte`  
8-bit integer values (default).

`-short`  
16-bit integer values.

`-int`  
32-bit integer values.

`-long`  
Superseded by `-int`.

`-float`  
Single-precision floating point values.

`-double`  
Double-precision floating point values.

`-signed`  
Values are signed integers (default for short and long). Ignored for floating point types.

`-unsigned`  
Values are unsigned integers (default for byte). Ignored for floating point types.

`-range` min *max*  
specifies the valid range of pixel values. Default is the full range for the type and sign. This option is ignored for floating point values.

`-real_range` min *max*  
specifies the real range of image values that corresponds to the pixel values of option `-range`. Default is to not store the real image minimum and maximum. If `-scan_range` is used, then the image minimum and maximum corresponding to the scanned pixel minimum and maximum are calculated and stored. This option is ignored for floating point values.

`-swap_bytes`  
Input values (either `-short` or `-int`) need to be converted between Motorola (big-endian) and Intel (little-endian) data format. If "short" input is specified, adjacent bytes are swapped. If "int" input is specified, inner and outer byte pairs are swapped. This option has no effect with other input types.

Output data type and range
==========================

`-obyte`  
Store 8-bit integer values (default is input type).

`-oshort`  
Store 16-bit integer values (default is input type).

`-oint`  
Store 32-bit integer values (default is input type).

`-olong`  
Superseded by `-oint`.

`-ofloat`  
Single-precision floating point values (default is input type).

`-odouble`  
Double-precision floating point values (default is input type).

`-osigned`  
Values are signed integers (default for short and long). Ignored for floating point types. If output type is not specified, then default is input sign type.

`-ounsigned`  
Values are unsigned integers (default for byte). Ignored for floating point types. If output type is not specified, then default is input sign type.

`-orange` min *max*  
specifies the valid range of pixel values. Default is the full range for the type and sign. This option is ignored for floating point values. If output type and sign are not specified, then the default is the input range.

## Scanning integers for range

`-noscan_range`  
Do not scan integer values for their minimum and maximum - assume that the -range option gives the appropriate range of pixel values (default). No rescaling of pixel values is done (unless the output type differs from the input type) and the created images are assumed to have a real (not pixel value) minimum and maximum of zero and one.

`-scan_range`  
Integer values are scanned for their minimum and maximum. Pixel values are rescaled to give the full range of pixel values and the real minimum and maximum are set to the pixel minimum and maximum (unless -real\_range is used). This should be equivalent to converting the input to a floating point type and reading it in with -float -oshort (for example) assuming that -real\_range is not used.

## Writing output file

`-2`  
Create MINC 2.0 format output files.

`-clobber`  
Overwrite existing minc file (default).

`-noclobber`  
Don't overwrite existing minc file.

## Reading from input file

`-input` inputfile  
Read input data from *inputfile* instead of standard input.

`-skip` length  
Skip the first *length* bytes of the input.

## World coordinate conversion

`-xstep` xstep  
Step size for x dimension (default = none).

`-ystep` ystep  
Step size for y dimension (default = none).

`-zstep` zstep  
Step size for z dimension (default = none).

`-xstart` xstart  
Starting coordinate for x dimension (default = none). This is a distance parallel to the axis.

`-ystart` ystart  
Starting coordinate for y dimension (default = none). This is a distance parallel to the axis.

`-zstart` zstart  
Starting coordinate for z dimension (default = none). This is a distance parallel to the axis.

`-xdircos` x1 *x2* *x3*  
Direction cosines for x dimension (default = none).

`-ydircos` y1 *y2* *y3*  
Direction cosines for y dimension (default = none).

`-zdircos` z1 *z2* *z3*  
Direction cosines for z dimension (default = none).

`-origin` o1 *o2* *o3*  
Specify the spatial coordinates of the first voxel. If the direction cosines are not given or are the default ones, this option will give the same results as using the -start options. Otherwise, the coordinate is projected parallel to the axes to determine the appropriate start values.

## Frame time and length specification

`-frame_times` t1,*t2*,*t3*,...  
Specify the start of each time frame. The number of values given must be equal to the length of the time dimension specified on the command line. All of the values given must be in one argument (no spaces between them, or the string must be quoted). Separation by spaces instead of commas is permitted.

`-frame_widths` w1,*w2*,*w3*,...  
Specify the length of each time frame. The comments for `-frame_times` apply here as well.

To set the start and step values for a functional file with a constant frame times, use the `-dattribute` flag described below as follows:

-dattribute time:step=1 -dattribute time:start=0

## Imaging modality

`-nomodality`  
Do not store modality type in file (default).

`-pet`  
PET data.

`-mri`  
MRI data.

`-spect`  
SPECT data.

`-gamma`  
Data from a gamma camera.

`-mrs`  
MR spectroscopy data.

`-mra`  
MR angiography data.

`-ct`  
CT data.

`-dsa`  
DSA data

`-dr`  
Digital radiography data.

## Attribute specification

`-sattribute` variable:*attribute*=*value*  
Specify that *variable* should be created with string *attribute* set to *value*. The complete specification, including *variable*, *attribute* and *value*, should be contained in only one argument to the program - quoting may be needed for strings containing blanks.

`-dattribute` variable:*attribute*=*value* :  
Like `-sattribute`, but for specifying double-precision attribute values.

`-attribute` variable:*attribute*=*value*  
Like `-sattribute` or `-dattribute`, except that the type is chosen by first trying to interpret the value as double precision - if that fails, then the value is assumed to be a string.

## Generic options

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin

## SEE ALSO
[minctoraw](minctoraw) [mincextract](mincextract)
