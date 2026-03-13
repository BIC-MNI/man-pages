---
section: 1
title: minc_taylor_reg
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# minc_taylor_reg

Apply Taylor series-based registration using vector coefficient volumes.

`minc_taylor_reg <vec0.mnc> <vecx.mnc> <vecy.mnc> <vecz.mnc> <output.mnc>`

## DESCRIPTION

**minc_taylor_reg** applies a registration transformation defined by Taylor
series expansion coefficients stored in separate MINC volumes. The tool takes
four input coefficient volumes (the constant term and the x, y, and z linear
terms) and computes the resulting transformed output volume.

This tool is typically used in conjunction with other registration and
deformation tools in the minc-toolkit pipeline.

## EXAMPLES

Apply Taylor series registration:

    minc_taylor_reg vec0.mnc vecx.mnc vecy.mnc vecz.mnc output.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[minctracc](minctracc), [mincresample](mincresample)
