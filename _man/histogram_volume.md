---
section: 1
title: histogram_volume
author: David MacDonald
group: Volume Operations
---
# histogram_volume

compute and output a histogram of voxel intensities in a MINC volume

`histogram_volume volume_file output_filename|none [x|y|z|none] [slice_pos] [filter_ratio] [y_scale]`

## DESCRIPTION

`histogram_volume` computes the intensity histogram of a MINC volume and
writes it to the specified output file. If `none` is given as the output
filename, the histogram is printed to standard output. An optional slice
along the x, y, or z axis at a given position may be selected to compute
the histogram for that slice only. The `filter_ratio` parameter controls
the smoothing of the histogram, and `y_scale` controls the vertical
scaling of the output.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`volume_file`
:   The input MINC volume.

`output_filename`
:   The output file for the histogram, or `none` for standard output.

`x|y|z|none`
:   Optional axis for selecting a specific slice. Use `none` for the
    whole volume.

`slice_pos`
:   The position of the slice along the selected axis.

`filter_ratio`
:   Optional smoothing filter ratio for the histogram.

`y_scale`
:   Optional vertical scaling factor for the histogram output.

## EXAMPLES

Compute the histogram for an entire volume:

    histogram_volume volume.mnc histogram.txt

Compute the histogram for a specific z-slice at position 50:

    histogram_volume volume.mnc histogram.txt z 50

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[mincstats](mincstats) [intensity_statistics](intensity_statistics) [volume_hist](volume_hist)
