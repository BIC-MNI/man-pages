---
section: 1
title: lobe_segment.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# lobe_segment.pl

segment brain lobes using atlas-based label propagation

`lobe_segment [options] <to_model_nl.xfm> <to_tal.xfm> <class.mnc> <out_labels.mnc>`

## DESCRIPTION

**lobe_segment** performs stereotaxic lobe segmentation of a classified brain
volume using atlas-based label propagation. It takes as input the nonlinear
transformation to model space, the linear transformation to Talairach space,
and a tissue classification volume (e.g. from **classify**), and produces a
labelled output volume where each voxel is assigned to a brain lobe.

The tool uses atlas templates in the model directory to propagate lobe labels
from the atlas to the subject. A cortical surface mask can optionally be
provided for refined segmentation at grey/white boundaries.

## OPTIONS

`-version`
:   Print version information and exit.

`-surface_mask <obj>`
:   Use the specified cortical surface object as a mask for surface-based
    refinement of lobe boundaries.

`-template <mnc>`
:   Use the specified MINC volume as the atlas template instead of the default.

`-modeldir <dir>`
:   Path to the directory containing atlas label templates.

`-gwcb <g w c b>`
:   Set the label values for grey matter, white matter, CSF, and background
    in the tissue classification input. Default: 2 3 1 0.

`-verbose`
:   Print progress information during processing.

`-debug`
:   Print additional debugging information.

`-clobber`
:   Overwrite existing output files.

`-tmpdir <dir>`
:   Use the specified directory for temporary files.

`-keeptmp`
:   Do not delete temporary files after completion.

## EXAMPLES

Segment lobes from a classified brain volume:

    lobe_segment subject_to_model_nl.xfm subject_to_tal.xfm \
        classify.mnc lobes.mnc

Segment lobes with a custom model directory and surface mask:

    lobe_segment -modeldir /opt/models/lobe_atlas \
        -surface_mask cortex.obj \
        subject_to_model_nl.xfm subject_to_tal.xfm \
        classify.mnc lobes.mnc

Segment with non-default tissue class labels:

    lobe_segment -gwcb 1 2 3 0 -verbose -clobber \
        subject_to_model_nl.xfm subject_to_tal.xfm \
        classify.mnc lobes.mnc

## AUTHOR

Jason Lerch, Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**pipeline_segment.pl**(1), **lobes_to_volumes.pl**(1), **classify**(1)
