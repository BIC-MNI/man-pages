---
section: 1
title: lego_core_extract.pl
author: Vladimir S. Fonov
group: Distortion Correction
---
# lego_core_extract.pl

extract core markers from a LEGO phantom scan

`lego_core_extract.pl <input> <output_core> [output_mask] [options]`

## DESCRIPTION

**lego_core_extract.pl** extracts the core region from a LEGO phantom MRI scan.
The LEGO phantom is a structured phantom used for geometric distortion assessment
in MRI scanners. This tool identifies and isolates the core markers within the
phantom image, producing an output volume containing only the extracted core
region and optionally a binary mask of that region.

The extraction process can include optional denoising, non-uniformity correction
(N3), and settings optimised for 3-Tesla scanners.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--grayscale`
:   Process the input as a grayscale image (do not apply colour-based extraction).

`--nuc`
:   Apply non-uniformity correction (N3) during preprocessing.

`--denoise`
:   Apply denoising to the input before core extraction.

`--3t`
:   Use settings optimised for 3-Tesla MRI scanners.

`--nuc-iter <n>`
:   Number of iterations for non-uniformity correction.

## EXAMPLES

Extract the core from a LEGO phantom scan:

    lego_core_extract.pl phantom.mnc core.mnc

Extract the core with a mask and preprocessing:

    lego_core_extract.pl --denoise --nuc --clobber \
        phantom.mnc core.mnc core_mask.mnc

Extract from a 3T scan with verbose output:

    lego_core_extract.pl --verbose --3t phantom_3t.mnc core.mnc

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**adni_preprocess.pl**(1), **phantomfit.pl**(1), **calc_distortions.pl**(1)
