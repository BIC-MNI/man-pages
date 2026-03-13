---
section: 1
title: xfmdecomp
author: Andrew Janke
group: Miscellaneous Tools
---
# xfmdecomp

decompose a .xfm transformation into rotation, translation, scale, and shear

`xfmdecomp <input.xfm>`

## DESCRIPTION

**xfmdecomp** is a Perl script that decomposes a linear MNI `.xfm` transformation
file into its constituent geometric components: rotation angles, scale factors,
shear parameters, and translation offsets. The decomposed parameters are printed
to standard output.

This is useful for inspecting registration results, verifying that transformations
are within expected ranges, and extracting specific geometric parameters for
analysis or reporting.

The decomposition extracts:

- **Rotations**: angles around the x, y, and z axes (in degrees)
- **Translations**: offsets along the x, y, and z axes (in millimetres)
- **Scales**: scaling factors along the x, y, and z axes
- **Shears**: shear parameters

Only linear (affine) transformations can be decomposed. Non-linear grid
transformations are not supported.

## OPTIONS

xfmdecomp does not accept option flags. The single argument is the transform
file to decompose.

`<input.xfm>`
:   Input MNI transformation file containing a linear (affine) transform.

## EXAMPLES

Decompose a linear transformation:

    xfmdecomp registration.xfm

Save the decomposition to a file:

    xfmdecomp registration.xfm > params.txt

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[xfm2param](xfm2param) [param2xfm](param2xfm) [xfmtool](xfmtool)
