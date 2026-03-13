---
section: 1
title: minc_qc.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_qc.pl

generate quality control images from MINC volumes

`minc_qc.pl <input.mnc> <output.jpg> [options]`

## DESCRIPTION

**minc_qc.pl** generates quality control (QC) images from MINC volumes with
optional mask overlays using multiple colour look-up tables (LUTs). It produces
a composite image showing representative slices of the input volume, optionally
overlaid with a colour-coded mask or label volume. The tool is commonly used in
processing pipelines to produce visual summaries for manual QC review.

Multiple colour map options are available for both the primary image and the
overlay, including spectral, hot metal, cyan-red, and custom LUTs. Label
overlays can use discrete colour maps.

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

`--hotmetal-mask`
:   Use a hot metal colour map for the mask overlay.

`--gray-mask`
:   Use a grayscale colour map for the mask overlay.

`--image-range <min> <max>`
:   Set the display range for the primary input volume.

`--mask-range <min> <max>`
:   Set the display range for the mask overlay.

`--cyanred`
:   Use a cyan-red diverging colour map for the primary image.

`--cyanred-mask`
:   Use a cyan-red diverging colour map for the mask overlay.

`--lut <file>`
:   Apply the specified look-up table file to the primary image.

`--mask-lut <file>`
:   Apply the specified look-up table file to the mask overlay.

`--discrete`
:   Treat the primary LUT as a discrete (label) colour map.

`--discrete-mask`
:   Treat the mask LUT as a discrete (label) colour map.

`--big`
:   Generate a larger output image.

`--bbox`
:   Automatically crop the image to the bounding box of non-zero voxels.

`--labels`
:   Treat the primary volume as a label volume with discrete colours.

`--labels-mask`
:   Treat the mask volume as a label volume with discrete colours.

`--red`
:   Map the primary volume to the red channel.

`--green-mask`
:   Map the mask overlay to the green channel.

`--clamp`
:   Clamp intensity values to the specified display range.

## EXAMPLES

Generate a basic QC image:

    minc_qc.pl subject_t1.mnc qc.jpg

Generate a QC image with a brain mask overlay:

    minc_qc.pl --mask brain_mask.mnc --spectral-mask \
        subject_t1.mnc qc_masked.jpg

Generate a QC image with label overlay and title:

    minc_qc.pl --mask labels.mnc --discrete-mask --labels-mask \
        --title "Subject 001" --clobber \
        subject_t1.mnc qc_labels.jpg

Generate a large QC image with custom display range:

    minc_qc.pl --big --image-range 0 100 --mask-range 0 5 \
        --mask overlay.mnc --hotmetal-mask \
        subject_t1.mnc qc_big.jpg

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_qc2.pl**(1), **minc_pretty_pic.pl**(1), **mincpik**(1)
