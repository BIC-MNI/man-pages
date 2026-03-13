---
section: 1
title: bestlinreg_g
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# bestlinreg_g

perform best linear registration (generalized variant)

`bestlinreg_g [options] source.mnc target.mnc output.xfm [output.mnc]`

## DESCRIPTION

**bestlinreg_g** is an enhanced variant of **bestlinreg.pl** that adds support
for selectable cost functions and additional transformation constraints. Like
**bestlinreg.pl**, it performs hierarchical multi-scale linear registration
between a source and target MINC volume using **minctracc**, proceeding through
several blur and step-size stages.

This variant allows the user to choose among mutual information, normalised
mutual information, and cross-correlation cost functions. It also provides flags
to individually disable specific affine components (shear, scale, rotation,
translation) for constrained registration. A secondary source/target pair can
be supplied for multi-channel cost evaluation, and a working directory can be
specified for intermediate files.

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
:   Use the specified directory for intermediate files instead of a temporary directory.

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
:   Assume the source and target are already roughly aligned, reducing the search range.

## EXAMPLES

Register using normalised mutual information:

    bestlinreg_g -nmi subject.mnc model.mnc subject_to_model.xfm

Perform a 12-parameter registration with no shear:

    bestlinreg_g -lsq12 -noshear -clobber \
        subject.mnc template.mnc output.xfm output.mnc

Multi-channel registration with a secondary modality:

    bestlinreg_g -mi -sec_source t2.mnc -sec_target t2_model.mnc \
        t1.mnc t1_model.mnc output.xfm

## AUTHOR

Claude Lepage, Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**bestlinreg.pl**(1), **bestlinreg_s**(1), **minctracc**(1), **mritotal**(1)
