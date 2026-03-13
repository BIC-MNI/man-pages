---
section: 1
title: xfmtool
author: Louis Collins
group: Registration
---
# xfmtool

manipulate MNI transformation files

`xfmtool <operation> [args]`

## DESCRIPTION

**xfmtool** is a Perl script for manipulating MNI `.xfm` transformation files.
It provides several operations for combining, inverting, and extracting
transformations without invoking separate tools for each operation.

Supported operations include:

- **compose**: Concatenate two or more transformations into a single combined
  transformation (equivalent to sequential application)
- **invert**: Compute the inverse of a transformation
- **extract**: Extract a specific transformation from a compound transform file

This tool provides a convenient single-command interface for common transform
manipulation tasks that would otherwise require separate calls to xfmconcat,
xfminvert, etc.

## OPTIONS

`<operation>`
:   The operation to perform. One of: compose, invert, extract.

For **compose**:

`xfmtool compose <xfm1> <xfm2> [xfm3 ...] <output.xfm>`
:   Concatenate transformations in order and write the result.

For **invert**:

`xfmtool invert <input.xfm> <output.xfm>`
:   Compute and write the inverse transformation.

For **extract**:

`xfmtool extract <input.xfm> <output.xfm>`
:   Extract a transformation component from a compound transform file.

## EXAMPLES

Compose two transformations:

    xfmtool compose linear.xfm nonlinear.xfm combined.xfm

Invert a transformation:

    xfmtool invert forward.xfm inverse.xfm

## AUTHOR

Louis Collins, Peter Neelin - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Peter Neelin

## SEE ALSO

[xfmconcat](xfmconcat) [xfminvert](xfminvert) [xfmdecomp](xfmdecomp)
