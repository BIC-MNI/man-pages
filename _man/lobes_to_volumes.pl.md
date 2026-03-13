---
section: 1
title: lobes_to_volumes.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# lobes_to_volumes.pl

compute lobe volumes from a lobe-segmented MINC volume

`lobes_to_volumes.pl <lobes.mnc> [--xfm <xfm>]`

## DESCRIPTION

**lobes_to_volumes.pl** computes the volumes (in cubic millimetres) of each
labelled brain lobe from a lobe-segmented MINC volume produced by
**lobe_segment**. The volumes are printed to standard output, one label per
line.

If a transformation (`.xfm`) is provided via the `--xfm` option, the voxel
volumes are adjusted according to the Jacobian determinant of the
transformation, allowing the output to reflect volumes in a different
coordinate space (e.g. native space volumes when the labels are in stereotaxic
space).

## OPTIONS

`--xfm <xfm>`
:   Apply the specified transformation to adjust voxel volumes by its Jacobian
    determinant. This is useful for computing native-space volumes from labels
    defined in stereotaxic space.

## EXAMPLES

Compute lobe volumes directly from a labelled volume:

    lobes_to_volumes.pl lobes.mnc

Compute native-space volumes using a stereotaxic transformation:

    lobes_to_volumes.pl lobes.mnc --xfm subject_to_tal.xfm

Save volumes to a file:

    lobes_to_volumes.pl lobes.mnc --xfm subject_to_tal.xfm > volumes.txt

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**lobe_segment.pl**(1), **print_all_labels**(1), **mincstats**(1)
