---
section: 1
title: pipeline_thomas.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_thomas.pl

tissue-class Jacobian-modulated blurred maps for THOMAS

`pipeline_thomas.pl <cls> <nl_xfm> <jacobian> <out_csf> <out_gm> <out_wm>`

## DESCRIPTION

**pipeline_thomas.pl** generates tissue-class-specific Jacobian-modulated and
blurred maps suitable for use with the THOMAS (Thalamus Optimized Multi-Atlas
Segmentation) pipeline or similar voxel-based analyses. For each tissue class
(CSF, GM, WM), the script extracts a binary mask from the classification,
modulates it by the Jacobian determinant of the nonlinear transformation, and
applies spatial smoothing.

The resulting maps encode both tissue presence and local volume information,
making them suitable for statistical analyses of regional brain volume
differences.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Generate THOMAS tissue maps:

    pipeline_thomas.pl classified.mnc nl.xfm jacobian.mnc \
      csf_thomas.mnc gm_thomas.mnc wm_thomas.mnc

Generate with verbose output and clobber:

    pipeline_thomas.pl classified.mnc nl.xfm jacobian.mnc \
      csf_thomas.mnc gm_thomas.mnc wm_thomas.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_smooth.pl](pipeline_smooth.pl), [pipeline_jacobian.pl](pipeline_jacobian.pl)
