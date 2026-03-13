---
section: 1
title: bestlinreg.pl
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# bestlinreg.pl

perform best linear registration between two MINC volumes

`bestlinreg.pl [options] source.mnc target.mnc output.xfm [output.mnc]`

## DESCRIPTION

**bestlinreg.pl** performs hierarchical linear registration between a source and
target MINC volume using **minctracc**. The fitting proceeds through a series of
blur levels and step sizes with parameters optimised by Claude Lepage for robust
convergence. The result is a linear transformation (`.xfm`) that maps the source
volume into the space of the target volume. An optional resampled output volume
can also be produced.

The script supports 6-, 7-, 9-, and 12-parameter affine models, defaulting to
9-parameter (rigid body plus independent scaling). Source and target masks can be
supplied to restrict the region used for fitting.

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
:   Do not produce a resampled output volume even if an output filename is given.

`-source_mask <mask.mnc>`
:   Apply the given binary mask to the source volume during registration.

`-target_mask <mask.mnc>`
:   Apply the given binary mask to the target volume during registration.

`-lsq6`
:   Use a 6-parameter rigid-body model (3 rotations, 3 translations).

`-lsq7`
:   Use a 7-parameter similarity model (rigid body plus one global scale).

`-lsq9`
:   Use a 9-parameter model (rigid body plus three independent scales). This is the default.

`-lsq12`
:   Use a full 12-parameter affine model (rigid body, scales, and shears).

`-quaternions`
:   Use quaternion-based rotation parametrisation in minctracc.

## EXAMPLES

Register a subject to an MNI model with the default 9-parameter model:

    bestlinreg.pl subject.mnc mni_icbm152_t1_tal_nlin_sym_09c.mnc subject_to_mni.xfm

Perform a rigid-body registration with an initial transform:

    bestlinreg.pl -lsq6 -init_xfm rough.xfm -clobber \
        subject.mnc target.mnc refined.xfm resampled.mnc

Register with masks on both source and target:

    bestlinreg.pl -source_mask src_mask.mnc -target_mask tgt_mask.mnc \
        src.mnc tgt.mnc output.xfm

## AUTHOR

Claude Lepage, Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**bestlinreg_g**(1), **bestlinreg_s**(1), **minctracc**(1), **mritotal**(1)
