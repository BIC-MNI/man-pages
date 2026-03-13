---
section: 1
title: deface_volume.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# deface_volume.pl

deface (remove facial features from) a MINC volume

`deface_volume.pl <input.mnc> <output.mnc> [options]`

## DESCRIPTION

**deface_volume.pl** removes identifying facial features from a MINC MRI volume
by applying a pseudo-random deformation grid to the face region. The tool
generates (or accepts) a random deformation field, applies it within a face mask
in stereotaxic space, and resamples the input to produce the defaced output. An
edge smoothing kernel blends the deformed region with unmodified brain tissue.

The tool can operate with a pre-computed stereotaxic transformation or compute
one internally. It supports control over the deformation amplitude, smoothing
kernel FWHM, and optional brain/face mask inputs.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--fwhm <f>`
:   Full-width at half-maximum (in mm) of the smoothing kernel applied to the
    random deformation grid. Default: 6.

`--amp <f>`
:   Amplitude (in mm) of the random deformation field. Default: 12.

`--tal_grid <grid>`
:   Use the specified pre-computed deformation grid in stereotaxic space.

`--keep_tmp`
:   Do not delete temporary working files after completion.

`--edge_smooth <f>`
:   FWHM (in mm) of the smoothing kernel used at the boundary between the
    deformed face region and unmodified tissue. Default: 2.

`--model <name>`
:   Name of the stereotaxic model to use.

`--model_dir <dir>`
:   Directory containing the stereotaxic model files.

`--tal_xfm <xfm>`
:   Supply a pre-computed stereotaxic transformation.

`--save_grid <file>`
:   Save the generated random deformation grid to the specified file.

`--brain <mask.mnc>`
:   Supply a brain mask to protect the brain region from deformation.

`--face <mask.mnc>`
:   Supply a custom face mask defining the region to deface.

`--normalize`
:   Normalise intensity values in the output volume.

## EXAMPLES

Deface a volume with default parameters:

    deface_volume.pl subject.mnc subject_defaced.mnc

Deface with higher amplitude and save the deformation grid:

    deface_volume.pl --amp 20 --fwhm 8 --save_grid grid.mnc \
        subject.mnc subject_defaced.mnc

Deface using a pre-computed stereotaxic transform and brain mask:

    deface_volume.pl --tal_xfm subject_to_tal.xfm --brain brain_mask.mnc \
        --clobber subject.mnc subject_defaced.mnc

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**deface_minipipe.pl**(1), **make_random_grid.pl**(1), **mincresample**(1)
