---
section: 1
title: minc_aqc.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_aqc.pl

automated quality control assessment of MINC volumes

`minc_aqc.pl <input.mnc> <output_prefix> [options]`

## DESCRIPTION

**minc_aqc.pl** generates automated quality control (QC) images from a MINC
volume. It produces individual JPEG slice images at specified positions through
the volume, which can be used for visual inspection of image quality, alignment,
or processing results.

The tool extracts representative slices from the input volume and saves each
as a separate JPEG image named with the output prefix followed by a slice index.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Print the commands that would be executed without running them.

`--clobber`
:   Overwrite existing output files.

`--slices <n>`
:   Number of slices to extract per orientation. Default: 1.

## EXAMPLES

Generate QC images with default settings:

    minc_aqc.pl subject_t1.mnc qc_output

Generate multiple slices per orientation with verbose output:

    minc_aqc.pl --slices 3 --verbose --clobber subject_t1.mnc qc_subject

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_qc.pl**(1), **mincpik**(1), **minc_pretty_pic.pl**(1)
