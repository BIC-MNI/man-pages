---
section: 1
title: itk_label_stats
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_label_stats

Calculate per-label statistics from a label image.

`itk_label_stats <input.mnc> [output] [options]`

## DESCRIPTION

**itk_label_stats** computes statistics for each label in a MINC label volume.
For each unique label value, the tool reports the voxel count and volume.
When an additional intensity image is provided with `--image`, it also
computes the mean, standard deviation, minimum, and maximum intensity within
each labelled region.

Results are printed to standard output. When `--csv` is specified, the output
is formatted as comma-separated values for easy import into spreadsheets or
downstream analysis scripts.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--image` *file*
:   Provide an intensity image from which to compute per-label intensity
    statistics (mean, standard deviation, min, max).

`--csv`
:   Output statistics in CSV format.

## EXAMPLES

    # Print volume statistics for each label
    itk_label_stats labels.mnc

    # Compute intensity statistics within each label region
    itk_label_stats labels.mnc --image t1.mnc

    # Output as CSV for further processing
    itk_label_stats labels.mnc --image t1.mnc --csv > stats.csv

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute.

## COPYRIGHTS

Copyright &copy; 2009-2024 by Vladimir S. Fonov

## SEE ALSO

[mincstats](mincstats) ,
[print_all_labels](print_all_labels)
