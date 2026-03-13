---
section: 1
title: nlfit_o2
author: Vladimir S. Fonov
group: EZminc Registration Scripts
---
# nlfit_o2

non-linear fitting optimization pass 2

`nlfit_o2 <source.mnc> <target.mnc> <input.xfm> <output.xfm> [options]`

## DESCRIPTION

**nlfit_o2** is a Perl wrapper script for performing a second optimization pass
of non-linear registration using **minctracc**. It is part of the hierarchical
nlfit suite that performs non-linear registration in a coarse-to-fine progression.

The second optimization pass refines the deformation field produced by the
previous fitting steps (nlfit_l, nlfit_s, nlfit_f) by running additional
optimization iterations. This can improve registration accuracy by further
reducing the residual difference between the source and target volumes.

The script takes a source volume, a target volume, an initial transformation
(typically the output from the fine resolution step), and produces a further
optimized non-linear transformation.

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
:   Input transformation file from a previous fitting step.

`<output.xfm>`
:   Output optimized non-linear transformation file.

## EXAMPLES

Run second optimization pass after fine-resolution fitting:

    nlfit_o2 source.mnc target.mnc nlfit_f_output.xfm nlfit_o2_output.xfm

Run a complete hierarchical non-linear registration pipeline:

    nlfit_l source.mnc target.mnc linear.xfm nl_l.xfm
    nlfit_s source.mnc target.mnc nl_l.xfm nl_s.xfm
    nlfit_f source.mnc target.mnc nl_s.xfm nl_f.xfm
    nlfit_o2 source.mnc target.mnc nl_f.xfm nl_final.xfm

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[nlfit_f](nlfit_f) [nlfit_l](nlfit_l) [nlfit_s](nlfit_s) [minctracc](minctracc)
