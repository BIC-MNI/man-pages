---
section: 1
title: adni_preprocess.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# adni_preprocess.pl

preprocess ADNI images for distortion correction analysis

`adni_preprocess.pl [options] <input.mnc> <output.mnc>`

## DESCRIPTION

**adni_preprocess.pl** performs preprocessing of ADNI (Alzheimer's Disease
Neuroimaging Initiative) phantom MRI scans to prepare them for geometric
distortion correction analysis. The pipeline includes the following steps:

1. Image denoising to reduce noise in the phantom scan.
2. Non-parametric non-uniformity intensity correction (N3) to correct for
   MRI field inhomogeneity.
3. Centre-of-mass calculation to align the phantom to a standard position.
4. Intensity normalisation.

The resulting preprocessed volume is suitable for input to downstream distortion
analysis tools such as **phantomfit.pl**.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

## EXAMPLES

Preprocess an ADNI phantom scan:

    adni_preprocess.pl input_phantom.mnc preprocessed.mnc

Preprocess with verbose output, overwriting any existing result:

    adni_preprocess.pl --verbose --clobber raw_phantom.mnc clean_phantom.mnc

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**phantomfit.pl**(1), **lego_core_extract.pl**(1), **nu_correct**(1)
