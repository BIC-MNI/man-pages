---
section: 1
title: compute_icbm_vols
author: David MacDonald
group: Registration Scripts
---
# compute_icbm_vols

compute ICBM volumes from a classified image

`compute_icbm_vols classified_image.mnc`

## DESCRIPTION

`compute_icbm_vols` is a script that computes brain lobe volumes from a
tissue-classified MINC image using ICBM atlas labels. It outputs the
volume measurements for each brain region to standard output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`classified_image.mnc`
:   The input tissue-classified MINC image.

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincstats](mincstats) [classify](classify)
