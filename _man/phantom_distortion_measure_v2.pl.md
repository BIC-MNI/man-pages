---
section: 1
title: phantom_distortion_measure_v2.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# phantom_distortion_measure_v2.pl

measure geometric distortion using paired phantom scan and mask inputs (version 2)

`phantom_distortion_measure_v2.pl <scan1> <mask1> [<scan2> <mask2> ...] <output.par> <output.xfm> <output.csv>`

## DESCRIPTION

**phantom_distortion_measure_v2.pl** is a revised version of
**phantom_distortion_measure.pl** that accepts paired scan and mask inputs. Each
phantom scan is accompanied by a corresponding binary mask that identifies the
phantom region, eliminating the need for automatic core extraction. The pipeline
performs hierarchical nonlinear registration constrained by spherical harmonics
to measure scanner geometric distortion.

In addition to the `.par` and `.xfm` outputs, this version writes a CSV file
summarizing the distortion measurements, making it easier to integrate results
into automated quality assurance workflows. Support for Elastix-based
registration and brick-structured phantom geometries is available in this version.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--debug`
:   Enable debug mode with additional diagnostic output.

`--clobber`
:   Overwrite existing output files.

`--order <n>`
:   Order of the spherical-harmonic expansion. Default: 5.

`--work_dir <dir>`
:   Specify a working directory for intermediate files.

`--model <dir>`
:   Path to the phantom model directory. This option is required.

`--min_step <f>`
:   Minimum step size in millimetres for the hierarchical registration.
    Default: 2.

`--measure`
:   Only measure distortion without fitting the parametric model.

`--mask <mask.mnc>`
:   Specify an additional mask to restrict the region used for distortion
    measurement.

`--exclude <file>`
:   Specify a file listing regions to exclude from the fit.

`--limit_linear`
:   Limit the linear component of the registration.

`--keep <f>`
:   Fraction of the distortion field to retain after filtering. Default: 1.0.

`--cylindric`
:   Use cylindrical coordinate representation for the distortion model.

`--init <xfm>`
:   Provide an initial transformation for the registration.

`--step_iterations <n>`
:   Number of iterations at each step of the hierarchical registration.

`--out-roi <file>`
:   Write a region-of-interest mask to the specified file.

`--only-roi`
:   Only compute distortion within the specified region of interest.

`--dilate-roi <n>`
:   Dilate the region-of-interest mask by the given number of voxels.

`--pca`
:   Use PCA regularization for the distortion model.

`--pcs <n>`
:   Number of principal components to retain when using PCA regularization.

`--dd`
:   Use Diffeomorphic Demons for the nonlinear registration step.

`--ants`
:   Use ANTs (mincANTS) for the nonlinear registration step.

`--elastix`
:   Use Elastix for the nonlinear registration step.

`--bricks`
:   Enable brick-structured phantom geometry mode for phantoms with a regular
    grid of internal markers.

`--keep-tmp`
:   Do not remove temporary working files after processing.

## EXAMPLES

Measure distortion from a single scan with its mask:

    phantom_distortion_measure_v2.pl phantom.mnc phantom_mask.mnc \
        distortion.par distortion.xfm results.csv \
        --model /path/to/phantom_model --verbose

Measure from multiple paired scans:

    phantom_distortion_measure_v2.pl \
        scan1.mnc mask1.mnc scan2.mnc mask2.mnc \
        distortion.par distortion.xfm results.csv \
        --model /path/to/phantom_model --order 7

Use Elastix registration with brick phantom geometry:

    phantom_distortion_measure_v2.pl phantom.mnc phantom_mask.mnc \
        distortion.par distortion.xfm results.csv \
        --model /path/to/phantom_model --elastix --bricks --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantom_distortion_measure.pl**(1), **phantomfit.pl**(1)
