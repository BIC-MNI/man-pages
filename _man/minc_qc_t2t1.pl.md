---
section: 1
title: minc_qc_t2t1.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_qc_t2t1.pl

generate T2/T1 overlay quality control images

`minc_qc_t2t1.pl <t1.mnc> <t2.mnc> <output.jpg> [options]`

## DESCRIPTION

**minc_qc_t2t1.pl** generates a QC image by overlaying a T2-weighted volume on
a T1-weighted volume using a red-green colour scheme. The T1 volume is displayed
in one channel and the T2 volume in another, allowing visual assessment of
spatial alignment between the two modalities. Areas of good alignment appear as
a blend, while misaligned regions show colour separation.

This tool is commonly used in multi-modal processing pipelines to verify that
T2-to-T1 registration has been performed correctly.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--fake`
:   Print the commands that would be executed without running them.

`--clobber`
:   Overwrite existing output files.

`--title <text>`
:   Add the specified title text to the output image.

`--mask <mnc>`
:   Apply the specified mask to restrict the displayed region.

## EXAMPLES

Generate a T2/T1 overlay QC image:

    minc_qc_t2t1.pl subject_t1.mnc subject_t2.mnc qc_t2t1.jpg

Generate with a title and brain mask:

    minc_qc_t2t1.pl --title "Subject 001 T2/T1" --mask brain_mask.mnc \
        --clobber subject_t1.mnc subject_t2.mnc qc_t2t1.jpg

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_qc.pl**(1), **minc_qc_rgb.pl**(1), **pipeline_qc_t2t1.pl**(1)
