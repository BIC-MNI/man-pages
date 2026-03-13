---
section: 1
title: evaluate_field
author: John G. Sled
group: Non-Uniformity Correction
---
# evaluate_field

evaluate a compact spline field representation and write it as a MINC volume

`evaluate_field [options] -like <volume.mnc> <infile.fld> <outfile.mnc>`

## DESCRIPTION

**evaluate_field** evaluates a compact field representation (produced by
**spline_smooth**) on a volume grid and writes the result as a MINC volume. The
**-like** option specifies a reference volume whose sampling grid defines the
output dimensions. This tool is used as part of the N3 non-uniformity correction
pipeline to convert compact spline representations of the bias field into full
MINC volumes.

## OPTIONS

`-clobber`
:   Overwrite an existing output file.

`-noclobber`
:   Do not overwrite an existing output file (default).

`-verbose`
:   Print progress information (default).

`-quiet`
:   Do not print progress information.

`-like <volume.mnc>`
:   Specify the reference volume whose sampling grid the field is evaluated on.

`-mask <mask.mnc>`
:   Specify a mask volume defining the region on which the field is evaluated.

`-byte`
:   Write output with 8-bit integer voxels.

`-short`
:   Write output with 16-bit integer voxels.

`-long`
:   Write output with 32-bit integer voxels.

`-float`
:   Write output with 32-bit floating point voxels.

`-double`
:   Write output with 64-bit floating point voxels.

`-signed`
:   Write output with signed integer voxels.

`-unsigned`
:   Write output with unsigned integer voxels.

## EXAMPLES

    evaluate_field -like template.mnc field.fld output.mnc

    evaluate_field -like template.mnc -mask brain_mask.mnc field.fld output.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[spline_smooth](spline_smooth), [correct_field](correct_field), [nu_correct](nu_correct), [nu_estimate](nu_estimate)
