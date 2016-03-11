# MINCRESAMPLE

**mincresample** resamples a minc file along new spatial dimensions

`mincresample <options> <infile> <outfile>`

## DESCRIPTION

**mincresample** will resample a minc file along new spatial dimensions with new 
voxel positions. Each volume in the input file (given by the spatial dimensions 
xspace, yspace and zspace) is resampled according to the command-line options. 
Non-spatial dimensions are preserved in their original order, but spatial 
dimensions can be re-ordered to give transverse, sagittal or coronal images. The 
new voxel values are calculated using tri-linear, tri-cubic or nearest-neighbour 
interpolation.

## WORLD COORDINATES

World coordinates refer to millimetric coordinates relative to some physical 
origin (either the scanner or some anatomical structure). Voxel coordinates are 
simply the indices into the image volume of a given voxel. In order to specify 
appropriate resampling options, it is necessary to understand how MINC 
coordinate conversions work.
Each dimension of a MINC image volume is specified by name - the spatial 
dimensions are xspace, yspace and zspace. The convention is that positive xspace 
coordinates run from the patient's left side to right side, positive yspace 
coordinates run from patient posterior to anterior and positive zspace 
coordinates run from inferior to superior. For each of these spatial dimensions, 
the world coordinate conversion is specified by a pair of attributes: step and 
start. The xspace world coordinate, for example is calculated using x = v\*step 
+ start, where x is the x world coordinate and v is the voxel count (starting at 
zero). Thus the magnitude of the step attribute specifies the distance between 
voxels and the sign of the step attribute specifies the orientation of the axis.
There is a further twist: MINC files are allowed to have non-orthogonal axes 
with the dimensions not perfectly aligned with the named axis. There can be a 
direction\_cosine attribute that gives the true orientation of the axis. For 
example, normally the xspace dimension should line up with the world x axis, ie. 
direction cosine = (1,0,0); however, it is possible to have a direction cosine 
of (0.9, 0.43589, 0).
These attributes (step, start and direction\_cosines) provide a conversion from 
voxel coordinates to world coordinates. Combined with a number of elements or 
samples along an axis, they provide a complete description of where the output 
sampling should be. However, when we are resampling data, we are frequently 
interested in a change of world coordinates: from an MRI scanner's coordinate 
system to a PET scanner's coordinate system, for example, or from a volume in 
its acquisition space to coordinates in a standardized space. This change of 
world coordinates can be specified through the use of a transformation (.xfm) 
file. Thus, in general, the resampling involves three transformations: from the 
input file's voxel coordinates to its world coordinates (specified by the input 
file), from the input world coordinates to the output world coordinates 
(specified by the transformation file), and from the output file's world 
coordinates to its voxel coordinates (specified by command-line options).
In general, direction cosines are rarely used - axis re-orientation is specified 
by a change of world coordinates (the transformation file). As well, resampling 
positions (output world to voxel conversion) are often specified relative to a 
model file (ie. resample this file so that it looks like that file). Although 
there are many options for a complete specification of the transformation, one 
does not usually need to specify more than a few of them.

## OPTIONS


Note that options can be specified in abbreviated form (as long as they are 
unique) and can be given anywhere on the command line.

## General options


