---
section: 1
title: volume_denoise.pl
author: Vladimir S. Fonov
group: EZminc Utility Scripts
---
# volume_denoise.pl

NLM-based volume denoising with automatic noise estimation

`volume_denoise.pl <input.mnc> <output.mnc> [options]`

## DESCRIPTION

**volume_denoise.pl** denoises a MINC volume using Non-Local Means (NLM)
filtering. The script automatically estimates the noise level from the input
volume and applies the NLM filter with the estimated or user-adjusted noise
parameter. The beta parameter controls the degree of smoothing relative to the
estimated noise level.

Multi-threaded execution is supported for faster processing on multi-core
systems. The underlying implementation uses **mincnlm** or **minc_anlm** for
the actual filtering computation.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--threads <n>`
:   Number of threads to use for parallel processing. Default: 1.

`--beta <f>`
:   Smoothing parameter that scales the estimated noise level. Higher values
    produce stronger denoising. Default: 1.

## EXAMPLES

Denoise a volume with default settings:

    volume_denoise.pl input.mnc output.mnc

Denoise with 4 threads and stronger smoothing:

    volume_denoise.pl input.mnc output.mnc --threads 4 --beta 1.5

Denoise with verbose output, overwriting existing files:

    volume_denoise.pl input.mnc output.mnc --verbose --clobber

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**mincnlm**(1), **minc_anlm**(1), **noise_estimate**(1)
