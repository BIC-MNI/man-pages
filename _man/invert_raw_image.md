---
section: 1
title: invert_raw_image
---
# invert_raw_image

invert_raw_image - invert 2D image along either or both axes
`invert_raw_image xsize xsize bytesperpixel ` 

## DESCRIPTION

`invert_raw_image` reads an image from standard input and copies it to standard 
output, inverting along either or both dimensions according to the arguments.

The parameter *xsize* specifies the number of pixels in the x-direction. Use a 
negative number to flip the image along this axis. Ditto for *ysize.* The number 
of bytes per pixel defaults to 1 if not specified.
