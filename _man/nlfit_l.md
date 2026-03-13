---
section: 1
title: nlfit_l
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# nlfit_l

non-linear fitting at large/coarse resolution step

`nlfit_l <source.mnc> <target.mnc> <input.xfm> <output.xfm> [options]`

## DESCRIPTION

**nlfit_l** is a Perl wrapper script for performing non-linear registration using
**minctracc** at a large (coarse) resolution step. It is part of the hierarchical
nlfit suite that performs non-linear registration in a coarse-to-fine progression.

The large resolution step uses the widest deformation grid spacing, capturing
only broad global shape differences between the source and target volumes. This
is typically the first non-linear step run after an initial linear registration,
and its output serves as the starting point for the standard (**nlfit_s**) and
fine (**nlfit_f**) resolution steps.

The script takes a source volume, a target volume, an initial transformation
(typically a linear transform), and produces a coarse non-linear transformation.

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
:   Input transformation file (typically a linear registration).

`<output.xfm>`
:   Output coarse non-linear transformation file.

## EXAMPLES

Run large-resolution non-linear fitting from an initial linear transform:

    nlfit_l source.mnc target.mnc linear.xfm nlfit_l_output.xfm

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[nlfit_f](nlfit_f) [nlfit_s](nlfit_s) [nlfit_o2](nlfit_o2) [minctracc](minctracc)
