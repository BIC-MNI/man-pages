MRITOTAL
1
MNI\_AutoReg
mritotal
performs multi-scale fitting of a normal human brain to a standard model
mritotal
options
&lt;source&gt;
&lt;output&gt;
mritotal
-help
Options can come in any order, be intermixed with the required arguments, and be abbreviated as long as they are not ambiguous.

DESCRIPTION
===========

`mritotal` registers the T1-weighted MRI image volume for a single normal human brain to a standard atlas space using a multi-scale method \[1\]. Usually, the atlas is defined by the average of many T1-weighted MRI volumes independantly registered to a stereotaxic coordinate system such as Talairach space \[2,3\]. (Such an atlas, based on the MNI 305 Average Brain, should already be installed on your system if mritotal is available.) However, mritotal is flexible enough to allow fitting to a model in any space, although the model must be preconstructed. For example, the construction of an average of T2-weighted MRI data in Talairach space would allow fitting of T2-weighted data to Talairach space.

mritotal has only two required arguments: the input volume and the output transform file. Note that mritotal does *not* output a new image volume; you must use mincresample to create a new MINC volume using the transform output by mritotal if you wish to visually inspect the registration.

mritotal has two main stages: preprocessing and fitting. The preprocessing consists of subsampling, cropping, and blurring the input volume. (The capability to perform intensity clamping is also there, but it's not enabled in the current release.) Because the preprocessing steps are somewhat data dependent, mritotal provides a number of options to customize the procedure for your data (see the PREPROCESSING section. below). Also, mritotal provides a mechanism called *protocol files* whereby you can permanently specify the set of preprocessing steps needed for your particular data. This too is covered below, in the CONFIGURATION AND PROTOCOL FILES section.

Fitting consists of a series of optimizations performed on progressively less blurred data, with each fit initialized by the results of the previous fit. See the FITTING ALGORITHM section below for complete information. In the current release, the sequence of fits is not controllable by the user, although the program is structured such that a reasonably knowledgable Perl programmer could customize the fitting procedure if necessary.

Options may be abbreviated as long as they are not ambiguous; the full list of options may be had at any time by running "mritotal -help". The options governing preprocessing (subsampling, cropping, and -- eventually -- clamping) are covered under the PREPROCESSING section below; here are all the others:

*Site-Specific Options*

These options can also be set in the configuration file (/usr/local/etc/mni\_autoreg/mritotal.cfg). In fact, system-wide defaults should be set there by the installer of the MNI Auto Registration Package. That way, most users will never have to worry about the -model or -protocol options. See the CONFIGURATION AND PROTOCOL FILES section below for full information.

-modeldir &lt;dir&gt;  
Tells mritotal the default directory to search for model files. That way, you can just put all model files in one directory, and refer to them by supplying just the basename to the "-model" option.

-model &lt;basename&gt;  
Tells mritotal the base filename of the model files to use for fitting. For instance, the default model files (available as mni-models\_average305-lin-1.1.tar.gz) are average305\_t1\_tal\_lin.mnc, average305\_t1\_tal\_lin\_16\_blur.mnc, average305\_t1\_tal\_lin\_\_8\_blur.mnc, and others... It makes sense to install these all in the same directory (specified with -modeldir), and just use "-model average305\_t1\_tal\_li" to pick these model files. (Of course, this particular example is not necessary -- mritotal's built-in default is to look for the average305\_t1\_tal\_lin model files. -model is only needed if you wish to use an alternate set of model files.) Note that if the base filename specified by -model starts with a "/" (i.e., it's an absolute path), then the directory specified by -modeldir is ignored.

-protocol &lt;protocol&gt;  
Tells mritotal what "protocol" to use for preprocessing. This is done by loading a specially named file, e.g. "mritotal.foo.cfg" for protocol "foo". Protocol files are explained in the CONFIGURATION AND PROTOCOL FILES section below.

*User Preferences*

These options can also be set in the configuration file.

-verbose (default; opposite is -quiet)  
Display status information and print out every command executed. It is strongly recommended that you log the output of mritotal to a file, rather than silencing it with -quiet.

-execute (default; opposite is -noexecute)  
Actually execute the commands needed to perform the fit. -noexecute is there mainly for debugging.

-clobber (default is -noclobber)  
Overwrite the output file (and tell mincblur and minctracc to clobber their output files).

-debug (default is -nodebug)  
Print lots of debugging output. (This doesn't actually change what mritotal prints out, only what minctracc and mincblur print out.)

-tmpdir &lt;dir&gt;  
Change the directory used by mritotal for temporary files. Note that this directory (and everything in it) will be deleted when mritotal finishes, unless you also use the -keeptmp option.

-keeptmp (default is -nokeeptmp)  
Don't delete the temporary directory when done.

*Data-Specific Options*

These consist of the pre-processing options (-nosubsample, -guess\_subsample, -isosubsample, -subsample, and similar options for cropping -- described in the PREPROCESSING section below), as well as:

-linear  
Choose linear mode of operation. This is the default.

-nonlinear  
Choose the nonlinear mode of operation.

-objective &lt;obj&gt; (default: xcorr)  
Specify the objective function to use for fitting in linear steps. You can use any of the objective functions supported by minctracc (do "minctracc -help" for an up-to-date list); currently, these are:

xcorr cross-correlation mi mutual information \[Collignon\] vr variance of ratios \[Woods\] zscore normalized difference ssc stochasic sign change

Only cross-correlation has been thoroughly tested and routinely used for fitting MRI data to Talairach space with mritotal.

-firstobj &lt;obj&gt; (default: none)  
Specify the objective function to use for the first fit only. The default is just to use the main objective, as specified by -objective.

-startlevel &lt;level&gt;  
In nonlinear mode, specify the level of detail to begin at. The default is to begin at level 16 (i.e. 16mm blur).

-stoplevel &lt;level&gt;  
In nonlinear mode, specify the level of detail to stop at. The default is level 8 (i.e. 8mm blur).

*Other Options*

These options can only be specified on the command line.

-transformation &lt;xfmfile&gt;  
Use the specified transformation file to initialize the fit. If this option is used, mritotal will skip the first several fitting steps (except using principal axes to determine the "centre of gravity" of the input volume; this is still needed for the centre of rotations and scales.) In particular, fitting will start with the first full nine-parameter fit. This is particularly useful when dealing with slightly abnormal anatomy; in these cases, the fully automated method may fail, whereas a rough manual registration can be performed to "seed" the last few steps of the automated registration.

PREPROCESSING
=============

Subsampling of the data is done solely to save time and memory; if you are worried about aliasing problems or desire the utmost accuracy, you can disable it (but make sure you have a *lot* of memory to spare for the blurring steps). The options that control subsampling are:

-nosubsample  
Disable subsampling.

-guess\_subsample (default)  
Use a simple heuristic to determine the new sampling frequency for the data. In particular, mritotal subsamples any dimension with a step size of less than 1.5 mm by halving the sampling frequency (or doubling the step) in that dimension.

-isosubsample &lt;step&gt;  
Subsample all three spatial dimensions using the same step size.

-subsample &lt;xstep&gt; &lt;ystep&gt; &lt;zstep&gt;  
Subsample the three spatial dimensions independantly, using the specified step size.

The options that control cropping are quite similar:

-nocrop  
Disable cropping.

-guess\_crop (default)  
Use a simple heuristic to determine the cropping of the volume. In particular, mritotal removes any data more than 190mm below the top of the volume. This works reasonably well as long as the top of the subject's head is close to the top of the scanning volume, and the subject is a normal adult human.

-isocrop &lt;crop&gt;  
Crop all three spatial dimensions using the same crop specification (explained below).

-crop &lt;xcrop&gt; &lt;ycrop&gt; &lt;zcrop&gt;  
Crop the three spatial dimensions independantly, using the three crop specifications (explained below).

A crop specification is a pair of numbers that specify the amount to chop off each end of an axis. (Actually, these numbers specify how much to *extend* the axis by, so you must give negative numbers to chop data off. That's because crop specifications are simply passed to *autocrop,* which likes to extend dimensions by default.) The first number specifies how much to chop off the low end of the axis, and the second specifies how much to chop off the high end. Note that these are "low" and "high" in the sense implied by the MINC standard, i.e. the low end of the x axis is the patient's left, low y is patient posterior, and low z is patient inferior -- independent of the order or orientation of your data. Finally, the numbers can be specified in voxels, millimetres, or as a percentage of the original dimension extent.

As an example, data acquired under the ICBM (International Consortium for Brain Mapping) \[4\] MRI protocol extends well down into the subject's neck. This is because the volumes are sagittal acquisitions, with 256 1mm voxels in the z dimension. This excess data sometimes causes the fitting to fail, so we must first remove data roughly below the brain, without first knowing where the brain is. (After all, the whole point of registering data to a stereotaxic space is so that we can easily locate points such as the bottom of the brain in many subjects.) It was found that removing 25% of the volume from the bottom of the volume (low z) effectively does this. (Note that 75% of 256mm -- the amount left over after cropping -- is just 192mm, which is where the 190mm used by the "-guess\_crop" option came from.) This is explicitly given as a "crop specification" for the z axis by "-25%,0" -- meaning remove 25% of the data at the low end of the z axis, and don't touch the high end. Since we want to leave both the x and y axes alone, the crop specification for both is "0,0". Hence, to specify the entire cropping sequence, we use "-crop 0,0 0,0 -25%,0".

For a fancier example, recall that the crop amounts can be specified as percentages (of the original extent of each dimension), as millimetres, or as voxel counts. E.g., to remove 10 voxels at both ends of the x axis and 20mm at the top of the head (high z), you would use "-crop -10v,-10v 0,0 0,-20mm". You can mix and match the three units at will; for instance, you could chop 25% at the bottom, and 10 voxels at the top, of the z axis with "-crop 0,0 0,0 -25%,-10v". (If no unit is specified, mm is assumed.)

The final step of preprocessing is to (usually) blur the data. This is required because the default fitting algorithm depends on having blurred intensity data (using both 16mm and 8mm FWHM Gaussian kernels) and blurred gradient data (using an 8mm FWHM Gaussian kernel) available. (Note, however, that blurring can be disabled with the -noblur option.)

Before the data can be blurred, it must be zero-padded to minimize edge effects due to the FFT applied to mincblur. This step is not user-controllable, but for historical reasons the "unpadding" done after blurring (to remove the data effected by edge effects) is. In particular, releases of mritotal up to (and including) version 0.97 did not do this unpadding properly; they only removed the amount of data that was added with the original zero padding. Starting with version 0.98, the unpadding is done correctly by removing part of the original data as well. If necessary, you can force mritotal to use its old, incorrect behaviour with the "-oldpad" option.

FITTING ALGORITHM
=================

The multi-scale method used by mritotal is as follows: first, a principal axis computation is used to determine the "centre of gravity" of the input volume. (This computation is done on the subsampled, cropped, and clamped volume without any blurring.) The centre of the model (target) volume is also computed, and the difference between these two centres is used as the translational component of the initial transformation. There is no estimation of the initial rotations or scales. Then, an iterative optimization method is used to refine the fit using a 7-parameter transformation (translations, rotations, and one global scale). This is done with 16mm intensity blurred data.

An identical iterative fit is then performed on data that is less heavily blurred (using a Gaussian kernel of 8mm FWHM). After this step, all fitting is done on gradient data, again created with an 8mm Gaussian kernel; also, a mask is used to exclude all non-brain voxels from the fit. One more fit is performed using only seven parameters, after which a full nine parameters (three translations, three rotations, and three scales) are optimized.

Three fits are performed on 8mm gradient data with the nine parameter optimization. After the first one, mritotal takes a short break to ensure that the z-scale factor has not grown out of control; this is done by checking that the z-scale is no more than 15% greater than the average of the x and y scales. If it is, then it is set to the average of the x and y scales. Then, a fit is performed to optimize with the corrected z-scale (if necessary; this correction rarely takes place in practice). One final fit is performed to ensure that we have the correct minimum.

CONFIGURATION AND PROTOCOL FILES
================================

Through the configuration and protocol files, mritotal provides a flexible mechanism to specify site- and data-specific options. These are simply files with command-line options in them; comments (from any \# character to end-of-line) and blank lines are ignored. Also, only certain subsets of the command line options are allowed in each file.

Typically, there will be one global configuration file, and at least one global protocol file (these both live in /usr/local/etc/mnireg); users may also have their own files that live in their home directories. The configuration file (regardless of the directory it's in) is called mritotal.cfg, and the protocol files are named like mritotal.&lt;protocol&gt;.cfg, where &lt;protocol&gt; is the name of the protocol. This is specified by the -protocol option, which can appear either on the command line or in the configuration file. Usually, the configuration file will include "-protocol default", which means that the protocol file mritotal.default.cfg will be loaded from either the user's home directory or /usr/local/etc/mnireg (but not both).

The exact rules dealing with configuration and protocol files are:

1) mritotal searches for the configuration file in the user's home directory, followed by /usr/local/etc/mnireg. Whichever is found first is read and processed. The options allowed in the configuration file are the "site-specific" and "user preference" options: -model, -protocol, -verbose (-quiet), -execute (-noexecute), -clobber (-noclobber), -debug (-nodebug), -tmpdir, and -keeptmp (-nokeeptmp).

2) If one of the options in the configuration file is "-protocol" (it should be!), then as soon as that option is seen, mritotal reads and processes the corresponding protocol file. (If the configuration file specifies "-protocol foo", then mritotal will read mritotal.foo.cfg.) Again, the file is searched for first in the user's home directory, then in /usr/local/etc/mnireg (independently of where the configuration file was found).

3) After all the options in the configuration file are processed, the options given by the user on the command line are processed. If a -protocol option is seen, then step (2) repeats for the new protocol file; any options in it override options from previous protocol files. In fact, the user can specify any number of -protocol options, and each one will result in a new protocol file being read and overriding the options from previous protocol files.

If no protocol is specified (either in the configuration file or on tha command line), mritotal defaults to the same setup as is encoded in the "default" protocol distributed with the MNI Auto Registration Package.

SEE ALSO
========

minctracc1, mincblur1, autocrop1

AUTHORS
=======

mritotal was originally written as a C shell script by Louis Collins &lt;louis@nil.mni.mcgill.ca&gt;, who also devised the algorithm under the direction of Dr. Alan Evans &lt;alan@pet.mni.mcgill.ca&gt; and Dr. Terry Peters &lt;terry@nil.mni.mcgill.ca&gt; at the McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University. It was originally translated to Perl by Graeme O'Keefe, and completely rewritten using Perl 5 by Greg Ward &lt;greg@pet.mni.mcgill.ca&gt; (who also made some improvements to the preprocessing stage). minctracc, mincblur, volume\_cog, and check\_scale are all by Louis Collins and are distributed along with mritotal; autocrop is by Greg Ward and is distributed with mritotal; mincresample and mincreshape are by Peter Neelin &lt;neelin@pet.mni.mcgill.ca&gt; and are distributed as part of the MINC package. Copyright (c) 1993-95 by Louis Collins and Greg Ward.

AVAILABILITY
============

mritotal is part of the MNI Automated Registration Package (MNI\_AutoReg) from <http://pacakges.bic.mni.mcgill.ca/>

REFERENCES
==========

\[1\] Collins DL, Neelin P, Peters TM, and Evans AC, "Automatic 3-D intersubject registration of MR volumetric data in standardized Talairach space", Journal of Computer Assisted Tomography, 182:192-205.

\[2\] Evans AC, Collins DL, Milner B, "An MRI-based stereotactic atlas from 250 young normal subjects", Soc Neurosci Abstr, 1992;18:408.

\[3\] Talairach J, Tournoux P, "Co-planar sterotactic atlas of the human brain: 3-dimensional proportional system: an approach to cerebral imaging", Stuttgart: Georg Thieme Verlag, 1988.

\[4\] Mazziota JC, Toga AW, Evans A, Fox P, and Lancaster J, "A probabilistic atlas of the human brain: theory and rationale for its development", Neuroimage 2, 89-101 (1995).
