---
section: 1
title: suppress_fat
author: David MacDonald
group: Registration Scripts
---
# suppress_fat

suppress fat signal in MRI volumes

`suppress_fat [options] input.mnc output.mnc`

## DESCRIPTION

**suppress_fat** is a Perl script that suppresses fat signal in MRI volumes.
Fat signal can interfere with registration and segmentation pipelines, and this
tool reduces its contribution to improve downstream processing results.

This script requires the Perl module **Getopt::Tabular**.

## SEE ALSO

[inormalize](inormalize), [nu_correct](nu_correct)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
