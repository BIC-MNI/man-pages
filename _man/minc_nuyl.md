---
section: 1
title: minc_nuyl
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# minc_nuyl

Intensity normalization using piece-wise linear histogram matching.

`minc_nuyl [options] <source.mnc> <target.mnc> [output]`

## DESCRIPTION

**minc_nuyl** performs intensity normalization of a source MINC volume to
match the intensity histogram of a target volume using the piece-wise linear
histogram standardization method. The method is based on Nyul, Udupa, and
Zhang (2000), "New Variants of a Method of MRI Scale Standardization"
(IEEE Transactions on Medical Imaging, 19(2):143-150).

The tool can also create a standardized histogram model from a single volume
using the `--chist` option, and apply normalization using a look-up table.

## OPTIONS

`--source-mask` *mask*
:   Apply a mask to the source volume for histogram computation.

`--target-mask` *mask*
:   Apply a mask to the target volume for histogram computation.

`--linear`
:   Use global linear normalization instead of piece-wise linear mapping.

`--steps` *n*
:   Set the number of histogram matching steps (landmarks). Default: 10.

`--fix_zero_padding`
:   Handle zero-padded regions in the input volumes.

`--verbose`
:   Print progress information during processing.

`--ks`
:   Report the Kolmogorov-Smirnov statistic between the normalized and
    target histograms.

`--chist`
:   Create a standardized histogram file from the source volume instead of
    normalizing. In this mode, the second argument is the output histogram
    filename.

`--dump` *lut*
:   Write the intensity mapping look-up table to the specified file.

`--cut-off` *pct*
:   Set the percentile cut-off for histogram matching.

## EXAMPLES

Normalize source to match target intensity:

    minc_nuyl source.mnc target.mnc normalized.mnc

Normalize with brain masks:

    minc_nuyl --source-mask src_mask.mnc --target-mask tgt_mask.mnc \
        source.mnc target.mnc normalized.mnc

Create a standardized histogram:

    minc_nuyl source.mnc model.hist --chist

Normalize with linear mapping:

    minc_nuyl --linear source.mnc target.mnc normalized.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[volume_pol](volume_pol), [inormalize](inormalize)
