---
section: 1
title: xfm_normalize.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# xfm_normalize.pl

normalize an XFM or grid transform to a standard uniform axis-aligned format

`xfm_normalize.pl <input.xfm|input.mnc> <output.xfm> [options]`

## DESCRIPTION

**xfm_normalize.pl** normalizes an XFM transformation file or a MINC grid
volume to a standard representation on a uniform, axis-aligned grid. This is
useful for converting grid transforms with irregular sampling or oblique axes
into a canonical form that is compatible with tools that expect regular grids.

The input can be either an `.xfm` file containing a grid transform or a `.mnc`
file representing a deformation field directly. The output is always an `.xfm`
file with an associated grid volume resampled to uniform spacing. A reference
volume can be specified with `--like` to define the output sampling grid.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--like <mnc>`
:   Specify a reference MINC volume whose sampling grid defines the output
    grid geometry (extent, step, and start values).

`--step <f>`
:   Isotropic step size in millimetres for the output grid.

`--exact`
:   Preserve exact grid values without smoothing or interpolation artifacts.

`--invert`
:   Invert the transformation before writing the output.

## EXAMPLES

Normalize an XFM to a uniform grid:

    xfm_normalize.pl input.xfm output.xfm

Normalize with a specific step size and reference volume:

    xfm_normalize.pl input.xfm output.xfm --step 1.0 --like reference.mnc

Normalize and invert a grid transform:

    xfm_normalize.pl input.xfm output.xfm --invert --clobber --verbose

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**xfm2def**(1), **xfmconcat**(1)
