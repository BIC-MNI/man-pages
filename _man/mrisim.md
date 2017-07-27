---
section: 1
title: mrisim
author: Remi Kwan
...

MRISIM
======


mrisim - an MRI simulation system 

SYNOPSIS
--------

**mrisim** \[ *&lt;options&gt;* \] *&lt;output.mnc&gt;*

**mrisim** \[ *-version* \]

**mrisim** \[ *-help* \]


DESCRIPTION
-----------

**mrisim** is a simple MRI simulation program which produces MINC
volumes from a segmented and labelled brain phantom. It allows intrinsic
tissue parameters (T1, T2...) and pulse sequence parameters (TR, TE ...)
to be specified and then produces simulated images with noise.
Currently, no artifacts are implemented.

All input and output is through the command line and parameter files
giving default values. In each parameter file, all entries must appear
in the stated order. The format of each parameter file is described
below. It is probably best to make copies of the sample parameter files
and change parameter values if needed.


OPTIONS
-------

**mrisim** has the following options. All non-ambiguous abbreviations of
command line switches are also valid. Parameters are denoted with angle
brackets, &lt;&gt;, and optional arguments are denoted with square
brackets, \[\].

**-discrete** *\[&lt;discrete.mnc&gt;\]*

This option specifies that a discrete phantom is to be used. Optionally,
a discrete phantom file can be given. If a phantom file is not given the
default file in the tissue parameter file is used.

**-fuzzy**
*\[&lt;fuzzy0.mnc&gt;:&lt;label0&gt;,...,&lt;fuzzyN.mnc&gt;:&lt;labelN&gt;\]*

This option specifies that a fuzzy phantom is to be used. Optionally,
fuzzy phantom files can be given in a list. This list consists of a
phantom filename separated from its corresponding tissue label by a
colon. The tissue label must correspond to a tissue label in the tissue
parameter file. If fuzzy phantom files are not given, the default files
in the tissue parameter file are used.

**-tissue** *&lt;tissue.prm&gt;*

This option specifies the tissue parameter file to use.

**-coil** *&lt;coil.rf&gt;*

This option specifies the RF coil parameter file to use.

**-sequence** *&lt;sequence.seq&gt;*

This option specifies the pulse sequence parameter file to use.

**-rxmap** *\[&lt;rxmap.mnc&gt;\]*

This option specifies that signal reception RF inhomogeneity is to be
modelled in the simulation. Optionally, an RF inhomogeneity map file can
be given. This map file must be a MINC volume of the same size as the
labelled phantom volume. If no field map file is given, the default file
in the RF coil parameter file is used.

**-txmap** *\[&lt;txmap.mnc&gt;\]*

This option specifies that signal transmission RF inhomogeneity is to be
modelled in the simulation. Optionally, an RF inhomogeneity map file can
be given. This map file must be a MINC volume of the same size as the
labelled phantom volume. If no field map file is given, the default file
in the RF coil parameter file is used.

**-logfile** *\[&lt;logfile.log&gt;\]*

This option specifies that a log file is to be generated. Optionally,
the name of the log file can be given. If a file name is not given, by
default, a log file named "mrisim.log" will be generated.

**-noclobber**

This option causes **mrisim** to not overwrite the output simulation
file if it already exists. This is the default.

**-clobber**

This option causes **mrisim** to overwrite the output simulation file if
it already exists.

**-verbose**

This option causes log messages to be printed to stdout while the
simulation is running. This is the default.

**-quiet**

This option causes no log messages to be printed while the simulation is
running.

**-voxel\_dims** *&lt;z-step-mm&gt; &lt;y-step-mm&gt; &lt;x-step-mm&gt;*

This option specifies the voxel dimensions of the simulated volume in mm
and (z y x) order. This overrides any entries in the pulse sequence
parameter file. When this option is used, both slice thickness and slice
separation will be set to &lt;z-step-mm&gt;. If a different slice
thickness is required, this can be specified with -slice\_thickness. If
-voxel\_dims is not used, voxel dimensions are read from the pulse
sequence parameter file by default.

**-voxel\_offset** *&lt;z-offset-mm&gt; &lt;y-offset-mm&gt;
&lt;x-offset-mm&gt;*

This option specifies an offset in mm for each dimension of the
simulated image in (z y x) order. The quarter voxel shift used in
previous releases can be specified by using -old\_offset.

