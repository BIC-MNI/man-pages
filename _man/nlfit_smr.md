---
section: 1
title: nlfit_smr
author: Louis Collins
group: Registration Scripts
---
# nlfit_smr

perform non-linear fitting with surface-based multi-resolution

`nlfit_smr [options] source.mnc target.mnc output.xfm`

## DESCRIPTION

**nlfit_smr** is a Perl script that performs non-linear registration using
a surface-based multi-resolution strategy. The script drives a series of
non-linear fitting steps at progressively finer resolutions to compute a
deformation field that maps the source volume to the target volume.

The multi-resolution approach starts with coarse deformations and refines
them at each level, which improves both robustness and accuracy of the
final registration. The output is an XFM transform file containing the
non-linear deformation.

## SEE ALSO

[minctracc](minctracc), [nlfit_s](nlfit_s), [nlfit_o2](nlfit_o2),
[bestlinreg.pl](bestlinreg.pl)

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by Louis Collins
