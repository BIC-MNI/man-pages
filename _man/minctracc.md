# MINCTRACC

minctracc estimates the spatial transformation required to register two volumes together.
`minctracc <options> <source> <target> <output>`
`minctracc -help`

## DESCRIPTION

*Minctracc* will estimate the best linear spatial transformation required to register two 3D volumes. The program uses optimization over a user selectable number of parameters to identify the best (according to a user identified objective function) transformation that maps voxel values of the first data set into the second. The objective function is evaluated on a 3D lattice with user-specified spacing.

## OVERVIEW

You need to specify two MINC data files on the command line, the first is the source volume and the second is the target volume. The third item on the command line is the name of the output transformation file, specifying where the program will store the results (in .xfm format). Note that the output is *not* a new MINC volume; you must use mincresample to resample the data according to the transform output by minctracc if you wish to see the transformed image data.

Using flags on the command line, the user can specify:

- the type of transformation to be optimized and saved, - mask files to be used with the source or target volumes, - a transformation file to specify the initial starting condition, - the type of objective function to be minimized, - the type of interpolation function to use, - and the definition of the sampling matrix used to measure the objective function.

Internally, the program optimizes the transformation parameters of translations, rotations, scaling(s) and possibly shear(s). These parameters are used to create a homogeneous transformation matrix that maps the data in the world space of the first volume to the world space of the second volume. It is this matrix that is saved in the output transformation file. The program 'xfm2param' can be used to extract the transformation parameters from the .xfm file.

## Specifying the initial starting position:

There are a number of methods available to get an initial transformation to start the optimization process. The first is the default if there is no input transformation information on the command line. In this case, a principal axes transformation (PAT) is used as the starting transformation. When the PAT is used, the center of rotation and scaling is automatically estimated from the center of gravity (COG) of the source data set. The initial translation parameters are those needed to align the COGs of the two data sets. The rotations are those need to align the principal axes of the two volumes. This method is not always robust when the two data sets do not represent the same volume (ie source is 10cm thick slice of brain, and the target is a whole head), so other initialization methods are available.

In the second method, with the '-transformation' option the user specifies a transform (.xfm) file that contains a linear transformation used to map points of volume one (source) into volume two (target). This transformation file can be the result of a rough manual registration accomplished with 'register', or the previous result of an application of minctracc, for example.

The third option is used when the two volumes are already fairly closely aligned (eg., if they were acquired in the same scanning session). Here, '-identity' is used to specify an identity matrix to the used to initialize the transformation matrix.

Once the matrix is specified, the program extracts the transformation parameters (translations, rotations, scales and shears) and optimizes these parameters when trying to find the best transformation.

When the user specifies a transformation matrix (other than PAT), the default center is 0,0,0. The user can can change this in two ways: 1) the '-center <cx> <cy> <cz>' option permits direct input of the center to be used, 2) the '-est\_center' option tells the program to estimate and use the center of gravity of the source volume. Note that it is a good idea to have a reasonable guess for the center of rotation and scaling since it makes the parameters more orthogonal to each other (e.g. a small change in rotation will not grossly affect the translations).

Note that when estimating a non-linear registration, if no transformation is given as input, the program will estimate a linear transformation first. If you are interested in only the non-linear transformation, then use -identity.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## Initial transformation information.

These are the options used to specify the initial starting conditions for the optimization of the transformation parameters.

`-transformation` <filename.xfm>: Specify a file giving the world coordinate transformation mapping points from the source into the target space.

`-identity:` Use identity transformation for starting point.

`-est_center:` Use only the center estimated from Principal axis trans.

`-est_scales:` Use only the scales estimated from Principal axis trans.

`-est_translations:` Use only the translations estimated from Principal axis trans.

Note that the four previous options (-est\_\*) are not mutually exclusive. You can, for example, use '-est\_center -est\_translations' to estimate the center of rotation and scaling, as well as the initial translation componant required to register the centers of gravity of the two volumes.

`-center` <xcent> <ycent> <zcent>: Force the center of rotation and scale.

`-no_clobber:` Do not overwrite output file (default).

`-clobber:` Overwrite output file.

## Output transformation type.

The type of output file can be constrained depending on the type of registration required. For example, intra-subject registration can be completed with only 6 parameters if rigid body assumptions hold.