**-gain** *&lt;signal\_gain&gt;*

This option specifies a image signal gain multiplier for the output
image. Tissue simulations are computed normalized to a maximum CSF
signal of 1.0. The default gain multiplier used is 10000, giving output
image voxels in the range 0..10000.

**-recon\_matrix** *&lt;recon-size&gt;*

This option specifies the size of the square reconstructed output image
matrix. This must be one of 64, 128, 256, or 512.

**-scan\_matrix** *&lt;scan-size&gt;*

This option specifies the size of the square acquisition matrix. This
must be one of 64, 128, 256, or 512.

**-slice\_thickness** *&lt;slice-thickness-mm&gt;*

This option specifies the slice thickness to use in mm. Note that this
parameter specifies the slice thickness used in slice selection and
noise computations, and does not refer to the inter-slice sample
separation that is specified as the parameter &lt;z-step-mm&gt; with
-voxel\_dims.

**-nslices** *&lt;number-of-slices&gt;*

This option specifies the number of output slices to generate. By
default this is zero, and the number of slices will be read from the
pulse sequence parameter file. If the number of slices entry in the
parameter file is empty **mrisim** will attempt to generate enough
slices to sample the entire phantom volume.

**-nnpv**

This option specifies that the old nearest-neighbour partial volume
evaluation method is to be used. By default, a Fourier resampling
technique is used to evaluate imaging chain partial volume.

**-old\_offset**

This option specifies that a quarter voxel offset of the output images
is to be used as in previous releases.

**-version**

This option prints version information and exits.

**-help**

This option prints a summary of the command-line options.

[ ]()

PHANTOM FILES
-------------

Anatomical features are described in **mrisim** using phantom files as
input. A phantom file is a standard MINC volume which consists of
labelled tissue data. Both compressed and uncompressed MINC volumes can
be used, although processing of uncompressed volumes is faster. Two
types of phantom data are supported: discrete label data and fuzzy label
data.

A discrete label phantom consists of a volume of discrete, integer
valued, labels, each representing a particular tissue class. Standard
examples of discrete phantoms are *phantom10.mnc.Z* (see FILES) and
*colin20.mnc.Z* which are 1.0 mm and 0.5 mm isotropically sampled
discrete volumes. From these phantoms, it is possible to produce
lower-resolution simulated images with partial volume effects by
specifying the required resolution in the pulse sequence parameter file
(see below).

Fuzzy label phantoms allow more flexibility in defining anatomical
partial volume effects. In a discrete phantom, each voxel must belong to
a given tissue class. Using fuzzy phantoms, tissue fractions can be
specified so that a voxel may be, for instance, 10% grey matter and 90%
white matter. This is a more general method of specifying tissue
phantoms and allows smoother transitions between tissue boundaries to be
specified. A fuzzy phantom for N distinct tissue classes is specified by
N MINC volumes. Each volume specifies a tissue fraction between 0 and 1
for each voxel. This can be thought of as a tissue probability map. When
generating simulations, the simulator normalizes the tissue fraction sum
for each voxel to one.

[ ]()

PARAMETER FILES
---------------

Parameter files are used to define default values for simulator input.
Certain parameters may be specified using command-line arguments. If
this is the case, the default values in parameter files are overridden.
**mrisim** parameter files all follow a standard format. Each line can
either be a comment line or a line specifying a parameter value. If a
line begins with a \# it is parsed as a comment and ignored, otherwise
the line must consist of a label, followed by a colon (:), followed by
an optional end of line comment in parenthesis. The label is used as a
descriptive comment, and the end of line comment is normally used to
describe valid ranges for the field. Note that the order in which lines
appear within the file is important. The field label is merely
descriptive and is not parsed by the simulator.

[ ]()

### TISSUE PARAMETER FILE (tissue.prm)

The tissue parameter file describes the tissue characteristics of input
phantom files. The first five parameters in the tissue parameter file
are as follows:

**Number of Tissue Classes**

Specifies the number of tissue labels that will be described by the
phantom. Between 1 and 255 unique labels can be specified.

**Simulation Flip Angles**

If transmission RF inhomogeneity is simulated, this specifies the number
of discrete flip angles that will be simulated. All other flip angles
will then be generated by linearly interpolating between these points.

**Phantom Type**

