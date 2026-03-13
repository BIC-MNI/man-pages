---
section: 1
title: nlfit_f
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# nlfit_f

non-linear fitting at fine resolution step

`nlfit_f <source.mnc> <target.mnc> <input.xfm> <output.xfm> [options]`

## DESCRIPTION

**nlfit_f** is a Perl wrapper script for performing non-linear registration using
**minctracc** at a fine resolution step. It is part of the hierarchical nlfit
suite that performs non-linear registration in a coarse-to-fine progression.

The fine resolution step operates at the smallest deformation grid spacing,
capturing detailed local anatomical differences between the source and target
volumes. This step is typically run after the large (**nlfit_l**) and standard
(**nlfit_s**) resolution steps have already established a coarse deformation field.

The script takes a source volume, a target volume, an initial transformation
(typically the output from a previous coarser step), and produces a refined
non-linear transformation at fine resolution.

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
:   Input transformation file from a previous registration step.

`<output.xfm>`
:   Output refined non-linear transformation file.

## EXAMPLES

Run fine-resolution non-linear fitting after standard step:

    nlfit_f source.mnc target.mnc nlfit_s_output.xfm nlfit_f_output.xfm

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[nlfit_l](nlfit_l) [nlfit_s](nlfit_s) [nlfit_o2](nlfit_o2) [minctracc](minctracc)
