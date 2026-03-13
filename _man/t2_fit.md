---
section: 1
title: t2_fit
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# t2_fit

Fit T2 relaxation curves from multiple echo images.

`t2_fit [options] <input1> ... <inputn> <output>`

## DESCRIPTION

**t2_fit** fits T2 relaxation curves from a series of multiple echo time
MINC volumes acquired at different echo times. The tool estimates the T2
relaxation time at each voxel by fitting an exponential decay model to the
multi-echo data, producing a T2 map as output.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--threshold` *f*
:   Set the background intensity threshold. Voxels with intensity below this
    value are excluded from fitting.

`--t2_threshold` *f*
:   Set the maximum T2 threshold. Fitted T2 values above this limit are
    clamped or excluded.

`--mask` *minc_file*
:   Restrict the T2 fitting to voxels within the specified binary mask.

## EXAMPLES

Fit T2 from four echo images:

    t2_fit echo1.mnc echo2.mnc echo3.mnc echo4.mnc t2_map.mnc

Fit T2 with a brain mask and background threshold:

    t2_fit --mask brainmask.mnc --threshold 100 echo1.mnc echo2.mnc echo3.mnc t2_map.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mincmath](mincmath), [minccalc](minccalc)
