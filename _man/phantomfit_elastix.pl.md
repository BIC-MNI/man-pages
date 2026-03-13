---
section: 1
title: phantomfit_elastix.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# phantomfit_elastix.pl

hierarchical nonlinear fitting constrained by spherical harmonics using Elastix

`phantomfit_elastix.pl [options] source.mnc target.mnc source_mask.mnc target_mask.mnc bricks.mnc [...] output.xfm`

## DESCRIPTION

**phantomfit_elastix.pl** is a variant of **phantomfit.pl** that uses **Elastix**
for the nonlinear registration step. This variant accepts five positional inputs:
the source and target volumes, corresponding source and target masks, and a
bricks volume that identifies the internal marker structure of the phantom. The
deformation field is constrained by a spherical-harmonic basis to produce a
smooth parametric distortion model.

The fitting proceeds through multiple resolution levels. The bricks volume
provides additional structural constraints specific to phantoms with a regular
grid of internal markers. An output directory can be specified for Elastix
intermediate results.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-debug`
:   Enable debug mode with additional diagnostic output.

`-clobber`
:   Overwrite existing output files.

`-fake`
:   Print the commands that would be executed without running them.

`-init_xfm <xfm>`
:   Use the specified transformation as the initial starting estimate.

`-order <n>`
:   Maximum order of the spherical-harmonic expansion. Default: 5.

`-par <file>`
:   Write the spherical-harmonic parameter file to the specified path.

`-measure`
:   Only measure the distortion without iterative fitting.

`-step_iterations <n>`
:   Number of iterations at each step of the hierarchical registration.

`-min_step <f>`
:   Minimum step size in millimetres for the finest level of the hierarchy.
    Default: 1.

`-limit`
:   Limit the magnitude of the estimated distortion field.

`-keep <f>`
:   Fraction of the distortion field to retain after filtering. Default: 1.0.

`-cylindric`
:   Use cylindrical coordinate representation for the distortion model.

`-init <xfm>`
:   Provide an initial linear transformation for the registration.

`-work_dir <dir>`
:   Specify a working directory for intermediate files.

`-outdir <dir>`
:   Specify an output directory for Elastix intermediate results.

`-pca`
:   Use PCA regularization for the distortion model.

`-pcs <n>`
:   Number of principal components to retain when using PCA regularization.

## EXAMPLES

Fit a distortion model using Elastix with brick markers:

    phantomfit_elastix.pl phantom_scan.mnc phantom_model.mnc \
        source_mask.mnc target_mask.mnc bricks.mnc output.xfm

Fit with higher-order harmonics and a custom output directory:

    phantomfit_elastix.pl -order 7 -min_step 0.5 -outdir /tmp/elastix_work \
        -verbose phantom_scan.mnc phantom_model.mnc \
        source_mask.mnc target_mask.mnc bricks.mnc output.xfm

Fit with parameter output and PCA regularization:

    phantomfit_elastix.pl -par distortion.par -pca -pcs 10 -clobber \
        phantom_scan.mnc phantom_model.mnc \
        source_mask.mnc target_mask.mnc bricks.mnc output.xfm

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit.pl**(1)
