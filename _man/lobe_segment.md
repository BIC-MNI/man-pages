---
section: 1
title: lobe_segment
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# lobe_segment

segment brain lobes using atlas-based label propagation

`lobe_segment [options] <classified.mnc> <output_lobes.mnc>`

## DESCRIPTION

**lobe_segment** is a Perl script that segments brain lobes from a classified
brain volume using template-based lobe definitions. It takes a tissue-classified
MINC volume (typically produced by **classify**) and assigns each voxel to one of
the major brain lobes: frontal, parietal, temporal, occipital, and cerebellum.

The segmentation is performed by propagating pre-defined lobe labels from a
template atlas to the input volume. The template lobe definitions are stored
in a model directory and are mapped onto the subject's anatomy using the tissue
classification as a guide.

The output is a label volume where each voxel is assigned an integer value
corresponding to its lobe membership.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite the output file if it already exists.

`-model_dir <dir>`
:   Specify the directory containing template lobe definition files. Defaults to
    the standard minc-toolkit model directory.

## EXAMPLES

Segment brain lobes from a classified volume:

    lobe_segment classified.mnc lobes.mnc

Segment with a custom model directory and verbose output:

    lobe_segment -verbose -clobber -model_dir /opt/models/lobes classified.mnc lobes.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[classify](classify) [pipeline_segment.pl](pipeline_segment.pl)
