---
section: 1
title: deface_minipipe.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# deface_minipipe.pl

defacing mini-pipeline for anonymizing MRI volumes

`deface_minipipe.pl <T1W_file> [modality2] ... <output_base>`

## DESCRIPTION

**deface_minipipe.pl** runs a complete defacing pipeline to remove identifying
facial features from MRI volumes. It is designed to anonymise structural brain
images for data sharing while preserving the brain region.

The pipeline performs the following steps:

1. Linear registration of the input T1-weighted volume to a stereotaxic model.
2. Optionally, nonlinear registration for improved alignment.
3. Brain extraction using BEaST (Brain Extraction based on nonlocal
   Segmentation Technique).
4. Generation of a face mask in stereotaxic space.
5. Application of a random grid deformation to the face region, producing an
   output volume in which facial features are distorted beyond recognition.

Multiple input modalities can be provided; the pipeline will use the T1W
registration to deface each of them and write results to the output base
directory.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--model-dir <dir>`
:   Directory containing the stereotaxic model files.

`--model <name>`
:   Name of the stereotaxic model to use.

`--nonlinear`
:   Perform nonlinear registration in addition to linear.

`--no-int-norm`
:   Disable intensity normalisation.

`--watermark`
:   Embed a watermark in the defaced volume to indicate it has been processed.

`--xfm <base_xfm>`
:   Supply a pre-computed stereotaxic transformation instead of computing one.

`--brain-mask`
:   Use a pre-existing brain mask instead of running BEaST.

`--keep-tmp`
:   Do not delete temporary working files after completion.

`--keep-real-range`
:   Preserve the real value range of the input volume in the output.

`--beastlib <dir>`
:   Path to the BEaST library directory. This option is required.

`--3t`
:   Use settings optimised for 3-Tesla MRI scanners.

## EXAMPLES

Deface a single T1-weighted volume:

    deface_minipipe.pl --beastlib /opt/minc/share/beast-library-1.1 \
        subject_t1.mnc output_base

Deface T1 and T2 volumes together:

    deface_minipipe.pl --beastlib /opt/minc/share/beast-library-1.1 \
        --verbose --clobber \
        subject_t1.mnc subject_t2.mnc output_base

Use a pre-computed transformation:

    deface_minipipe.pl --beastlib /opt/minc/share/beast-library-1.1 \
        --xfm subject_to_model.xfm \
        subject_t1.mnc output_base

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**deface_volume.pl**(1), **pipeline_deface.pl**(1), **mincbeast**(1)
