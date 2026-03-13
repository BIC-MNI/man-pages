---
section: 1
title: make_random_grid.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# make_random_grid.pl

generate a random deformation grid for testing

`make_random_grid.pl <sample.mnc> <output_grid> [options]`

## DESCRIPTION

**make_random_grid.pl** generates a pseudo-random deformation grid in MINC
format. The grid has the same sampling geometry as the input sample volume. The
deformation vectors at each voxel are drawn from a random distribution and then
smoothed with a Gaussian kernel. This tool is primarily used for generating
deformation fields for defacing (see **deface_volume.pl**) or for testing
nonlinear registration pipelines.

The amplitude and smoothness of the deformation field can be controlled via
command-line options. An optional mask can restrict the non-zero deformation
region.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--amplitude <f>`
:   Peak amplitude (in mm) of the random deformation vectors. Default: 1.0.

`--fwhm <f>`
:   Full-width at half-maximum (in mm) of the Gaussian smoothing kernel applied
    to the random field. Default: 10.

`--keep_tmp`
:   Do not delete temporary working files after completion.

`--mask <mask.mnc>`
:   Restrict non-zero deformation to the region defined by the given binary mask.

`--byte`
:   Store the output grid with byte (8-bit) precision instead of the default
    floating-point precision.

`--edge_smooth <f>`
:   FWHM (in mm) of the smoothing kernel applied at the boundary between the
    deformed and undeformed regions when a mask is used.

## EXAMPLES

Generate a random deformation grid matching the geometry of a sample volume:

    make_random_grid.pl sample.mnc random_grid.mnc

Generate a high-amplitude grid for defacing:

    make_random_grid.pl --amplitude 12 --fwhm 6 \
        sample.mnc deface_grid.mnc

Generate a masked deformation field:

    make_random_grid.pl --mask face_mask.mnc --amplitude 10 \
        --edge_smooth 3 --clobber sample.mnc masked_grid.mnc

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**deface_volume.pl**(1), **pipeline_deface_grid.pl**(1), **mincresample**(1)
