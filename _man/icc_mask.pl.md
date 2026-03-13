---
section: 1
title: icc_mask.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# icc_mask.pl

create an intra-cranial cavity mask for brain volume estimation

`icc_mask.pl <input.mnc> <output_mask.mnc> --model <model> --icc-model <icc_mask>`

## DESCRIPTION

**icc_mask.pl** generates an intracranial cavity (ICC) mask for a given input
MINC volume. The ICC mask encompasses the entire volume within the skull,
including the brain, ventricles, and CSF spaces. This is useful for estimating
total intracranial volume (ICV), which serves as an important normalisation
factor in volumetric brain studies.

The tool works by performing nonlinear registration between the input volume
and a reference model, then propagating a pre-defined ICC mask from the model
space back to the native space of the input. The `--model` option specifies
the reference anatomical model and the `--icc-model` option specifies the
corresponding ICC mask in model space.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--model <model.mnc>`
:   Path to the reference anatomical model volume.

`--icc-model <icc_mask.mnc>`
:   Path to the ICC mask in the reference model space.

## EXAMPLES

Generate an ICC mask using a standard model:

    icc_mask.pl subject_t1.mnc subject_icc.mnc \
        --model /opt/minc/share/icbm152_model_09c/mni_icbm152_t1_tal_nlin_sym_09c.mnc \
        --icc-model /opt/minc/share/icbm152_model_09c/mni_icbm152_t1_tal_nlin_sym_09c_mask.mnc

Generate an ICC mask with verbose output:

    icc_mask.pl --verbose --clobber subject.mnc icc_mask.mnc \
        --model model.mnc --icc-model model_icc.mnc

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**mincbeast**(1), **pipeline_mritotal.pl**(1), **mincresample**(1)