`-pat:` Return the principal axis transformation matrix (input matrix ignored), no optimization done.

`-lsq3:` Return a 3 parameter transformation (3 translations only).

`-lsq6:` Return a 6 parameter rigid-body transformation (3 translation, 3 rotation, scale=1.0).

`-lsq7:` Return a 7 parameter transformation (lsq6 + 1 global scale; this is the same as -procrustes, and is the default).

`-lsq9:` Return a 9 parameter transformation (lsq6 + 3 scales).

`-lsq10:` Return a 10 parameter transformation (lsq9 + 1 shear).

`-lsq12:` Return a full 12 parameter transformation (lsq9 + 3 shears).

`-lsq:` Return a full 12 parameter transformation (same as -lsq12).

`-procrustes:` Return a procrustes transformation (3 trans, 3 rots, 1 scale), same as -lsq7. This is the default.

`-forward:` Recover forward transformation (source -> model, default).

`-invert:` Recover inverted transformation (model -> source).

## Options for mask volumes.

`-model_mask` <filename>: Specifies a binary mask file for the target. Any data voxel whose world coordinate falls in a zero-valued voxel in the mask is ignored in the calculation of the objective function.

`-source_mask` <filename>: Specifies a binary mask file for the source.

## Interpolation options.

`-trilinear:` Do a tri-linear interpolation between voxels when estimating the value for a node in the 3D lattice. This is the default.

`-tricubic:` Do a tri-cubic interpolation between voxels.

`-nearest_neighbour:` Do nearest neighbour interpolation between voxels (ie. find the voxel closest to the point and use its value).

## Optimization objective functions.

`-xcorr:` Use cross correlation (this is the default) \[2\].

`-zscore:` Use normalized difference. Before optimization, each volume is normalized to have the same mean, with a range of +/- 5 standard deviations. The objective function is simply the difference in normalized values between the two volumes.

`-ssc:` Use stochastic sign change \[3\]. This is the same as maximization of zero crossings.

`-vr:` Minimize the variance of the ratio vol1/vol2 \[4\].

`-mi:` Use mutual information similarity measure \[1\].

`-groups` <num>: Number of groups for -vr and -mi (default = 16).

`-threshold` <thresh1> <thresh2>: Lower limit for voxel threshold (default = 0.0 0.0). Lattice nodes with voxel values below this limit are ignored in the objective function. The threshold applies when -xcorr, -vr, -mi or -zscore are used as the objective function.

`-speckle` <val>: Percent speckle noise to add to source (default = 5). This option applies only when -ssc is used as the objective function.

## Options for linear optimization.

Simplex optimization is used to maximize/minimize the objective function to find the best transformation parameters.

`-tol` <val>: Stopping criteria tolerance (default = 0.005). The optimization will stop when tol> (f\_max-f\_min)/(f\_max+f\_min), where f\_max and f\_min are the maximum and minimum values of the objective function in the Simplex.

`-simplex` <val>: Radius of simplex volume (default = 20). This is measured in units of millimeters on the spatial axis, degrees of rotation or percentage scale on the scaling dimensions. When the initial estimate is know to be relatively good, the simplex radius should be reduced to the level of certainty of the input parameters.

`-w_translations` <w\_tx> <w\_ty> <w\_tz>: Optimization weight of translation in x, y, z (default = 1.0 1.0 1.0).

`-w_rotations` <w\_rx> <w\_ry> <w\_rz>: Optimization weight of rotations around x, y, z (default = 0.0174533 0.0174533 0.0174533). Internally, the rotations are stored as radians, although all user input is in degrees. The value 0.0174533 makes one degree equivalent to 1 mm in the optimization.

`-w_scales` <w\_sx> <w\_sy> <w\_sz>: Optimization weight of scaling along x, y, z (default = 0.02 0.02 0.02). This makes a 2% change in scale equivalent to 1mm of translation.

`-w_shear` <w\_sa> <w\_sb> <w\_sc>: Optimization weight of shears a,b and c (default = 0.02 0.02 0.02)

`-use_bfgs` Use BFGS optimizer instead of amoeba simplex

## Options for 3D lattice definition.

