---
section: 1
title: crispify
author: Vasco Kollokian
group: Classification and Segmentation
---
# crispify

create a crisp labelled volume from multiple fuzzy classification volumes

`crispify <options> <infile> <class> ...`

## DESCRIPTION

`crispify` takes multiple fuzzy (probabilistic) classification volumes as
input, each paired with an integer class label, and produces a single crisp
(discrete) labelled volume using a winner-takes-all approach.

For each voxel, the program compares the fuzzy membership values across all
input volumes and assigns the class label corresponding to the volume with
the highest membership value at that voxel. The output is stored as byte
data.

Input arguments are specified as pairs: each fuzzy volume filename is
followed by its integer class label.

## OPTIONS

`-volume` filename
:   Specify the output filename for the crisp labelled volume. This option
    is required.

`-verbose`
:   Show progress information.

`-clobber`
:   Overwrite the output file if it already exists.

`-debug` level
:   Show debugging information. Default: 0.

`-help`
:   Print summary of command-line options and exit.

`-version`
:   Print the program's version number and exit.

## EXAMPLES

Create a crisp label volume from three fuzzy classification volumes:

    crispify -volume output_labels.mnc csf.mnc 1 gm.mnc 2 wm.mnc 3

## AUTHOR

Vasco Kollokian

## SEE ALSO

[classify](classify) [mincmath](mincmath)
