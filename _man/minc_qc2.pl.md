---
section: 1
title: minc_qc2.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_qc2.pl

generate quality control images from MINC volumes (version 2)

`minc_qc2.pl <input.mnc> <output.jpg> [options]`

## DESCRIPTION

**minc_qc2.pl** is a variant of **minc_qc.pl** that produces QC images with a
horizontal layout and a configurable background colour. It generates composite
slice images from MINC volumes with optional mask overlays, designed for
pipeline QC review.

This variant supports averaging mode for thicker slab views, and offers a
simpler set of options compared to **minc_qc.pl**.

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
:   Overlay the specified mask volume on the primary image.

`--spectral`
:   Use a spectral colour map for the primary image.

`--spectral-mask`
:   Use a spectral colour map for the mask overlay.

`--image-range <min> <max>`
:   Set the display range for the primary input volume.

`--mask-range <min> <max>`
:   Set the display range for the mask overlay.

`--horizontal`
:   Arrange slices in a horizontal layout.

`--avg`
:   Average multiple slices to produce thicker slab views.

`--big`
:   Generate a larger output image.

`--bg <color>`
:   Set the background colour of the output image (e.g. "black", "white",
    or a hex colour code).

## EXAMPLES

Generate a QC image with horizontal layout:

    minc_qc2.pl --horizontal subject_t1.mnc qc.jpg

Generate a QC image with a mask and white background:

    minc_qc2.pl --mask brain_mask.mnc --spectral-mask --bg white \
        subject_t1.mnc qc.jpg

Generate a large averaged QC image with title:

    minc_qc2.pl --big --avg --title "Subject 001" --clobber \
        subject_t1.mnc qc_big.jpg

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_qc.pl**(1), **minc_pretty_pic.pl**(1), **mincpik**(1)
