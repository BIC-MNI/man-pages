---
section: 1
title: calc_distortions.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# calc_distortions.pl

calculate geometric distortion fields from phantom measurements

`calc_distortions.pl <phantom.mnc> <model_base> <output.xfm> [options]`

## DESCRIPTION

**calc_distortions.pl** calculates a geometric distortion field from tag files
derived from phantom MRI scans. It compares measured tag point positions in the
phantom scan against known model tag positions to produce a deformation field
(`.xfm`) that characterises scanner geometric distortions.

**Note:** This tool is considered obsolete. For current distortion correction
workflows, see **phantomfit.pl**.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--coeff <file>`
:   Read distortion correction coefficients from the specified file.

`--spacing <n>`
:   Set the tag point spacing in millimetres. Default: 2.

`--tags <file>`
:   Use the specified file as the measured tag point file instead of
    auto-detecting from the phantom scan.

`--model_tags <file>`
:   Use the specified file as the model (ideal) tag point file.

`--skip_grid`
:   Skip the generation of the grid deformation field.

`--align_xfm <xfm>`
:   Apply the specified alignment transformation before computing distortions.

## EXAMPLES

Compute a distortion field from a phantom scan:

    calc_distortions.pl phantom.mnc model_base distortion.xfm

Compute distortions with custom tag files and 3 mm spacing:

    calc_distortions.pl --spacing 3 --tags measured.tag --model_tags ideal.tag \
        phantom.mnc model_base distortion.xfm

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit.pl**(1), **adni_preprocess.pl**(1)
