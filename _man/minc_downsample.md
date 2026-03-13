---
section: 1
title: minc_downsample
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# minc_downsample

Downsample a MINC volume by specified factors.

`minc_downsample [options] <input> <output>`

## DESCRIPTION

**minc_downsample** reduces the resolution of a MINC volume by integer
downsampling factors along each spatial dimension. Different factors can be
specified independently for each axis, allowing for anisotropic downsampling.
The tool performs appropriate averaging during downsampling.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite existing output files.

`--xfactor` *f*
:   Set the downsampling factor along the X axis. Default: 1.

`--yfactor` *f*
:   Set the downsampling factor along the Y axis. Default: 1.

`--zfactor` *f*
:   Set the downsampling factor along the Z axis. Default: 2.

`--factor` *f*
:   Set the downsampling factor along the Z axis (same as `--zfactor`).

`--3dfactor` *f*
:   Set the same downsampling factor for all three axes.

`--float`
:   Write output in single-precision floating-point format.

`--short`
:   Write output in short integer format.

`--byte`
:   Write output in byte (unsigned char) format.

## EXAMPLES

Downsample a volume by a factor of 2 in all dimensions:

    minc_downsample --3dfactor 2 input.mnc downsampled.mnc

Downsample only in Z by a factor of 2 (default behavior):

    minc_downsample input.mnc downsampled.mnc

Downsample with different factors per axis:

    minc_downsample --xfactor 2 --yfactor 2 --zfactor 4 input.mnc downsampled.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mincresample](mincresample)
