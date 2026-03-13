---
section: 1
title: minc_pretty_pic_m.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_pretty_pic_m.pl

generate publication-quality montage images from MINC volumes

`minc_pretty_pic_m.pl <input.mnc> <output_image> [options]`

## DESCRIPTION

**minc_pretty_pic_m.pl** is a variant of **minc_pretty_pic.pl** that generates
multi-pane slice montage images with multiple slices per orientation. It
produces a grid of slices spanning the volume, which is useful for reviewing
the full extent of a brain volume or overlay in a single composite image.

The tool supports the same overlay, mask, LUT, RGB channel, and layout options
as **minc_pretty_pic.pl**, but without title/font/adjust options. It is designed
for generating comprehensive montage views.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--image-range <min> <max>`
:   Set the display range for the primary input volume.

`--ovl-range <min> <max>`
:   Set the display range for the overlay volume.

`--overlay <mnc>`
:   Overlay the specified volume on top of the primary volume.

`--mask <mnc>`
:   Apply the specified mask to restrict the displayed region.

`--scale <f>`
:   Scale factor for the output image size.

`--separate`
:   Output each slice as a separate image file.

`--coronal`
:   Include coronal slices in the output.

`--sagittal`
:   Include sagittal slices in the output.

`--axial`
:   Include axial slices in the output.

`--max`
:   Use maximum intensity projection instead of single slices.

`--over`
:   Display overlay on top of the primary image.

`--red`
:   Map the primary volume to the red channel.

`--green`
:   Map the primary volume to the green channel.

`--blue`
:   Map the primary volume to the blue channel.

`--vertical`
:   Arrange panes vertically instead of horizontally.

`--trim-x <n>`
:   Trim the specified number of voxels from the x-axis borders.

`--trim-y <n>`
:   Trim the specified number of voxels from the y-axis borders.

`--trim-z <n>`
:   Trim the specified number of voxels from the z-axis borders.

`--shift-x <n>`
:   Shift the slice position along the x-axis.

`--shift-y <n>`
:   Shift the slice position along the y-axis.

`--shift-z <n>`
:   Shift the slice position along the z-axis.

`--cyanred`
:   Use a cyan-red diverging colour map for the overlay.

`--lut <file>`
:   Apply the specified look-up table file to the primary volume.

`--discrete`
:   Treat the LUT as a discrete (label) colour map.

`--background <color>`
:   Set the background colour of the output image.

`--foreground <color>`
:   Set the foreground (text) colour of the output image.

`--noresample`
:   Do not resample the input volume before slice extraction.

`--tile <cols>x<rows>`
:   Arrange slices in a tile grid with the specified columns and rows.

`--geo <WxH>`
:   Set the output image geometry (width x height in pixels).

`--compact`
:   Remove spacing between panes for a compact layout.

`--debug`
:   Print additional debugging information.

## EXAMPLES

Generate an axial montage through the whole brain:

    minc_pretty_pic_m.pl --axial subject_t1.mnc montage.png

Generate a montage with an overlay and custom display range:

    minc_pretty_pic_m.pl --overlay labels.mnc --lut spectral.lut \
        --discrete --image-range 0 100 \
        subject_t1.mnc montage.png

Generate a compact coronal montage:

    minc_pretty_pic_m.pl --coronal --compact --clobber \
        subject_t1.mnc coronal_montage.png

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_pretty_pic.pl**(1), **minc_qc.pl**(1), **mincpik**(1)
