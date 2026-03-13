---
section: 1
title: nlfit_s
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# nlfit_s

non-linear fitting at standard resolution step

`nlfit_s <source.mnc> <target.mnc> <input.xfm> <output.xfm> [options]`

## DESCRIPTION

**nlfit_s** is a Perl wrapper script for performing non-linear registration using
**minctracc** at a standard (medium) resolution step. It is part of the
hierarchical nlfit suite that performs non-linear registration in a coarse-to-fine
progression.

The standard resolution step uses an intermediate deformation grid spacing,
capturing moderate anatomical differences between the source and target volumes.
This step is typically run after the large resolution step (**nlfit_l**) and
before the fine resolution step (**nlfit_f**).

The script takes a source volume, a target volume, an initial transformation
(typically the output from the large resolution step), and produces a refined
non-linear transformation at standard resolution.

## OPTIONS

Options are passed through to minctracc. Common options include:

`-verbose`
:   Print progress information during fitting.

`-clobber`
:   Overwrite existing output files.

`<source.mnc>`
:   Source MINC volume to be registered.

`<target.mnc>`
:   Target MINC volume to register to.

`<input.xfm>`
:   Input transformation file from the large resolution step.

`<output.xfm>`
:   Output non-linear transformation file at standard resolution.

## EXAMPLES

Run standard-resolution non-linear fitting after large step:

    nlfit_s source.mnc target.mnc nlfit_l_output.xfm nlfit_s_output.xfm

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[nlfit_f](nlfit_f) [nlfit_l](nlfit_l) [nlfit_o2](nlfit_o2) [minctracc](minctracc)
