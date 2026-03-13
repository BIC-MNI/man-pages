---
section: 1
title: pipeline_relx.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_relx.pl

T2 relaxometry fitting from multiple echo volumes

`pipeline_relx.pl <echo1> <echo2> ... <output> [--mask <mask>]`

## DESCRIPTION

**pipeline_relx.pl** performs T2 relaxometry by fitting an exponential decay
model to multiple echo volumes acquired at different echo times. The script
estimates the T2 relaxation time at each voxel by fitting the signal intensity
decay across echoes.

The input consists of two or more MINC volumes acquired at different echo
times, and the output is a T2 relaxation map. An optional brain mask can
restrict the fitting to the brain region, improving computation time and
reducing noise in non-brain areas.

T2 relaxometry maps are useful for quantitative MRI analysis, tissue
characterization, and detecting pathological changes that alter relaxation
properties.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--mask <mask>`
:   Brain mask to restrict T2 fitting to the brain region.

## EXAMPLES

Fit T2 relaxation from two echo volumes:

    pipeline_relx.pl echo1.mnc echo2.mnc t2_relx.mnc

Fit T2 relaxation from four echo volumes with a mask:

    pipeline_relx.pl echo1.mnc echo2.mnc echo3.mnc echo4.mnc \
      t2_relx.mnc --mask brain_mask.mnc

Fit with verbose output and clobber:

    pipeline_relx.pl echo1.mnc echo2.mnc t2_relx.mnc \
      --mask brain_mask.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[t2_fit](t2_fit), [pipeline_relx_cls.pl](pipeline_relx_cls.pl)
