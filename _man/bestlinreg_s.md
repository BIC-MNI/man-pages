---
section: 1
title: bestlinreg_s
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# bestlinreg_s

perform best linear registration (symmetric variant)

`bestlinreg_s [options] source.mnc target.mnc output.xfm [output.mnc]`

## DESCRIPTION

**bestlinreg_s** is a variant of **bestlinreg_g** that uses a different internal
blur and tolerance schedule during the hierarchical multi-scale fitting stages.
The altered schedule is designed to provide improved convergence behaviour for
certain registration scenarios. It accepts the same options as **bestlinreg_g**
and produces the same output: a linear `.xfm` transformation and an optional
resampled volume.

Like **bestlinreg_g**, it supports selectable cost functions (mutual information,
normalised mutual information, cross-correlation), secondary source/target
channels, and individual constraints on affine transformation components.

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

`-notrans`
:   Equivalent to disabling all translation parameters.

`-close`
:   Assume the source and target are already roughly aligned.

## EXAMPLES

Standard registration with the symmetric schedule:

    bestlinreg_s subject.mnc model.mnc subject_to_model.xfm

Registration with NMI cost function and a resampled output:

    bestlinreg_s -nmi -clobber subject.mnc model.mnc output.xfm output.mnc

## AUTHOR

Claude Lepage, Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**bestlinreg.pl**(1), **bestlinreg_g**(1), **bestlinreg_s2**(1), **minctracc**(1)
