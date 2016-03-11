AUTOCROP
1
MNI AutoReg 0.98
10/Sep/97
autocrop
tool for extracting and manipulating bounds of a MINC file
autocrop
options
in\_volume
out\_volume
autocrop
options
in\_volume
(The
first
form
applies
by
default,
or
if
options
includes
an
explicit
-resample
or
-reshape.
The
second
form
only
applies
if
options
includes
-noresample
or
-noreshape.)
DESCRIPTION
===========

HeaderDESCRIPTION `autocrop` is a tool for specifying and manipulating the bounds of a MINC file, where the *bounds* are defined as the *start* and *extent* of the volume in each dimension. Start and extent are both always defined in world coordinates, and given in millimetres. The bounds of a volume can be extracted from any MINC file, or from a specially-formatted tag file, or from the already-known volume covered by the brain in Talairach space. Operations that can be performed on these bounds include spatial transformations and various ways of increasing/decreasing the extent of the sampling volume in the three spatial dimensions.

`autocrop` uses either of *mincresample* or *mincreshape* for the actual processing of data. You can force it to use one or the other, or let it pick the appropriate one. (It will always pick mincreshape, unless you have asked for a different step size in your output volume. Also, if you attempt to force use of mincreshape and have asked for different steps, autocrop will complain and die.) Also, you can make autocrop simply print out command line options for one of the two utilities, and apply them later at your leisure.

OPTIONS
=======

HeaderOPTIONS This section is provided for quick reference once you know the rest of this man page cold. You'll probably want to skip it on a first reading. (Also, you can always get an up-to-date version of this option summary with the command *autocrop -help*.)

Basic behaviour options
-----------------------

SubsectionBasic behaviour options

-verbose print status information and command lines of subprograms \[default; opposite is -quiet\] -execute actually execute planned commands \[default\] -clobber blithely overwrite files (and make subprograms do as well) \[default: -noclobber\] -debug spew lots of debugging info (and make subprograms do so as well) \[default: -nodebug\] -tmpdir set the temporary working directory -keeptmp don't delete temporary files when finished \[default: -nokeeptmp\] </literallayout>Ve
SubsectionAction-to-take options

-resample force autocrop to use mincresample, and also ensure that resampling is actually performed -noresample don't actually do anything, but compute parameters for mincresample -reshape force autocrop to use mincreshape if possible, and also ensure that reshaping is actually performed -noreshape don't actually do anything, but compute parameters for mincreshape -params print out parameters to run mincresample/mincreshape \[default: on if not running them, -noparams otherwise\] </literallayout>Ve
Bounds specification options
----------------------------

SubsectionBounds specification options

-from <file> take the bounds from <file> (either a tag or MINC file) \[default: input volume\] -bbox <file> compute the bounding box of the data in <file>, and use that for the bounds -bbox\_threshold threshold value to use when running mincbbox \[default: 0\] -talairach take the bounds from the (approximate) extent of the brain in Talairach space </literallayout>Ve
SubsectionBounds transformation options

-transform <xfm> apply <xfm> to the bounds to get them into the space of the input volume -invert invert the <xfm> supplied with -transform before applying it </literallayout>Ve
Bounds modification options
---------------------------

SubsectionBounds modification options

-expand set the (x,y,z) expansion (increase volume extent symmetrically at each end of an axis) parameters -isoexpand set the same expansion parameter for all three axes -extend set the (x,y,z) extension (increase volume extent independently at each end of an axis) parameters -isoextend set the same extension parameter for all three axes </literallayout>Ve
SubsectionResampling options

-step <xstep> <ystep> <zstep>
set the x, y, and z step (voxel size) for the output sampling -isostep set the step (same in all three dimensions) for the output sampling </literallayout>Ve
HeaderACTION TAKEN With no options, `autocrop` is simply a front-end to *mincreshape*; the two commands

autocrop foo.mnc bar.mnc mincreshape foo.mnc bar.mnc </literallayout>Ve
are equivalent. However, you can force `autocrop` to use *mincresample* with the `-resample` option:

autocrop -resample foo.mnc bar.mnc </literallayout>Ve
Or, you can tell it to merely think about using mincreshape or mincresample with the `-noreshape` and `-noresample` options. Each of these has several side effects: they tell `autocrop` to not actually perform the desired crop, but merely to print out the arguments for whichever program is implied by the option. For instance,

