---
section: 1
title: phantomfit.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# phantomfit.pl

hierarchical nonlinear fitting constrained by spherical harmonics using minctracc

`phantomfit.pl [options] source.mnc target.mnc fit_mask.mnc estimate_mask.mnc [...] output.xfm`

## DESCRIPTION

**phantomfit.pl** performs hierarchical nonlinear registration between a source
and target MINC volume using **minctracc**, with the resulting deformation field
constrained to lie within a spherical-harmonic basis. This produces a smooth,
low-frequency parametric distortion model suitable for characterizing MRI
scanner geometric distortion.

The fitting proceeds through multiple resolution levels, from coarse to fine,
with the spherical-harmonic order increasing at each level. Two masks are
required: a fit mask defining the region over which the registration is
optimized, and an estimate mask defining the region over which the distortion
parameters are estimated. Additional mask pairs can be provided for multi-region
fitting. PCA-based regularization can be applied to constrain the solution space
using a pre-computed distortion basis.

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

`-weight <f>`
:   Weight for the similarity term in the registration objective. Default: 1.

`-stiffness <f>`
:   Stiffness regularization weight for the minctracc registration. Default: 0.4.

`-similarity <f>`
:   Similarity cost function weight for the minctracc registration. Default: 0.3.

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

Fit a distortion model with default settings:

    phantomfit.pl phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

Fit with higher-order harmonics and custom stiffness:

    phantomfit.pl -order 7 -stiffness 0.2 -min_step 0.5 -verbose \
        phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

Fit using cylindrical coordinates with PCA regularization:

    phantomfit.pl -cylindric -pca -pcs 10 -par distortion.par -clobber \
        phantom_scan.mnc phantom_model.mnc \
        fit_mask.mnc estimate_mask.mnc output.xfm

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit_ANTS.pl**(1), **phantomfit_DD.pl**(1), **phantomfit_elastix.pl**(1)
