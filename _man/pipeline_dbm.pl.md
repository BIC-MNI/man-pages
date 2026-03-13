---
section: 1
title: pipeline_dbm.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_dbm.pl

deformation-based morphometry from nonlinear transforms

`pipeline_dbm.pl <input.xfm> <output_dbm> [options]`

## DESCRIPTION

**pipeline_dbm.pl** performs deformation-based morphometry (DBM) by computing
a smoothed Jacobian determinant map from a nonlinear transformation file. The
resulting DBM map represents local volume changes relative to a reference model,
where values greater than 1 indicate local expansion and values less than 1
indicate local contraction.

The nonlinear transformation is typically produced by **pipeline_nlr.pl** and
maps a subject's brain to a standard template. The Jacobian determinant field
is blurred with a Gaussian kernel whose full-width at half-maximum (FWHM) is
controlled by the **--fwhm** option (default 8 mm).

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--fwhm <f>`
:   Full-width at half-maximum of the Gaussian blurring kernel applied to the
    Jacobian determinant map, in millimetres. Default is 8.

`--model <file>`
:   Reference model volume used to define the output sampling grid.

## EXAMPLES

Compute a DBM map with default 8 mm smoothing:

    pipeline_dbm.pl nl_transform.xfm dbm_output.mnc

Compute a DBM map with 4 mm smoothing:

    pipeline_dbm.pl nl_transform.xfm dbm_output.mnc --fwhm 4

Compute a DBM map with a specific model and clobber:

    pipeline_dbm.pl nl_transform.xfm dbm_output.mnc \
      --model icbm_avg_152_t1_tal_nlin_symmetric_VI.mnc --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_jacobian.pl](pipeline_jacobian.pl), [pipeline_nlr.pl](pipeline_nlr.pl)
