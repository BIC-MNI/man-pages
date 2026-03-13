---
section: 1
title: itk_split_labels
author: Vladimir S. Fonov
group: Patch-Based Morphology
---
# itk_split_labels

Split discrete label volume into per-label probability volumes with anti-aliasing.

`itk_split_labels <input> <output_XXXX.mnc> [options]`

## DESCRIPTION

**itk_split_labels** splits a discrete label volume into separate per-label
volumes. The output filename must contain a printf-style format specifier
(e.g., `XXXX` or `%04d`) which is replaced by the label number for each
output file.

By default, the tool produces binary masks for each label. When anti-aliasing
is enabled (`--aa`), the label boundaries are smoothed to produce continuous
probability maps rather than hard binary masks, which is useful for
subsequent interpolation or probabilistic analysis. Optional Gaussian
blurring and expit (logistic) sharpening can be applied to the probability
maps.

Labels can be remapped using a lookup table or relabel file before splitting.

## OPTIONS

`--clobber`
:   Overwrite output files if they already exist.

`--order` *n*
:   B-spline interpolation order for resampling (default: 2).

`--uniformize` *step*
:   Uniformize the volume to the given step size before splitting.

`--unistep` *step*
:   Set a uniform step size for the output volumes.

`--byte`
:   Store output voxels as unsigned byte.

`--short`
:   Store output voxels as short integer.

`--float`
:   Store output voxels as single-precision floating point.

`--relabel` *map.txt*
:   Relabel input labels according to the mapping in the specified text file.

`--lut` *map.txt*
:   Apply a lookup table from the specified text file.

`--lut-string`
:   Interpret the LUT argument as a string rather than a file path.

`--aa`, `--antialias`
:   Enable anti-aliased label splitting to produce smooth probability maps.

`--blur` *fwhm*
:   Apply Gaussian blurring with the specified full-width at half-maximum (mm).

`--expit` *beta*
:   Apply expit (logistic) sharpening with the given beta parameter.

`--normalize`
:   Normalize probability maps so they sum to 1.0 at each voxel.

`--missing` *max*
:   Maximum number of missing labels to tolerate.

`--layers` *n*
:   Number of anti-aliasing layers (default: 4).

## EXAMPLES

    # Split labels into binary masks
    itk_split_labels labels.mnc label_%04d.mnc

    # Split with anti-aliasing for smooth probability maps
    itk_split_labels labels.mnc prob_%04d.mnc --aa --float

    # Split with relabelling and normalization
    itk_split_labels labels.mnc prob_%04d.mnc --relabel remap.txt \
        --aa --normalize --float

    # Split with blurring and expit sharpening
    itk_split_labels labels.mnc prob_%04d.mnc --aa --blur 2.0 --expit 5.0

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[itk_merge_labels](itk_merge_labels) ,
[itk_merge_discrete_labels](itk_merge_discrete_labels)
