---
section: 1
title: minc_pretty_pic.pl
author: Vladimir S. Fonov
group: EZminc QC and Visualization Scripts
---
# minc_pretty_pic.pl

generate publication-quality images from MINC volumes

`minc_pretty_pic.pl <input.mnc> <output_image> [options]`

## DESCRIPTION

**minc_pretty_pic.pl** generates publication-quality multi-pane slice images
from MINC volumes. It supports overlays, colour look-up tables (LUTs), RGB
channel compositing, titles, and flexible layout control. The tool extracts
slices in coronal, sagittal, and/or axial orientations and composites them
into a single output image.

The tool can display a primary volume with an optional overlay or mask, apply
spectral or custom LUTs, control the image and overlay intensity ranges, and
add text titles. It is suitable for generating figures for papers and
presentations.

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
:   Include coronal slice(s) in the output.

`--sagittal`
:   Include sagittal slice(s) in the output.

`--axial`
:   Include axial slice(s) in the output.

`--max`
:   Use maximum intensity projection instead of a single slice.

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

`--adjust`
:   Automatically adjust windowing based on histogram analysis.

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

`--title <text>`
:   Add the specified title text to the output image.

`--pointsize <n>`
:   Set the font size (in points) for the title text.

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

Generate a three-pane image with coronal, sagittal, and axial slices:

    minc_pretty_pic.pl --coronal --sagittal --axial \
        subject_t1.mnc output.png

Display a volume with a label overlay using a spectral LUT:

    minc_pretty_pic.pl --overlay labels.mnc --lut spectral.lut \
        --discrete --image-range 0 100 \
        subject_t1.mnc output.png

Generate a titled image with custom display range:

    minc_pretty_pic.pl --title "Subject 001" --image-range 0 150 \
        --clobber subject_t1.mnc figure.png

## AUTHOR

Vladimir S. Fonov. McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov and McGill University. Licensed under the terms of the GNU General Public License version 3 or later.

## SEE ALSO

**minc_pretty_pic_m.pl**(1), **minc_qc.pl**(1), **mincpik**(1)
