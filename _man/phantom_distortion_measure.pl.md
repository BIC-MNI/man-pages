---
section: 1
title: phantom_distortion_measure.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# phantom_distortion_measure.pl

calculate geometric distortion from phantom scans via hierarchical nonlinear registration

`phantom_distortion_measure.pl <scan_1> [scan_2 ...] <output.par> <output.xfm> [options]`

## DESCRIPTION

**phantom_distortion_measure.pl** measures geometric distortion in MRI scanner
acquisitions by performing hierarchical nonlinear registration between one or
more phantom scans and a known distortion-free phantom model. The registration
is constrained by a spherical-harmonic basis to produce a smooth parametric
distortion field. The output consists of a parameter file (`.par`) describing
the distortion in spherical-harmonic coefficients and an XFM grid transform
file.

Multiple phantom scans can be provided to improve robustness by averaging the
distortion estimates. The phantom model must be specified with the `--model`
option. The order of the spherical-harmonic expansion, the minimum registration
step size, and various other parameters can be tuned.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--debug`
:   Enable debug mode with additional diagnostic output.

`--clobber`
:   Overwrite existing output files.

`--order <n>`
:   Order of the spherical-harmonic expansion used to model the distortion
    field. Default: 5.

`--work_dir <dir>`
:   Specify a working directory for intermediate files. A temporary directory
    is used if not specified.

`--model <dir>`
:   Path to the phantom model directory. This option is required.

`--min_step <f>`
:   Minimum step size in millimetres for the hierarchical registration.
    Default: 2.

`--no_core_extract`
:   Skip the core extraction step that isolates the phantom interior from the
    background.

`--measure`
:   Only measure the distortion without fitting the parametric model.

`--mask <mask.mnc>`
:   Specify a mask to restrict the region used for distortion measurement.

`--exclude <file>`
:   Specify a file listing regions to exclude from the distortion fit.

`--limit_linear`
:   Limit the linear component of the registration.

`--keep <f>`
:   Fraction of the distortion field to retain after filtering. Default: 1.0.

`--cylindric`
:   Use cylindrical coordinate representation for the distortion model.

`--acr`
:   Use ACR (American College of Radiology) phantom geometry.

`--init <xfm>`
:   Provide an initial transformation for the registration.

`--step_iterations <n>`
:   Number of iterations at each step of the hierarchical registration.

`--adni`
:   Use ADNI (Alzheimer's Disease Neuroimaging Initiative) phantom geometry.

`--out-roi <file>`
:   Write a region-of-interest mask to the specified file.

`--only-roi`
:   Only compute the distortion within the specified region of interest.

`--dilate-roi <n>`
:   Dilate the region-of-interest mask by the given number of voxels.

`--pca`
:   Use PCA (Principal Component Analysis) regularization for the distortion
    model.

`--pcs <n>`
:   Number of principal components to retain when using PCA regularization.

`--dd`
:   Use Diffeomorphic Demons for the nonlinear registration step.

`--ants`
:   Use ANTs (mincANTS) for the nonlinear registration step.

`--keep-tmp`
:   Do not remove temporary working files after processing.

## EXAMPLES

Measure distortion from a single phantom scan:

    phantom_distortion_measure.pl phantom_scan.mnc distortion.par distortion.xfm \
        --model /path/to/phantom_model --verbose

Measure distortion from multiple scans with higher-order harmonics:

    phantom_distortion_measure.pl scan1.mnc scan2.mnc scan3.mnc \
        distortion.par distortion.xfm \
        --model /path/to/phantom_model --order 7 --min_step 1

Use cylindrical coordinates with ANTs registration:

    phantom_distortion_measure.pl phantom.mnc distortion.par distortion.xfm \
        --model /path/to/phantom_model --cylindric --ants --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit.pl**(1), **phantom_distortion_measure_v2.pl**(1)
