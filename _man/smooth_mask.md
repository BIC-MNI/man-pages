---
section: 1
title: smooth_mask
author: David MacDonald
group: Registration Scripts
---
# smooth_mask

smooth a binary mask volume

`smooth_mask [options] input.mnc output.mnc`

## DESCRIPTION

**smooth_mask** is a Perl script that smooths a binary mask volume using
morphological operations. The smoothing reduces jagged edges and small
irregularities in the mask boundary, producing a cleaner mask suitable for
downstream processing such as registration or segmentation.

## SEE ALSO

[mincmorph](mincmorph), [dilate_volume](dilate_volume), [surface_mask](surface_mask)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1993 by David MacDonald