Specifies if a discrete or fuzzy label phantom is to be used. Note that
this can be overridden using the -discrete or -fuzzy command-line
switches.

**Highest Tissue Label**

Specifies the largest tissue label that appears in the phantom.

**Discrete Label File**

Specifies a path for the discrete label phantom. Note that the path is
either absolute or relative to the current working directory of the
simulator.

Following this is a description of each tissue and its parameters. The
following seven parameter fields are repeated for each tissue label.

**Tissue Name**

Specifies a descriptive name for the tissue type.

**Tissue Label**

Specifies the integer tissue label of the tissue type. Note that if a
discrete phantom is used and this tissue label does not appear in the
phantom, results are undefined.

**T1**

Specifies the longitudinal relaxation, T1, in msec.

**T2**

Specifies the transverse relaxation, T2, in msec.

**T2\***

Specifies the transverse relaxation, T2\*, in msec.

**NH**

Specifies the proton density, NH, (0 &lt; NH &lt; 1). For brain images,
the proton density of CSF is normally taken to be 1 and all other
tissues are measured relative to this.

[ ]()

### COIL PARAMETER FILE (coil.rf)

The coil parameter file specifies parameters related to the scanner's
reception system. This includes specifying noise model parameters and RF
field inhomogeneity for signal reception and transmission.

**Noise Model**

Specifies the noise model to use. The noise model must be one of
noiseless, percent, intrinsic, or imagesnr. The noiseless model
generates ideal images with no noise added. The percent model generates
noise with a standard deviation given as a percentage of the signal for
a reference tissue. The intrinsic model generates noise based on the
intrinsic SNR model of the scanner and image acquisition parameters. The
imagesnr model generates images with a required image SNR. Note that all
models generate images with Rayleigh statistics in the background and
Rician statistics in signal regions.

**Percent Noise**

This is a percentage in the range 0 to 100%. It specifies the standard
deviation of the gaussian noise that is to be added to real and
imaginary channels, and is used with the percent noise model. If X
specifies the noise percentage, in the range 0% to 100%, S refers to the
reference slice thickness, and T refers to the reference tissue label,
the standard deviation of noise will be calculate by

stddev = (X/100)\*intensity\_of\_tissue(T) for S mm slices

**Reference Thickness**

Specifies the slice thickness that is taken as a reference for the
percent noise model. For an absolute noise percentage, the reference
thickness should be 0.

**Reference Tissue**

Specifies the tissue label of the tissue to be used as a reference for
the percent noise model. If the specified reference tissue is 0, the
tissue with the maximum signal intensity is used.

**Intrinsic SNR**

The intrinsic signal to noise ratio of the coil normalized to
Hz\^(1/2)/mm\^3. If no noise is required set this parameter to -1. This
parameter is used with the intrinsic noise model.

**Receive map**

Specifies a MINC file to use as the default receive RF inhomogeneity
map. The size of the field map must be the same as the size of the input
labelled phantom. If no receive inhomogeneity is wanted, this should be
left blank.

**Transmit map**

Specifies a MINC file to use as the default transmit RF inhomogeneity
map. The size of the field map must be the same as the size of the input
labelled phantom. If no transmit inhomogeneity is wanted, this should be
left blank.

**Random seed**

The seed used to initialize the random number generator. This can be any
long integer and specified to generate the same pseudo-random number
sequence for multiple simulations. If 0 is entered, the simulator will
automatically generate a seed based on the time returned by
[time](/cgi-bin/man/man2html?2+time)(2).

[ ]()

### PULSE SEQUENCE PARAMETER FILE (sequence.seq)

The pulse sequence file consists of a list of sequence parameters, for
some commonly used sequences. It is possible to program other sequences
very easily, however this currently requires writing in C++. The
following describes the parameters in the pulse sequence file.

**Offcentre Z**

Specifies an offset in mm for the output z-direction. This offset is
relative to the world coordinates of the input phantom.

**Offcentre Y**

Specifies an offset in mm for the output y-direction. This offset is
relative to the world coordinates of the input phantom.

**Offcentre X**

Specifies an offset in mm for the output x-direction. This offset is
relative to the world coordinates of the input phantom.

**Slice orientation**

