---
section: 1
title: cmpxfm
author: Louis Collins
group: Registration
---
# cmpxfm

compare two MNI linear transform files element-by-element

`cmpxfm [options] xfm1 xfm2`

## DESCRIPTION

`cmpxfm` reads two MNI `.xfm` files containing linear transforms and
compares them element-by-element. It exits with success (status 0) if no
element differs from the corresponding element by more than a specified
tolerance, or with failure (status 1) if any element exceeds the tolerance.

Separate tolerances can be specified for the 3x3 rotation/scale matrix
elements and the 3x1 translation vector. The default tolerance for both is
the square root of the single-precision floating-point epsilon
(approximately 0.000345).

This tool is primarily useful for testing and validation of registration
pipelines.

## OPTIONS

`-linear_tolerance` value
:   Absolute tolerance for comparing the 3x3 rotation/scale matrix elements.
    Default: ~0.000345.

`-translation_tolerance` value
:   Absolute tolerance for comparing the translation vector elements.
    Default: ~0.000345.

`-show_max`
:   Show the maximum deviation found across all matrix elements.

`-show_all`
:   Show all element-by-element deviations.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXIT STATUS

0
:   All matrix elements are within the specified tolerance.

1
:   At least one matrix element differs by more than the specified tolerance.

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[xfm2param](xfm2param) [param2xfm](param2xfm) [xfmconcat](xfmconcat)
