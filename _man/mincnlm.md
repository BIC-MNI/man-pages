---
section: 1
title: mincnlm
author: Vladimir S. Fonov
group: Noise Filtering
---
# mincnlm

Non-local means denoising filter for MINC volumes.

`mincnlm [options] <infile.mnc> <outfile.mnc>`

## DESCRIPTION

**mincnlm** applies a non-local means (NLM) denoising filter to a MINC volume.
The implementation is by Pierrick Coupe and supports multiple noise models
including Gaussian, Rician, and Speckle. It can operate in a voxelwise or
block-based mode for improved performance.

The filter computes weighted averages of similar patches within a search
neighborhood, where similarity is measured according to the selected
weighting function.

## OPTIONS

`-sigma` *value*
:   Set the noise standard deviation. Default: 0 (auto-estimate).

`-beta` *value*
:   Set the smoothing parameter that controls filter strength. Default: 1.

`-v` *n*
:   Set the neighborhood connectivity: 1 for 26-connected, 2 for
    124-connected. Default: 1.

`-d` *n*
:   Set the search volume half-size in voxels. Default: 5.

`-w` *n*
:   Set the weighting function: 0 for L2 Gaussian, 1 for Pearson Speckle,
    2 for L2 with Rician bias correction. Default: 0.

`-aniso`
:   Enable anisotropic filtering.

`-block` *n*
:   Enable block-based approach (1) or disable it (0). Default: 1.

`-b_space` *n*
:   Set the block spacing distance. Default: 2.

`-m_min` *value*
:   Set the minimum mean ratio for block matching. Default: 0.95.

`-v_min` *value*
:   Set the minimum variance ratio for block matching. Default: 0.5.

`-mt` *n*
:   Set the number of threads for parallel processing. Default: 4.

`-hallucinate`
:   Enable hallucination mode for reconstructing missing data.

`-verbose`
:   Print progress information during processing.

`-debug`
:   Enable debug output.

`-clobber`
:   Overwrite existing output files.

## EXAMPLES

Denoise a volume with default settings:

    mincnlm input.mnc output.mnc

Denoise with Rician noise model and known noise level:

    mincnlm -w 2 -sigma 15 input.mnc output.mnc

Denoise using 8 threads with increased search radius:

    mincnlm -mt 8 -d 7 input.mnc output.mnc

## AUTHOR

Pierrick Coupe - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Pierrick Coupe

## SEE ALSO

[minc_anlm](minc_anlm), [noise_estimate](noise_estimate)