The objective function is estimated only on the nodes of a 3D lattice defined on the smallest of the two volumes. In this way, the coordinates of the lattice are used to specify positions in one volume, and when mapped through the transformation matrix, specify homologous positions in the other volume. The spacing between lattice samples is directly related to the resolution of the data used in the fit. For example, data blurred with a 12mm fwhm gaussian kernel does not need to be sampled with spacing less than 6mm.

`-step` <sx> <sy> <sz>: Step size (in mm) along each dimension (x, y, z). Default value is 4.0 4.0 4.0.

`-xstep` <sx>: Step size along the X dimension (default = 4.0).

`-ystep` <sy>: Step size along the Y dimension (default = 4.0).

`-zstep` <sz>: Step size along the Z dimension (default = 4.0)

## Options for optimization of non-linear transformations

The non-linear transformation is represented by a deformation field, (normally) defined in the space of the target volume. The full transformation is equal to the linear transformation plus the deformation stored in the deformation field. The deformation field is represented by a vector-valued 3D volume with -step distance between nodes.

`-nonlinear` specifies that a non-linear deformation field should be estimated. the -nonlinear can take on one of the following optional arguments: xcorr, diff, sqdiff, label, chamfer, corrcoeff, or opticalflow to define the objective function to be used to compare the source and target volumes.

`-sub_lattice` <val>: Defines the number of nodes along the diameter of the sublattice that defined the local neighbourhood used to estimate the deformation vector.

`-lattice_diameter` <valx> <valy> <valz>: determines the size (in mm) of the sublattice used to define the local neighbouhood.

`-use_magnitude` use magnitude data local deformation (default). this flag tells minctracc that a local sublattice will be needed. You normally don't have to specify this flag.

`-optical_flow` a flag to use optical flow to compute deformation on the two firstmain source/model volumes.

`-use_simplex` a flag to use 3D simplex optimization for local deformation (default).

`-quadratic` a flag to turn on local quadratic fitting for local deformation.

`-use_local` a flag to turn on local smoothing. by default, minctracc uses global smoothing for regularization.

`-use_nonisotropic` a flag to turn on directionally sensitive smoothing (def=isotropic smoothing) when usinglocal smoothing.

`-super` <val>: super sample deformation field during optimization (default=2) to speed up the evaluation of local deformation vectors.

`-no_super` turn off the super sample deformation field during optimization.

`-iterations` <val> this is the number of iterations for non-linear optimization (default value: 4).

`-weight` <val>: Weighting factor for each iteration in nl optimization. This defines how much of the currently estimated vector should be added to the deformation field (default value: 0.6).

`-stiffness` <val>: Weighting factor to define smoothness for regularization at each iteration (default value: 0.5).

`-similarity_cost_ratio` <val> Weighting factor to reduce the effect of large deformations \[ r=similarity\*w + cost(1\*w) \] (default value: 0.5)

## Options for logging progress.

`-verbose` <val>: Write verbose messages indicating progress (default = 1).

`-quiet:` Do not write log messages

`-debug:` Print out debug info.

## Generic options

`-help:` Print summary of command-line options and abort.

## EXAMPLES

Estimate the transformation required to map structures from an individual subject to match those in a target volume:

minctracc subject.mnc target.mnc subj\_to\_targ.xfm

Match the same subject, scanned on two occasions with similar protocol:

minctracc subj\_time1.mnc subj\_time2.mnc result.xfm BSOL -lsq6 -identity -est\_center

## REFERENCES

\[1\] A. Collingnon, F. Maes, D. Delaere, D. Vandermeulen, P. Suetens, G. Marchal, "Automated multi-modality image registration based on information theory", IPMI, 1995:263-274.

\[2\] Collins DL, Neelin P, Peters TM, and Evans AC, "Automatic 3-D intersubject registration of MR volumetric data in standardized Talairach space", J. Comput. Assis. Tomogr, 18(2):192-205.

\[3\] Minoshima S, Berger KL, Lee Ks, Mintun MA. "An automated method for rotation correction and centering of 3D functional brain images", J. Nucl. Med., 1992;33(8):1579-1585.

\[4\] R.P. Woods, J.C. Mazziotta, S.R. Cherry, "MRI-PET Registration with Automated Algorithm", J. Comput. Assis. Tomogr, 1993;17:536-546.

## AUTHOR

Louis Collins

## COPYRIGHTS

Copyright 1993-95 by Louis Collins
