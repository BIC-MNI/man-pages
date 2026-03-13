---
section: 1
title: glim_image
author: Mark Griffin
group: Statistical Analysis
---
# glim_image

fit a generalized linear model to voxel intensities across MINC volumes

`glim_image [options] <des.file>`

## DESCRIPTION

**glim_image** fits a generalized linear model (GLM) to voxel intensities
across a group of MINC volumes. It supports various exponential family
distributions and link functions. The design file specifies the input volumes,
design matrix, and contrasts. Use '-' as the design file to read the design
from standard input. The tool can compute t-statistics, F-statistics, and
estimate the smoothness (FWHM) of the residual fields for use in random field
theory corrections for multiple comparisons.

## EXAMPLES

    glim_image design.file

    glim_image -output_path /tmp/results design.file

    cat design.file | glim_image -

## AUTHOR

Mark Griffin - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2001 by Mark Griffin

## SEE ALSO

[mincmath](mincmath), [volume_stats](volume_stats), [mincstats](mincstats)
