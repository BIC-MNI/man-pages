---
section: 1
title: itk_distance
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_distance

calculate a distance transform on a volume

`itk_distance <input> <output> [options]`

## DESCRIPTION

**itk_distance** computes a distance map from a binary or labelled input volume
using the Danielsson distance transform algorithm from the Insight Toolkit (ITK).
Each voxel in the output volume contains the Euclidean distance (in voxel units)
to the nearest foreground voxel in the input.

By default the unsigned distance is computed, where all output values are
non-negative. With the `--signed` option, voxels inside the foreground region
receive negative distance values, producing a signed distance field suitable
for level-set methods and surface reconstruction.

When the input contains multiple labels, use `--label` to select a specific
label value as the foreground for the distance computation.

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--signed`
:   Compute a signed distance map. Voxels inside the object receive negative distances and voxels outside receive positive distances.

`--byte`
:   Store output voxels as unsigned 8-bit bytes.

`--short`
:   Store output voxels as signed 16-bit short integers.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

`--label` *n*
:   Use label value *n* as the foreground for the distance computation. Voxels with this label are treated as the object; all other voxels are background.

## EXAMPLES

Compute an unsigned distance map from a binary mask:

    itk_distance mask.mnc distance.mnc --float

Compute a signed distance field:

    itk_distance mask.mnc signed_dist.mnc --signed --float

Compute a distance map for a specific label:

    itk_distance labels.mnc dist_label3.mnc --label 3 --float --clobber

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_morph](itk_morph), [mincmorph](mincmorph), [minccalc](minccalc), [itk_resample](itk_resample)
