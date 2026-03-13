---
section: 1
title: pipeline_deface_grid.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_deface_grid.pl

generate a random distortion grid for defacing

`pipeline_deface_grid.pl <brain_mask> <output_grid> [options]`

## DESCRIPTION

**pipeline_deface_grid.pl** generates a random deformation grid that can be
applied to the facial region of an MRI volume as part of the defacing process.
Rather than simply zeroing out the face, the random distortion grid scrambles
the facial features, making re-identification impossible while preserving the
overall image appearance.

The script takes a brain mask to determine the protected brain region and
produces a MINC deformation grid file. An optional face mask can be provided
to restrict the distortion to specific facial areas.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--face_mask <file>`
:   A mask volume defining the facial region where the random distortion
    should be applied. If not specified, the face region is determined
    automatically from the brain mask.

## EXAMPLES

Generate a random distortion grid from a brain mask:

    pipeline_deface_grid.pl brain_mask.mnc distortion_grid.mnc

Generate a grid with a custom face mask:

    pipeline_deface_grid.pl brain_mask.mnc distortion_grid.mnc \
      --face_mask face_region.mnc

Overwrite an existing grid:

    pipeline_deface_grid.pl brain_mask.mnc distortion_grid.mnc --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[deface_volume.pl](deface_volume.pl), [make_random_grid.pl](make_random_grid.pl)
