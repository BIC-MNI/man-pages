---
section: 1
title: mincmorph
author: Andrew Janke
group: MINC Core Tools
---
# mincmorph

perform morphological operations on MINC volumes

`mincmorph [options] <in.mnc> <out.mnc>`

## DESCRIPTION

**mincmorph** performs mathematical morphology operations on MINC volumes.
Supported operations include erosion, dilation, median dilation, opening,
closing, low-pass and high-pass filtering, convolution, distance transform,
and connected component grouping. Operations can be applied individually or
composed in sequence using the **-successive** option with single-character
operation codes. Several structuring element kernels are available, including
2D 4-connected, 2D 8-connected, 3D 6-connected (default), and 3D
26-connected, or a custom kernel file can be specified.

## OPTIONS

`-filetype`
:   Use the input file type for the output.

`-byte`
:   Store output with 8-bit integer voxels.

`-short`
:   Store output with 16-bit integer voxels.

`-int`
:   Store output with 32-bit integer voxels.

`-float`
:   Store output with 32-bit floating point voxels.

`-double`
:   Store output with 64-bit floating point voxels.

`-signed`
:   Store output with signed integer voxels.

`-unsigned`
:   Store output with unsigned integer voxels.

`-2D04`
:   Use a 2D 4-connected structuring element.

`-2D08`
:   Use a 2D 8-connected structuring element.

`-3D06`
:   Use a 3D 6-connected structuring element (default).

`-3D26`
:   Use a 3D 26-connected structuring element.

`-kernel <file.kern>`
:   Use a custom kernel file as the structuring element.

`-floor`
:   Set the lower threshold for foreground/background classification.

`-ceil`
:   Set the upper threshold for foreground/background classification.

`-range`
:   Set a range of values for foreground/background classification.

`-foreground`
:   Set the foreground output value (default: 1).

`-background`
:   Set the background output value (default: 0).

`-binarise`
:   Binarise the volume using the foreground/background thresholds.

`-clamp`
:   Clamp voxel values to the specified range.

`-pad`
:   Pad the volume with background values.

`-erosion`
:   Perform morphological erosion.

`-dilation`
:   Perform morphological dilation.

`-median_dilation`
:   Perform median dilation.

`-open`
:   Perform morphological opening (erosion followed by dilation).

`-close`
:   Perform morphological closing (dilation followed by erosion).

`-lowpass`
:   Apply a low-pass filter using the structuring element.

`-highpass`
:   Apply a high-pass filter using the structuring element.

`-convolve`
:   Convolve the volume with the structuring element.

`-distance`
:   Compute the distance transform.

`-group`
:   Label connected components.

`-successive <string>`
:   Apply a sequence of operations specified by single-character codes: B (binarise), K (clamp), P (pad), E (erosion), D (dilation), M (median dilation), O (open), C (close), L (lowpass), H (highpass), X (convolve), F (distance/feature), G (group), R (read kernel), W (write), I (invert).

## EXAMPLES

    mincmorph -erosion input.mnc eroded.mnc

    mincmorph -3D26 -dilation input.mnc dilated.mnc

    mincmorph -successive BEDD input.mnc result.mnc

    mincmorph -kernel custom.kern -close input.mnc closed.mnc

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2000 by Andrew Janke

## SEE ALSO

[mincmath](mincmath), [mincresample](mincresample), [minccalc](minccalc), [mincdefrag](mincdefrag)
