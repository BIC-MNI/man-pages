---
section: 1
title: mrfseg.pl
author: Vladimir S. Fonov
group: MRF Segmentation
---
# mrfseg.pl

MRF-based tissue segmentation pipeline

`mrfseg.pl <input_t1.mnc> <output.mask> [options]`

## DESCRIPTION

**mrfseg.pl** is a Perl wrapper that runs an MRF (Markov Random Field) based
tissue segmentation pipeline on a T1-weighted MRI volume. The pipeline first
estimates tissue intensity distributions using **gamixture** (Gaussian mixture
modelling), then applies **mrfseg** to perform spatially regularized
classification. The result is a discrete tissue label mask.

An atlas specification can be supplied to provide tissue priors. A brain mask
can be provided to restrict the segmentation to the brain region. A low-resolution
mode is available for faster processing at reduced spatial resolution.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--mask <mask.mnc>`
:   Specify a brain mask to restrict the segmentation region. The default
    value is "default", which uses the mask provided by the atlas.

`--atlas <spec>`
:   Specify an atlas directory or specification file for tissue priors.

`--lowres`
:   Run the segmentation at low resolution for faster processing.

## EXAMPLES

Segment a T1 volume using default settings:

    mrfseg.pl input_t1.mnc output_labels.mnc

Segment with a custom brain mask and verbose output:

    mrfseg.pl input_t1.mnc output_labels.mnc --verbose --mask brain_mask.mnc

Segment using a specific atlas and low-resolution mode:

    mrfseg.pl input_t1.mnc output_labels.mnc --atlas /path/to/atlas --lowres --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**classify**(1), **em_classify**(1), **pipeline_classify.pl**(1)