autocrop -noresample foo.mnc </literallayout>Ve
would print out the part of a *mincresample* command-line that specifies the same sampling grid as found in *foo.mnc*. (Of course, the whole point of `autocrop` is to change that sampling grid in some way. That bit comes later.) For example, a typical PET volume at the MNI has 128x128x15 (x,y,z) voxels, with steps of 2mm, 2mm, and 6.5mm. For concreteness, assume the start coordinates for a given volume are (0,0,-7.9). Then the extent of this volume is (256mm,256mm,97.5mm), and the command

autocrop -noresample foo.mnc </literallayout>Ve
would print out

-start 0 0 -7.9 -step 2 2 6.5 -nelements 128 128 15 </literallayout>Ve
while

autocrop -noreshape foo.mnc </literallayout>Ve
would give you

-start 0,0,0 -count 15,128,128 </literallayout>Ve
Note that the parameters are specified to *mincresample* in canonical x,y,z order; for *mincreshape*, though, the parameters are reordered according to the volume at hand. In this case, the volume is transverse, so the dimensions are z,y,x.

Another minor point about the `-noresample` and `-noreshape` options: if you want to use their output in another program, you'll most likely either redirect `autocrop`'s output to a file, or open a pipe to read its output. In either case, `autocrop` does not print a newline at the end of the mincresample/mincreshape arguments, like it does when output is to a terminal. This is often convenient.

