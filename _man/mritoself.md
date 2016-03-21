---
section: 1
title: mritoself
author:
- Greg Ward
- Louis Collins
---
# mritoself

mritoself - intra-subject registration of two volumetric data sets
`mritoself <options> <source.mnc> <target.mnc> <xform.xfm>`

## DESCRIPTION

*Mritoself* estimates the linear transformation required to register two 
volumetric data sets from the same subject (intra-subject registration). The 
procedure was designed and tested on MRI data although other modalities can be 
registered as well (but this has not yet been tested).

*Mritoself* estimates the registration transformation in multiple steps, each 
successive step refining the previous fit. Currently, the sequence of 
resamplings, crops, blurs and fits are hard-coded, although there are a number 
of options to force specific fitting strategies for certain types of data.

## Fitting Data

By default, *Mritoself* uses a mutual information objective function evaluated 
on the original (unblurred) data volumes. Optionally, the data can be blurred 
before fitting with the `-blur` option. If the `-gradient` option is specified, 
then the gradient magnitude of the blurred images is used in the fitting 
process.

## Fitting Strategy

A two step fitting process is then applied to calculate the registration 
transformation. The first begins with an identity transformation, 7.3mm steps, 
and a medium-small (3mm) simplex to find an reasonable initial transformation. 
The second (and last) fit is estimated with 4.3mm steps and a small simplex 
(1.5mm).

If an initial transformation is available, it can be used with the `-transform` 
option. This will overide the `-identity` transform used in the first fit 
described above.

*option* <val>: description of option

## Generic options

`-help:` Print summary of command-line options and abort.

## AUTHOR

Greg Ward and Louis Collins

## COPYRIGHT

Copyright (c) 1996 by Greg Ward and Louis Collins
