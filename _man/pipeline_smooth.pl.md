---
section: 1
title: pipeline_smooth.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_smooth.pl

smooth tissue probability maps with optional Jacobian modulation

`pipeline_smooth.pl <cls> <out_wm> <out_gm> <out_csf> [out_lj] [options]`

## DESCRIPTION

**pipeline_smooth.pl** generates smoothed tissue probability maps from a
discrete tissue classification volume. For each tissue class (white matter,
grey matter, cerebrospinal fluid), a binary map is extracted from the
classification and blurred with a Gaussian kernel to produce a smooth
probability map.

When a nonlinear transform is provided via **--xfm**, the tissue maps can be
modulated by the Jacobian determinant of the transformation. This Jacobian
modulation preserves information about local volume differences, producing
maps suitable for voxel-based morphometry (VBM) analysis. The optional
fourth output receives the log-Jacobian-modulated maps.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

`--fwhm <f>`
:   Full-width at half-maximum of the Gaussian smoothing kernel in
    millimetres. Default is 8.

`--xfm <file>`
:   Nonlinear transformation file whose Jacobian determinant is used to
    modulate the tissue probability maps.

## EXAMPLES

Smooth tissue maps with default 8 mm kernel:

    pipeline_smooth.pl classified.mnc wm_smooth.mnc gm_smooth.mnc csf_smooth.mnc

Smooth with 6 mm kernel and Jacobian modulation:

    pipeline_smooth.pl classified.mnc wm_smooth.mnc gm_smooth.mnc \
      csf_smooth.mnc lj_smooth.mnc --fwhm 6 --xfm nl.xfm

Smooth with clobber:

    pipeline_smooth.pl classified.mnc wm_smooth.mnc gm_smooth.mnc \
      csf_smooth.mnc --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_classify.pl](pipeline_classify.pl), [pipeline_dbm.pl](pipeline_dbm.pl)