Specifies the orientation of the output image. This must be one of same
(same orientation as the input phantom), tra (transverse), sag
(sagittal), or cor (coronal). Note: only same is currently oriented. Use
[mincresample](/cgi-bin/man/man2html?1+mincresample)(1) to obtain
different orientations.

**Foldover direction**

Specifies the foldover (readout) direction for the acquisition.

**Number of slices**

Specifies the number of slices to be acquired. If this is 0 or blank,
the simulator will attempt to generate enough slices to cover the entire
input phantom z-coordinate.

**Slice thickness**

Specifies the slice thickness in mm of the acquisition used in computing
slice selection and noise levels. Unless overlap is required, this is
usually set to be the same as slice separation.

**Slice separation**

Specifies the separation or interslice sample distance in mm.

**Field of view**

Specifies the field of view in mm of slices. The voxel size with slices
will then be given by the field of view divided by the number of
samples, or reconstruction matrix size (see below).

**Rectangular FOV**

Specifies the scan percentage to be used in the range 0% to 100% for a
rectangular field of view acquisition. Note that currently, this only
affects noise calculations and rectangular FOV partial Fourier data is
not generated.

**Scan technique**

Specifies the type of pulse sequence to use. This must be one of SE
(spin echo), IR (inversion recovery), SFLASH (spoiled FLASH), CEFAST
(contrast enhanced FAST), FISP, FLASH, DSE\_EARLY (dual echo spin echo,
early echo), or DSE\_LATE (dual echo spin echo, late echo).

**Scan mode**

Specifies if a 2D, 3D or MS (multislice) sequence is to be acquired.
Note that currently this only affects noise calculations as all
simulations are simulated as multislice acquisitions.

**Repetition time (TR)**

Specifies the repetition (TR) in ms.

**Inversion time (TI)**

Specifies the inversion time (TI) in ms. This is only used for inversion
recovery sequences.

**Number of echoes**

Specifies the number of echoes to use in spin echo sequences.

**Partial Echo**

Specifies that a partial echo acquisition is to be used. The percentage
of the partial echo is taken from the scan percentage parameter. Note
that currently this only affects noise calculations as no partial
Fourier raw data is generated.

**Echo times**

Specifies the echo time (TE) in mm. If more than one echo is specified
in number of echoes, then multiple echo times should be specified in a
comma delimited list.

**Flip angle**

Specifies the flip angle in degrees to be used for the acquisition. Note
that all SE and IR sequences use an excitation flip angle of 90 degrees
regardless of the flip angle entry.

**Water fat shift**

Specifies the water fat shift in pixels to be used. This is used to
specify the receiver bandwidth for noise calculation.

**Number of signals averaged**

Specifies the number of signal excitations or averages.

**Half scan**

Specifies that a half Fourier scan is to be used. The percentage of the
scan is taken from the scan percentage parameter. Note that currently
this only affects noise calculations as no partial Fourier raw data is
generated.

**Scan percentage**

Specifies the scan percentage in the range 0% to 100% to use for partial
Fourier acquisitions. Note that currently this only affects noise
calculations as no partial Fourier raw data is generated.

**Scan matrix**

Specifies the size of the acquisition matrix to be used. This must be
one of 64, 128, 256, or 512.

**Reconstruction matrix**

Specifies the size of the reconstruction matrix to be used. This must be
one of 64, 128, 256, or 512.

**Image Type**

Specifies the type of the reconstructed output image. This must be one
of R (real), I (imaginary), M (magnitude), P (phase), or none.

**Save raw data**

Specifies that the acquired raw Fourier data should be saved. If the
output file specified was "output.mnc" two files named
"output.raw\_real.mnc" and "output.raw\_imag.mnc" will be created which
contain the real and imaginary parts of the raw data.

FILES
-----

`phantoms`

contains sample phantoms and tissue parameter files.

`sequences`

contains sample pulse sequence parameter files.

`coils`

contains sample RF coil parameter files.

`fields`

contains sample RF inhomogeneity field maps.

`phantoms/phantom10.mnc.Z`

standard labelled phantom data.


DIAGNOSTICS
-----------

While running, mrisim currently outputs a lot of information to stdout
which is useful for diagnosing what the simulation is doing. These
messages are also saved in a log file which describes the simulation.


BUGS
----

If you have any problems or have ideas for features you would like to
see implemented please let me know.

AUTHOR
------

Remi Kwan, <rkwan@nil.mni.mcgill.ca>