One important option that deserves mention here (because I couldn't think of where else to put it) is `-step`. Although the step size isn't strictly part of the volume bounds, it is certainly relevant when resampling data, and can be relevant when reshaping data. (For instance, if any step is changed by more than a sign, you can't use mincreshape!)

As a simple example, let's say you want to change the direction of sampling in the *z* axis. In this case, you simply supply `-step` with the desired new steps:

autocrop foo.mnc foo\_negative\_z.mnc -step 2 2 -6.5 </literallayout>Ve
(Yes, you have to know the old steps in order to supply the new ones in this case.) In this case, `autocrop` is smart enough to use mincreshape for the reordering.

Another possibility is that you might want to resample a volume to have isotropic voxel sizes---say, 2x2x2mm. This can be done as follows:

autocrop foo.mnc foo\_cubic.mnc -step 2 2 2 </literallayout>Ve
In this case, of course, `autocrop` must use mincresample. A handy shortcut option exists for the case of isotropic sampling: `-isostep`. You can save a few keystrokes on the above command with this:

autocrop foo.mnc foo\_cubic.mnc -isostep 2 </literallayout>Ve
BOUNDS SPECIFICATION
====================

HeaderBOUNDS SPECIFICATION Six numbers are necessary to specify the bounds of a three-dimensional volume (unfortunately, `autocrop` is rather prejudiced towards working with 3-D data): the start and extent in each of the *x*, *y*, and *z* dimensions. The LDQUOstartRDQUO parameters are just what you think from previous MINC experience: (start\_x,start\_y,start\_z) is the real-world coordinate for the first voxel in the volume. The LDQUOextentRDQUO of a dimension is simply the step (voxel size) multiplied by the LDQUOlengthRDQUO or LDQUOcountRDQUO (number of voxels).

Note that both the start and extent are sensitive to the sign of the step: for instance, if data is sampled left-to-right, then the *x* step and extent will both be positive, and the start will be the *smallest* *x*-coordinate. However, if data is sampled right-to-left, the *x* step and extent will be negative, and the start will be the largest *x*-coordinate. Similarly, posterior-to-anterior (back-to-front, for the Latin-challenged) sampling implies positive *y* step and extent, and inferior-to-superior (bottom-to-top) sampling implies positive *z* step. This doesn't really concern you when specifying the bounds of a volume, but it's handy to keep in mind.

Obviously, it's easy to extract the bounds of a volume straight from a MINC file. In fact, `autocrop`'s default mode is to take the start and extent straight from the input volume, which makes perfect sense most of the time. However, you can also take the bounds from another MINC file, from the data in another MINC file, or from a tag file that follows a convention explained below.

First, consider a possible scenario in which you would want the bounds from one volume to apply to another. One example is a label volume that covers only a fraction of the brain, where you want to extract only the MRI image data that corresponds to the labels. Let's say the image data is in *smith\_john\_mri.mnc*, and structure *foobar* has been painted with the labels saved in *smith\_john\_foobar.mnc*. (This label volume should be tightly cropped to encompass only the structure of interest. Recent versions of *Display* do this automatically.) Then you could crop the image data down to the size of the structure like this:

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -from smith\_john\_foobar.mnc </literallayout>Ve
Too easy, eh? If that's not good enough, you can even tell `autocrop` to do things like add five voxels at one end of the *x* dimension, or increase the volume by 5% all the way around. (But that's covered later, when we get to bounds modifiers.)

Now, what if the label volume is *not* tightly cropped to the structure of interest? In that case, you don't want `autocrop` to take the sampling limits of the whole volume; rather, you're interested in the limits of the data. This can be done with the `-bbox` option; for instance:

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -bbox smith\_john\_foobar.mnc </literallayout>Ve
would compute the bounding box of the data in *smith\_john\_foobar.mnc*, and use that to crop the input MRI file. If you want to compute the bounding box of a non-label volume (i.e. something with a noise floor), you can use `-bbox_threshold` to specify an absolute (real-world) voxel value to use as the cut-off for considering a voxel as LDQUOinteresting dataRDQUO.

Another possibility is that you don't have the bounds you want encoded in a handy MINC file; you want to set the start and extent explicitly for each dimension. This can be done by supplying a tag file to the -from option, e.g.

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -from mybounds.tag </literallayout>Ve
(Note that `autocrop` distinguishes between MINC and tag files solely by their filename, so you are advised to stick to the standard file naming conventions!) The tag file must have eight points, each of which is one corner of the volume's bounding box. You might think it would be easier and more sensible to specify just six points, such as the extrema of each axis within the volume. However, doing that leads to problems when the bounds are transformed with large rotations -- corners of the volume tend to get chopped off.

As an example, a typical PET file from the MNI has spatial parameters like this (courtesy of mincinfo):

dimension name length step start -------------- ------ ---- ----- zspace 15 6.5 -7.9 yspace 128 2 0 xspace 128 2 0 </literallayout>Ve
The bounds of this volume could be described as three ordered pairs (start and extent in x,y,z order): (0,256) (0,256) (-7.9,97.5). A tag file describing these bounds would look like this:

MNI Tag Point File Volumes = 1; Points = 0 0 -7.9 "" 0 256 -7.9 "" 0 0 89.6 "" 0 256 89.6 "" 256 0 -7.9 "" 256 256 -7.9 "" 256 0 89.6 "" 256 256 89.6 ""; </literallayout>Ve
It should be pretty clear that these eight points describe the rectangular volume taken from the MINC file. (If not, draw it!)

There's one final way to specify the bounds of a volume: `-talairach`. As the name implies, this option uses a set of hard-coded points in Talairach space that define the volume encompassing the brain and scalp. This volume is from *x*=-80..+80, *y*=-120..+90, and *z*=-80..+95, and was selected by someone (your humble narrator) who has zero formal knowledge of neuroanatomy. (Just so you know.) This option is often useful in conjunction with bounds transformations, which are illuminated below.

BOUNDS TRANSFORMATION
=====================

HeaderBOUNDS TRANSFORMATION Now that you have a bounding box for your data, presumably you want to change it in some way. The first is with a spatial transformation---for instance, your bounds might be in Talairach space, but you wish to apply them to data in native space. (For the historically minded, this was in fact the original impetus for `autocrop`, before it became the feature-laden behemoth you now find before you.)

As a concrete example, let's say we have an MRI volume in *smith\_john\_mri.mnc*, the transformation to get it into Talairach space in *smith\_john\_mrital.xfm*, and a tightly-cropped mask of the brain in Talairach space in *average305\_t1\_tal\_lin\_mask.mnc*. We wish to crop the native MRI volume using the extent of the brain, but first we need to transform the information about that extent back to native space. This can be done using `autocrop`'s `-transform` option, along with the `-invert` flag (because we're supplying the native-to-Talairach transform, not Talairach-to-native):

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -from average305\_t1\_tal\_lin\_mask.mnc BSOL -transform smith\_john\_mrital.xfm -invert </literallayout>Ve
(If you happen to have the Talairach-to-native transform handy, you can drop the `-invert` flag.)

As an aside, this is a great place to use the `-talairach` flag instead of supplying an explicit label volume from which to extract the bounding box. The advantages of `-talairach` are that you get the same bounds every time, those bounds are symmetric about *x* and easily reproducible, you don't need a tightly-cropped label volume, and you don't have to type as much. The disadvantage is that you're implicitly trusting one particular guess (mine) at the spatial extent of the brain+scalp in Talairach space.

BOUNDS MODIFICATION
===================

HeaderBOUNDS MODIFICATION Once you have your bounds in the desired space (either through a spatial transformation, or through not doing anything at all), you'll probably want to tweak them a little bit. Let's return to the example of cropping an MRI volume according to the bounds of a labelled structure. If you just do this:

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -from smith\_john\_foobar.mnc </literallayout>Ve
then you've thrown away all MRI data outside the bounding box of the labelled structure. If this is a small volume, then you've probably cropped way too much and lost any useful anatomical context. In this case, you probably want to expand the bounds by a little bit all the way around, say 10%. This is easily done with the `-expand` option (or rather, its shortcut `-isoexpand`):

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -from smith\_john\_foobar.mnc -isoexpand 10% </literallayout>Ve
(Not surprisingly, *-isoexpand 10%* is a shortcut for *-expand 10% 10% 10%*.) *Expanding* a dimension increases the amount of space covered by an equal amount at either end of the dimension. For instance, if the *x* dimension covers 200mm from *x*=0..+200, then expanding it by 10% will decrease the start by 20mm (10% of 200mm), and increase the extent by 40mm (20mm to actually extend the dimension, and 20mm to make up for the decrease in the start coordinate.)

Note that asking for a 10% expansion results in the dimension's extent actually being increased by 20%. This is a feature---it's just because LDQUOexpand by *x*RDQUO means LDQUOexpand by *x* at each end of the dimensionRDQUO.

Expansion factors can be also specified in millimetres or voxels; just append LDQUOmmRDQUO or LDQUOvRDQUO in place of LDQUO%RDQUO. If no unit is specifed, millimetres are used. Note that a percentage is always a percentage of the dimension's extent in *world* coordinates, not of the number of samples in that dimension. Also, expansion factors may be negative; this will cause the dimension to be reduced by the given amount at both ends.

Now, let's say you want to change the amount of space covered by a dimension differently at the two ends. This is called, for want of a better word, dimension extension. Extension factors look a lot like expansion factors, except there have to be two of them for each dimension: the first covers the LDQUOlowRDQUO end of an axis, and the second covers the LDQUOhighRDQUO end. Low and high here are in the world coordinate sense, so LDQUOlow xRDQUO is patient left, LDQUOlow yRDQUO is patient posterior, and LDQUOlow zRDQUO is patient superior, independent of the sampling direction.

A very real world example is the need to chop off the bottom of a volume before registration. This is common with MRI data that is acquired coronally or sagitally; typically, the *z* extent in these cases is 256mm, which extends well into the neck. If this data is not removed, automatic registration to a model brain can be very dodgy indeed. Also, removing a chunk of unneeded data is a big win for processing time and space. For example, to remove 25% of the data at the low end of the *z* axis:

autocrop smith\_john\_mri.mnc smith\_john\_crop.mnc BSOL -extend 0,0 0,0 -25%,0 </literallayout>Ve
Note that we have supplied separate extension pairs for each dimension, but that the extensions to *x* and *y* don't do anything. For *z*, the negative extension factor means to remove data---25% of it, to be specific. At the high end of the *z* axis, we do nothing. (If your MRI data consistently has >5mm of empty space, you might save a little more time and space by shaving this off with *-extend 0,0 0,0 -25%,-5mm*. Note the nifty mixing of units in one extension pair; this is perfectly legal and conceivably useful.)

MORE EXAMPLES
=============

HeaderMORE EXAMPLES (Nothing yet.)

SEE ALSO
========

HeaderSEE ALSO mincresample, mincreshape

AUTHOR
======

HeaderAUTHOR Greg Ward, <greg@bic.mni.mcgill.ca>; inspired by the needs of fully-automated MRI-PET and MRI-Talairach registration. (Hence see also *mritotal* and *mritopet* (which doesn't actually have a man page yet).)

AVAILABILITY
============

HeaderAVAILABILITY Currently part of the MNI AutoReg package, available from

http://packages.bic.mni.mcgill.ca/
</literallayout>Ve
COPYRIGHT
=========

HeaderCOPYRIGHT Copyright (c) 1994-96 Greg Ward, McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University. Permission to use, copy, modify, and distribute this software and its documentation for any purpose and without fee is hereby granted, provided that the above copyright notice appear in all copies. The author and McGill University make no representations about the suitability of this software for any purpose. It is provided LDQUOas isRDQUO without express or implied warranty.

Note that the programs mincreshape and mincresample are written and copyrighted by Peter Neelin, McConnell Brain Imaging Centre, with the same terms as above.
