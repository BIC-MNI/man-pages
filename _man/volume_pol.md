---
section: 1
title: volume_pol
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# volume_pol

Polynomial intensity normalization between volumes.

`volume_pol [options] <input> <template> [output_file]`

## DESCRIPTION

**volume_pol** performs polynomial intensity normalization of an input MINC
volume to match the intensity distribution of a template volume. The tool
fits a polynomial mapping function between the joint intensity histograms
of the input and template, producing a normalized output volume or printing
the polynomial coefficients.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--quiet`
:   Suppress all non-essential output.

`--clobber`
:   Overwrite existing output files.

`--source_mask` *mask*
:   Apply a mask to the input (source) volume for histogram computation.

`--target_mask` *mask*
:   Apply a mask to the template (target) volume for histogram computation.

`--order` *n*
:   Set the polynomial order for the intensity mapping.

`--hist` *histogram.dat*
:   Write the histogram data to the specified file.

`--joint` *joint_histogram*
:   Write the joint histogram to the specified file.

`--expfile` *file*
:   Write the polynomial expression to the specified file.

`--min` *min*
:   Set the minimum intensity value for histogram computation.

`--max` *max*
:   Set the maximum intensity value for histogram computation.

`--noclamp`
:   Do not clamp output values to the input range.

`--kl`
:   Report the Kullback-Leibler divergence between the normalized and
    target histograms.

`--ks`
:   Report the Kolmogorov-Smirnov statistic between the normalized and
    target histograms.

## EXAMPLES

Normalize input to match template intensity:

    volume_pol input.mnc template.mnc normalized.mnc

Normalize with masks and polynomial order 4:

    volume_pol --source_mask src_mask.mnc --target_mask tgt_mask.mnc \
        --order 4 input.mnc template.mnc normalized.mnc

Save the joint histogram:

    volume_pol --joint joint_hist.dat input.mnc template.mnc normalized.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[minc_nuyl](minc_nuyl), [inormalize](inormalize)
