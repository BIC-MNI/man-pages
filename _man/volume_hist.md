---
section: 1
title: volume_hist
author: John G. Sled
group: Non-Uniformity Correction
---
# volume_hist

create histograms of intensity values in a MINC volume

`volume_hist [options] <infile> <outfile>`

## DESCRIPTION

**volume_hist** computes intensity histograms of a MINC volume and writes the
result to a file. The histogram can be output in text or matlab format. A mask
volume can be used to restrict the computation to a region of interest. This
tool is used in the N3 non-uniformity correction pipeline to generate the
histogram that is subsequently sharpened by **sharpen_hist**.

## OPTIONS

`-clobber`
:   Overwrite an existing output file.

`-noclobber`
:   Do not overwrite an existing output file (default).

`-verbose`
:   Print progress information.

`-quiet`
:   Do not print progress information.

`-bins <n>`
:   Set the number of histogram bins (default: 200).

`-mask <mask.mnc>`
:   Specify a mask volume to restrict the histogram computation.

`-classes <n>`
:   Limit the number of histograms (classes) to compute.

`-select <class>`
:   Only compute the histogram for the selected class.

`-auto_range`
:   Automatically determine the intensity range from the data.

`-window`
:   Use a triangular Parzen window for histogram smoothing.

`-text`
:   Output in text format (default).

`-matlab`
:   Output in matlab format.

## EXAMPLES

    volume_hist input.mnc histogram.txt

    volume_hist -bins 500 -mask brain_mask.mnc input.mnc histogram.txt

    volume_hist -matlab input.mnc histogram.mat

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[sharpen_hist](sharpen_hist), [sharpen_volume](sharpen_volume), [volume_stats](volume_stats), [nu_correct](nu_correct)
