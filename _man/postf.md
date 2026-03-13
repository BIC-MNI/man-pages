---
section: 1
title: postf
author: Gabriel C. Leger and Robert D. Vincent
---
# postf

a medical image display utility.

`postf [filename] [-title <window-title] [-debug] [-noprogress] [-cindex <min> <max>] [-frames <n>] [-frame <n>] [-rframes <min> <max>] [-slices <n>] [-rslices <min> <max>] [-width <n>] [-height <n>] [-roi_radius <r>] [-dynamic] [-images <n>] [-spectral | -hotmetal | -grayscale] [-describe] [-help] [-version]`

## DESCRIPTION

The program 
postf
is a medical image display utility that allows viewing of MINC files with various options for controlling the display, including color maps, frame selection, slice selection, window size, and region of interest.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

- `-filename`: The MINC file to display. If not provided, a file selection dialog may appear.
- `-title <window-title>`: Set the window title.
- `-debug`: Enable debug mode.
- `-noprogress`: Disable progress display.
- `-cindex <min> <max>`: Set the color index range.
- `-frames <n>`: Set the number of frames.
- `-frame <n>`: Set the current frame.
- `-rframes <min> <max>`: Set the frame range.
- `-slices <n>`: Set the number of slices.
- `-rslices <min> <max>`: Set the slice range.
- `-width <n>`: Set the window width.
- `-height <n>`: Set the window height.
- `-roi_radius <r>`: Set the region of interest radius.
- `-dynamic`: Enable dynamic updating.
- `-images <n>`: Set the number of images.
- `-spectral`: Use spectral color map.
- `-hotmetal`: Use hot metal color map.
- `-grayscale`: Use grayscale color map.
- `-describe`: Describe the file and exit.
- `-help`: Display help information.
- `-version`: Display version information.

## SEE ALSO

Other MINC visualization tools such as `mincview`, `xfdisp`, etc.

