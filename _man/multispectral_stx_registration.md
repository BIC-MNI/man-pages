---
section: 1
title: multispectral_stx_registration
author: Louis Collins
group: Registration Scripts
---
# multispectral_stx_registration

perform stereotaxic registration using multi-spectral MRI data

`multispectral_stx_registration [options] input_files... output.xfm`

## DESCRIPTION

**multispectral_stx_registration** is a script that performs stereotaxic
registration using multiple MRI contrasts (multi-spectral data) such as
T1-weighted, T2-weighted, and PD-weighted volumes simultaneously. By
combining information from multiple contrasts, the registration can achieve
more robust and accurate results than single-contrast registration.

The script coordinates the registration pipeline, applying the appropriate
preprocessing and optimization steps for multi-spectral input data.

## SEE ALSO

[mritotal](mritotal), [bestlinreg.pl](bestlinreg.pl),
[mritotal_suppress](mritotal_suppress)

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by Louis Collins
