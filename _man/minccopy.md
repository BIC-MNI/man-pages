---
---
# MINCCOPY

minccopy - copy minc image values from one minc file to another
` minccopy -pixel\_values  -real\_values infile outfile`

## DESCRIPTION

`minccopy` copies image values from one minc file to another. Both the input and output files must exist, and the images in both files must have an equal number dimensions and equal dimension lengths.

By default the *real* value of each pixel is copied. Use the `-pixel_values` to copy the pixel values instead.

*NOTE*: This program is intended primarily for use with scripts such as *mincedit*. It does not follow the typical design rules of most MINC command-line tools and therefore should be used only with caution.

## OPTIONS

-   `-pixel_values` Copy voxel values in raw mode.

-   `-real_values` Copy voxel intensities (default).

-   `-help` Print summary of command-line options and exit.

-   `-version` Print version number of program and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin
