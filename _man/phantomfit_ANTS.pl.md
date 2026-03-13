---
section: 1
title: phantomfit_ANTS.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# phantomfit_ANTS.pl

hierarchical nonlinear fitting constrained by spherical harmonics using ANTs

`phantomfit_ANTS.pl [options] source.mnc target.mnc fit_mask.mnc estimate_mask.mnc [...] output.xfm`

## DESCRIPTION

**phantomfit_ANTS.pl** is a variant of **phantomfit.pl** that uses
**mincANTS** (Advanced Normalization Tools) for the nonlinear registration step
instead of **minctracc**. The deformation field is constrained by a
spherical-harmonic basis to produce a smooth parametric distortion model.

The fitting proceeds through multiple resolution levels. Two masks are required:
a fit mask for registration optimization and an estimate mask for distortion
parameter estimation. Additional mask pairs can be provided. This variant does
not expose the weight, stiffness, or similarity parameters available in
**phantomfit.pl**, as ANTs uses its own internal regularization scheme.

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

`-pca`
:   Use PCA regularization for the distortion model.

`-pcs <n>`
:   Number of principal components to retain when using PCA regularization.

## EXAMPLES

Fit a distortion model using ANTs:

    phantomfit_ANTS.pl phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

Fit with higher-order harmonics and verbose output:

    phantomfit_ANTS.pl -order 7 -min_step 0.5 -verbose \
        phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

Fit using cylindrical coordinates with PCA regularization:

    phantomfit_ANTS.pl -cylindric -pca -pcs 10 -par distortion.par -clobber \
        phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit.pl**(1), **phantomfit_DD.pl**(1)