`-2`  
Create MINC 2.0 format output files.

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-verbose`  
Print out progress information for each slice computed (default).

`-quiet`  
Do not print out progress information.

## Resampling specification

Options that give the output sampling (all of the following except 
`-transformation`) are parsed in the order that they appear on the command line. 
Thus a command with `-like file.mnc -znelements 34 -zstep 2` will give a sampling like that in file in *file.mnc* but with 34 
samples at 2 mm along the *zspace* axis. The default sampling is taken from the 
input file, transformed according to any transformation.

`-transformation` file.xfm  
Specify a file giving the world coordinate transformation (default is the 
identity transformation).

`-invert_transformation`  
Invert the transformation before using it.

`-noinvert_transformation`  
Do no invert the transformation (default).

`-tfm_input_sampling`  
Transform the input sampling (using the transform specified by 
`-transformation`) along with the data and use this as the default sampling 
(default).

`-use_input_sampling`  
Use the input sampling as the default sampling, as is, without transformation, 
even though the data is being transformed (old behaviour).

`-like` file.mnc  
Specify a model file that gives the output world to voxel transformation and 
number of elements (ie. transform this file so that it looks like that one).

`-standard_sampling`  
Set the sampling to standard values (start = 0, step = 1, direction cosines 
point along appropriate axes).

`-spacetype` string  
Set the name of the output space (usually *native\_\_\_\_* or *talairach\_*).

`-talairach`  
Set the name of the output space to talairach\_.

`-units` string  
Set the units of the output space.

`-origin` ox oy oz  
Specify the coordinate of the first voxel. This is not the same as the start 
value if the direction cosines are non-standard. As well, the start is not just 
a perpendicular projection of the origin onto the axis, it is a parallel 
projection (as in a multi-dimensional parallelogram projection). The conversion 
is handled properly by this option.

`-nelements` nx ny nz  
Number of elements along each of the world dimensions.

`-xnelements` nx  
Number of elements along the xspace dimension.

`-ynelements` ny  
Number of elements along the yspace dimension.

`-znelements` nz  
Number of elements along the zspace dimension.

`-step` xstep ystep zstep  
Step between voxels along each of the world dimensions.

`-xstep` xstep  
Step between voxels along the xspace dimension.

`-ystep` ystep  
Step between voxels along the yspace dimension.

`-zstep` zstep  
Step between voxels along the zspace dimension.

`-start` xstart ystart zstart  
Position of centre of first voxel along each of the world dimensions.

`-xstart` xstart  
Position of centre of first voxel along the xspace dimension.

`-ystart` ystart  
Position of centre of first voxel along the yspace dimension.

`-zstart` zstart  
Position of centre of first voxel along the zspace dimension.

`-dircos` x1 x2 x3 y1 y2 y3 z1 z2 z3  
Direction cosines for each of the world axes.

`-xdircos` x1 x2 x3  
Direction cosines for the xspace dimension.

`-ydircos` y1 y2 y3  
Direction cosines for the yspace dimension.

`-zdircos` z1 z2 z3  
Direction cosines for the zspace dimension.

## Dimension ordering


The default is to preserve the original dimension order.

`-transverse`  
Write out transverse slices.

`-sagittal`  
Write out sagittal slices.

`-coronal`  
Write out coronal slices.

## Output data type and range


The default for type, sign and valid range is to use those of the input file. If 
type is specified, then both sign and valid range are set to the default for 
that type. If sign is specified, then valid range is set to the default for the 
type and sign.

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
Write out values as signed integers (default for short and long). Ignored for 
floating point types.

`-unsigned`  
Write out values as unsigned integers (default for byte). Ignored for floating 
point types.

`-range` min max  
specifies the valid range of output voxel values. Default is the full range for 
the type and sign. This option is ignored for floating point values.

`-keep_real_range`  
Preserve the real minimum and maximum from the input volume, so that values are 
scaled in the same way on output. This is particularly useful for resampling 
label volumes where interpolating intensity values does not make sense.

`-nokeep_real_range`  
Recompute the real minimum and maximum for each output slice. This is the 
default.

## Handling of undefined (invalid) voxel values


`-fill`  
Output voxels that fall outside of the input volume have undefined values. When 
the `-fill` option is used, these voxels are given a value that is outside of 
the valid range (less than the valid minimum, if the type, sign and valid range 
permit) so that they can be detected by other software. The values of these 
voxels are not included in the *image-max* and *image-min* variables.

`-nofill`  
Use a real/physical value (not voxel value) of zero for points outside of the 
input volume. These points are included in the calculation of the *image-max* 
and *image-min* variables. This is the default.

`-fillvalue` fillvalue  
Specifies a real/physical value (not voxel value) for points outside of the 
input volume. The points are not included in the calculation of the *image-max* 
and *image-min* variables.

## Interpolation options


`-trilinear`  
Do a tri-linear interpolation between voxels. The edges of the volume are at the 
centre of the first and last voxels of a dimension. This is the default.

`-tricubic`  
Do a tri-cubic interpolation between voxels. The edges of the volume are at the 
centre of the first and last voxels of a dimension.

`-nearest_neighbour`  
Do nearest neighbour interpolation between voxels (ie. find the voxel closest to 
the point and use its value). The edges of the volume are at the edge of the 
first and last voxels of a dimension (centre +/- half voxel separation).

`-sinc`  
Do renormalized windowed-sinc interpolation between voxels, as described by 
Thacker et al. JMRI 10:582-588 (1999).

`-width` n  
Specifies the half-width of the sinc interpolation kernel, in the range from 1 
to 10. The full sinc kernel width is *n* \* 2 + 1, and therefore varies from 3 
to 21. The default value is 5 giving a full-width of 11.

`-hanning`  
Use a Hanning window with the sinc interpolant. This is the default.

`-hamming`  
Use a Hamming window with the sinc interpolant.

## Generic options

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES

Resample an individual's brain in a standardized space on a standard sampling 
grid:

mincresample individual.mnc in\_std\_space.mnc BSOL -transform 
transform\_to\_standard\_space.xfm BSOL -like standard\_sampling.mnc

Resample an MRI volume to be matched with a PET volume, but with finer 
resolution:

mincresample mri.mnc mri\_resampled.mnc BSOL -transform mri\_to\_pet.xfm -like 
pet.mnc BSOL -step 1 1 2 -xstart -0.5 -ystart -0.5 BSOL -nelements 256 256 64

Turn a transverse volume into a sagittal volume:

mincresample transverse.mnc sagittal.mnc BSOL -sagittal -nearest

Turn a 256x256x64 (1x1x2mm) transverse volume into 256x128x256 (1x1x1mm) 
sagittal volume:

mincresample transverse.mnc sagittal.mnc -sagittal BSOL -zstep 1 -znelem 128

Get a finer axial sampling on a PET volume:

mincresample pet\_15\_slices.mnc pet\_46\_slices.mnc BSOL -zstep 2 -znelements 
46

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin

## SEE ALSO

[mincreshape]
