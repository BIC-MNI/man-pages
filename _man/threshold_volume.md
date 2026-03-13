---
section: 1
title: threshold_volume
author: David MacDonald
group: Volume Operations
---
# threshold_volume

create a label volume by thresholding an input MINC volume

`threshold_volume input.mnc labels.mnc|labels.tag min_value max_value label_value [out.mnc] | [min_value2 max_value2] | [-crop] ...`

## DESCRIPTION

**threshold_volume** creates a label volume (or tag file) from an input MINC
volume. Voxels whose intensity values fall between **min_value** and
**max_value** (inclusive) are assigned **label_value** in the output. All other
voxels are set to zero.

The output can be written to a MINC volume or a tag file, depending on the
extension of the second argument.

Multiple threshold ranges can be specified by providing additional
**min_value** and **max_value** pairs on the command line. Each range uses the
same **label_value**.

If **-crop** is specified, the output volume is cropped to the bounding box of
the labelled voxels.

If **out.mnc** is specified as an additional argument, the result is written
to that file instead of overwriting the labels file.

## EXAMPLES

    threshold_volume input.mnc labels.mnc 100 200 1

    threshold_volume input.mnc labels.mnc 100 200 1 -crop

    threshold_volume input.mnc labels.mnc 50 100 1 150 200 2

## SEE ALSO

[mincmath](mincmath), [mincmask](mincmask), [minccalc](minccalc)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
