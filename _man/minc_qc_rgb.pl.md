---
section: 1
title: minc_qc_rgb.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_qc_rgb.pl

generate RGB quality control images from MINC volumes

`minc_qc_rgb.pl <red.mnc> [green.mnc] [blue.mnc] <output.jpg> [options]`

## DESCRIPTION

**minc_qc_rgb.pl** generates RGB composite QC images by mapping up to three
MINC volumes to the red, green, and blue channels of a colour image. This is
useful for visualising multi-modal data (e.g. different contrasts or different
time points) in a single composite image where spatial correspondence can be
visually assessed.

If only one input volume is provided, it is mapped to all three channels
(producing a grayscale image). Two volumes map to red and green channels. Three
volumes map to red, green, and blue channels respectively.

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

`--big`
:   Generate a larger output image.

`--image-range <min> <max>`
:   Set the display range applied to all input channels.

## EXAMPLES

Generate an RGB composite from T1, T2, and PD volumes:

    minc_qc_rgb.pl t1.mnc t2.mnc pd.mnc composite.jpg

Generate a red-green overlay of two volumes:

    minc_qc_rgb.pl pre.mnc post.mnc overlay.jpg

Generate a single-channel image with a title:

    minc_qc_rgb.pl --title "Subject 001" --big \
        subject_t1.mnc qc.jpg

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_qc.pl**(1), **minc_pretty_pic.pl**(1), **minc_qc_t2t1.pl**(1)
