---
section: 1
title: xdisp
author: Unknown (based on original X11 image display utility)
---
# xdisp

an image display utility for the X Window System.

`xdisp [filename|--] [-geometry WxH+x+y|-geom WxH+x+y] [-fn font| -font font] [-foreground color|-fg color] [-background color|-bg color] [-grc graphics_color] [-PseudoColor|-DirectColor|-TrueColor] [-name window_name] [-noiconify] [-private] [-cmi] [-gery|-hot|-spectral] [-swap] [-color_bar] [-bilinear|-nn|-nearest_neighbour] [-all] [-image image_number] [-gamma] [-byte|-ubyte|-short|-ushort|-int|-uint|-long|-ulong|-float|-double] [-nc num_colors] [-wl] [-roi roi_filename] [-rescale] [-verbose|-v] [-height height|-h height] [-width width|-w width] [-offset byte_offset|-o byte_offset] [-skip byte_skip] [-upper upper|-u upper] [-lower lower|-l lower] [-zoom zoom_factor|-z zoom_factor] [-help]`

## DESCRIPTION

xdisp is an X11 program that displays intensity images. The program was developed within a medical imaging context and therefore accepts raw (i.e. without a header) data files as well as a few specific file formats. The primary features of xdisp are contrast/brightness adjustment, resizing, cropping, rotation, flipping, and graphics file production (GIF, TIFF, PICT, Sun raster, SGI, Matlab, short integer, byte, Postscript(PS), and EPS). In addition, xdisp only uses Xlib calls.

xdisp has four important features designed to make your life easier. First, it automatically detects GE Signa 4.X and Signa 5.X files. Second, it automatically detects ACR-NEMA (Philips and Siemens tested) and MNI MINC files. Third, it assumes that headerless files are in the native byte order of the machine on which it is running. Fourth, it provides a simple command line interface for controlling the display.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

- `filename|--`: The file to display. If `--` is used, xdisp reads from standard input.
- `-geometry WxH+x+y|-geom WxH+x+y`: Set the window geometry (width, height, x offset, y offset).
- `-fn font| -font font`: Set the font.
- `-foreground color|-fg color`: Set the foreground color.
- `-background color|-bg color`: Set the background color.
- `-grc graphics_color`: Set the graphics color.
- `-PseudoColor|-DirectColor|-TrueColor`: Set the color model.
- `-name window_name`: Set the window name.
- `-noiconify`: Prevent the window from being iconified.
- `-private`: Use a private colormap.
- `-cmi`: Enable color map input.
- `-gery|-hot|-spectral`: Set the color map to grayscale, hot metal, or spectral.
- `-swap`: Swap the byte order of the data.
- `-color_bar`: Display a color bar.
- `-bilinear|-nn|-nearest_neighbour`: Set the interpolation mode.
- `-all`: Display all images in a multi-image file.
- `-image image_number`: Select a specific image number from a multi-image file.
- `-gamma`: Apply gamma correction.
- `-byte|-ubyte|-short|-ushort|-int|-uint|-long|-ulong|-float|-double`: Specify the data type of the input file.
- `-nc num_colors`: Set the number of colors in the colormap.
- `-wl`: Enable window leveling.
- `-roi roi_filename`: Specify a region of interest file.
- `-rescale`: Rescale the image data.
- `-verbose|-v`: Enable verbose output.
- `-height height|-h height`: Set the window height.
- `-width width|-w width`: Set the window width.
- `-offset byte_offset|-o byte_offset`: Set the byte offset in the file.
- `-skip byte_skip`: Set the byte skip between images.
- `-upper upper|-u upper`: Set the upper value for display.
- `-lower lower|-l lower`: Set the lower value for display.
- `-zoom zoom_factor|-z zoom_factor`: Set the zoom factor.
- `-help`: Display help information.

## SEE ALSO

Other MINC visualization tools such as `postf`, `mincview`, etc.

