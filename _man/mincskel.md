---
section: 1
title: mincskel
author: David MacDonald
group: Volume Operations
---
# mincskel

compute the skeleton (medial surface) of a white matter partial volume estimate

`mincskel pve_wm.mnc skel_wm.mnc`

## DESCRIPTION

**mincskel** computes the skeleton (medial surface) of a white matter partial
volume estimation map. The input *pve_wm.mnc* is a MINC volume containing
partial volume estimates for white matter, typically produced by a tissue
classification pipeline. The output *skel_wm.mnc* contains the skeletonized
representation, which approximates the medial surface of the white matter.

Skeletonization is useful for measuring white matter thickness and for
extracting the central sheet of white matter structures.

## EXAMPLES

    mincskel pve_wm.mnc skeleton.mnc

## SEE ALSO

[mincmorph](mincmorph), [classify](classify)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
