---
section: 1
title: mritotal_suppress
author: Louis Collins
group: Registration Scripts
---
# mritotal_suppress

suppress fat signal from MRI data during mritotal registration

`mritotal_suppress [options] input.mnc output.xfm`

## DESCRIPTION

**mritotal_suppress** is a Perl script that performs stereotaxic
registration using **mritotal** with fat signal suppression preprocessing.
It suppresses the fat signal in MRI data before running the linear
registration, which improves registration accuracy in scans where bright
fat signal can interfere with intensity-based registration algorithms.

This script requires the **Getopt::Tabular** Perl module.

## SEE ALSO

[mritotal](mritotal), [bestlinreg.pl](bestlinreg.pl),
[suppress_fat](suppress_fat)

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by Louis Collins
