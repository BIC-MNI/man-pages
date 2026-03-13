---
section: 1
title: bestlinreg_s2
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# bestlinreg_s2

perform best linear registration (symmetric variant 2)

`bestlinreg_s2 [options] source.mnc target.mnc output.xfm [output.mnc]`

## DESCRIPTION

**bestlinreg_s2** is a variant of the bestlinreg family that uses a
blur+dxyz configuration for its internal multi-scale fitting stages. The
stage schedule differs from both **bestlinreg_s** and **bestlinreg_g**,
providing an alternative convergence profile. It accepts most of the same
options as **bestlinreg_g** (excluding `-notrans`) and produces a linear
`.xfm` transformation with an optional resampled output volume.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite existing output files.

`-fake`
:   Print the commands that would be executed without running them.

`-init_xfm <xfm>`
:   Use the specified transformation as the initial starting estimate.

`-noresample`
:   Do not produce a resampled output volume.

`-source_mask <mask.mnc>`
:   Apply the given binary mask to the source volume during registration.

`-target_mask <mask.mnc>`
:   Apply the given binary mask to the target volume during registration.

`-lsq6`
:   Use a 6-parameter rigid-body model.

`-lsq7`
:   Use a 7-parameter similarity model.

`-lsq9`
:   Use a 9-parameter model. This is the default.

`-lsq12`
:   Use a full 12-parameter affine model.

`-quaternions`
:   Use quaternion-based rotation parametrisation.

`-mi`
:   Use mutual information as the cost function.

`-nmi`
:   Use normalised mutual information as the cost function.

`-xcorr`
:   Use cross-correlation as the cost function.

`-work_dir <dir>`
:   Use the specified directory for intermediate files.

`-sec_source <source2.mnc>`
:   Supply a secondary source volume for multi-channel registration.

`-sec_target <target2.mnc>`
:   Supply a secondary target volume for multi-channel registration.

`-noshear`
:   Disable shear parameters in the affine model.

`-noscale`
:   Disable scale parameters in the affine model.

`-norot`
:   Disable rotation parameters in the affine model.

`-noshift`
:   Disable shift (translation) parameters in the affine model.

`-close`
:   Assume the source and target are already roughly aligned.

## EXAMPLES

Register using the s2 schedule with cross-correlation:

    bestlinreg_s2 -xcorr subject.mnc model.mnc output.xfm

Rigid-body registration with masks:

    bestlinreg_s2 -lsq6 -source_mask src_mask.mnc -target_mask tgt_mask.mnc \
        subject.mnc model.mnc output.xfm output.mnc

## AUTHOR

Claude Lepage, Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**bestlinreg.pl**(1), **bestlinreg_s**(1), **bestlinreg_g**(1), **minctracc**(1)
