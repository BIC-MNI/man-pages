---
section: 1
title: spline_smooth
author: John G. Sled
group: Non-Uniformity Correction
---
# spline_smooth

smooth and extrapolate data in MINC volumes using spline fitting

`spline_smooth [options] <infile> <outfile>`

## DESCRIPTION

**spline_smooth** smooths a MINC volume using tensor B-splines or thin plate
splines. It fits a smooth spline function to the data and can optionally output
a compact field representation for later evaluation with **evaluate_field**.
This tool is a key component of the N3 non-uniformity correction pipeline,
where it is used to produce a smooth estimate of the bias field from sample
points.

## OPTIONS

`-clobber`
:   Overwrite an existing output file.

`-noclobber`
:   Do not overwrite an existing output file (default).

`-verbose`
:   Print progress information.

`-quiet`
:   Do not print progress information.

`-lambda <val>`
:   Set the smoothing parameter controlling the trade-off between fidelity to data and smoothness (default: 0.01).

`-distance <val>`
:   Set the distance between basis functions in mm (default: 60).

`-b_spline`
:   Use tensor B-splines for smoothing (default).

`-tp_spline`
:   Use thin plate splines for smoothing.

`-mask <mask.mnc>`
:   Specify a mask volume defining the region to be smoothed.

`-output_mask <mask.mnc>`
:   Specify a mask defining the region for output.

`-extrapolate`
:   Extrapolate the field outside the mask region.

`-noextrapolate`
:   Do not extrapolate outside the mask region (default).

`-full_support`
:   Use the full support of the basis functions.

`-subsample <n>`
:   Fit to every nth data point (default: 1).

`-compact <file>`
:   Store a compact field representation to the specified file.

`-novolume`
:   Do not write the output volume; only write the compact field.

## EXAMPLES

    spline_smooth -distance 100 -lambda 0.001 input.mnc smoothed.mnc

    spline_smooth -mask brain_mask.mnc -compact field.fld input.mnc smoothed.mnc

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[evaluate_field](evaluate_field), [correct_field](correct_field), [nu_correct](nu_correct), [nu_estimate](nu_estimate)
