---
section: 1
title: mincblob
author: Andrew Janke
---
# mincblob

mincblob - calculate blobs from minc deformation grids
`mincblob <options> <in1>.mnc`

## DESCRIPTION

`mincblob` will calculate simple statistical metrics of a minc deformation grid file related to local volume change. The input deformation grid files are typically produced by minctracc.

There are currently 4 deformation grid metrics to choose from: trace, determinant, translation and magnitude. The first two relate to different estimates of local volume change the third is a measure of how consistent movement is in a direction but without a local change in volume. The last calcuates the magnitude of the local deformation vector. These metrics are all calculated with respect to a vectors immediate neighbours. No smoothing of the field is performed as part of this calculation so if a smooth results is desired input grid files should be first smoothed or blurred.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## General options

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-verbose`  
Print out extra information (more than the default).

`-trace` Compute the areas within the deformation field that equate to volume increase or decrease (+ve or -ve dilation) Dilation is defined as the trace of the deformation field Thus it should range between -1..1 with -1 being compression and 1 being dilation. This measure while fast is essentially a sum of partial derivatives in all three directions.

`-determinant`  
This computes the same metric as -trace but with greater accuracy as the local Jacobian matrix is first estimated. The first order determinant of the Jacobian is then returned.

`-translation`  
Compute the areas within the deformation field that equate to translation Translation is defined as: trans = arccos( A.B / |A|.|B| ) \* e^- (|A|-|B|) Thus it should range between 0..1 with 1 being "translation".

`-magnitude`  
Compute the magnitude of the local deformation vector.

## Generic options for all commands:

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Andrew Janke

## COPYRIGHTS

Program: Copyright © 2000 by Andrew Janke

Man page: Copyright © 2001 by Peter Neelin
