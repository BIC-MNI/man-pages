---
section: 1
title: sharpen_hist
author: John G. Sled
group: Non-Uniformity Correction
---
# sharpen_hist

create a mapping for minclookup to sharpen a volume histogram

`sharpen_hist [options] <infile> <outfile>`

## DESCRIPTION

**sharpen_hist** sharpens (deconvolves) an intensity histogram using a Wiener
filter. The input is a histogram file (produced by **volume_hist**) and the
output is a sharpened histogram. This deconvolution step is central to the N3
non-uniformity correction algorithm, where sharpening the histogram helps
estimate the bias field by separating the true tissue intensity distribution
from the blurring effect of the non-uniformity.

## OPTIONS

`-clobber`
:   Overwrite an existing output file.

`-noclobber`
:   Do not overwrite an existing output file (default).

`-verbose`
:   Print progress information.

`-quiet`
:   Do not print progress information.

`-fwhm <val>`
:   Set the full width at half maximum of the deconvolution kernel (default: 1).

`-noise <val>`
:   Set the noise level for the Wiener filter (default: 0.1).

`-blur`
:   Skip the deblurring step.

`-min <val>`
:   Set the bin value mapped to zero in the lookup table.

`-max <val>`
:   Set the bin value mapped to one in the lookup table.

`-range <min> <max>`
:   Set the range of bin values for the lookup table.

`-debug`
:   Save intermediate steps as matlab files for debugging.

## EXAMPLES

    sharpen_hist histogram.txt sharpened_histogram.txt

    sharpen_hist -fwhm 0.5 -noise 0.05 histogram.txt sharpened.txt

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[sharpen_volume](sharpen_volume), [volume_hist](volume_hist), [nu_correct](nu_correct), [nu_estimate](nu_estimate)
