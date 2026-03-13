---
section: 1
title: voldiff
author: Jason Lerch
group: Classification
---
# voldiff

compare classified volumes and produce a difference volume

`voldiff <input1.mnc> <input2.mnc> <output.mnc>`

## DESCRIPTION

**voldiff** computes the voxel-by-voxel difference between two MINC volumes. For
each voxel, the value in the second volume is subtracted from the value in the
first volume, and the result is stored in the output volume.

This tool is useful for comparing classification results, detecting changes
between time points, evaluating registration accuracy, or computing difference
maps for statistical analysis. The two input volumes must have compatible
dimensions and sampling.

## OPTIONS

voldiff does not accept option flags. All arguments are positional.

`<input1.mnc>`
:   First input MINC volume.

`<input2.mnc>`
:   Second input MINC volume to subtract from the first.

`<output.mnc>`
:   Output MINC volume containing the voxel-wise difference (input1 - input2).

## EXAMPLES

Compute the difference between two volumes:

    voldiff pre_treatment.mnc post_treatment.mnc difference.mnc

Compare two classification results:

    voldiff classify_method1.mnc classify_method2.mnc class_diff.mnc

## AUTHOR

Jason Lerch - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2003 by Jason Lerch

## SEE ALSO

[mincmath](mincmath) [minccalc](minccalc)
