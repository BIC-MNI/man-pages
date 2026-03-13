---
section: 1
title: mincmask
author: David MacDonald
group: Volume Operations
---
# mincmask

apply a binary mask to a MINC volume

`mincmask [options] <inputfile> <maskfile> <outputfile>`

## DESCRIPTION

**mincmask** applies a binary mask to a MINC volume. By default, voxels
where the mask value is zero are set to zero in the output, and voxels
where the mask is non-zero are copied from the input. The **-invert_mask**
option reverses this behaviour, erasing voxels where the mask is non-zero.

When the **-normalize** option is used, the output volume is intensity
normalized within the masked region.

## OPTIONS

`-clobber`
:   Overwrite the output file if it already exists.

`-no_clobber`
:   Do not overwrite the output file if it already exists. This is the
    default behaviour.

`-invert_mask`
:   Invert the mask so that voxels where the mask equals 1 are erased
    instead of preserved.

`-normalize`
:   Intensity normalize the result within the masked region.

`-verbose`
:   Print progress information during processing.

`-quiet`
:   Suppress progress information.

`-debug`
:   Print debugging information.

## EXAMPLES

Apply a mask to a volume:

    mincmask brain.mnc mask.mnc masked_brain.mnc

Apply an inverted mask with clobber:

    mincmask -clobber -invert_mask brain.mnc mask.mnc output.mnc

Apply a mask and normalize the result:

    mincmask -normalize brain.mnc mask.mnc normalized.mnc

## SEE ALSO

[mask_volume](mask_volume), [mask_values](mask_values), [mincmath](mincmath)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
