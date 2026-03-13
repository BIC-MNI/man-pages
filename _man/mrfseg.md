---
section: 1
title: mrfseg
author: Vladimir S. Fonov
group: MRF Segmentation
---
# mrfseg

MRF-based brain tissue segmentation.

`mrfseg <img> <brainmask> <atlas_def> <mixture_params> <labelimg> [pvelabelimg] [beta1] [beta2]`

## DESCRIPTION

**mrfseg** performs Markov Random Field (MRF) based tissue segmentation on a
brain MRI volume. The MRF model enforces spatial regularization to produce
smooth, consistent tissue labels while respecting image intensity information
from the Gaussian mixture model parameters.

The tool requires an input image, a brain mask (or the string 'default' to
assume all non-zero intensity voxels are brain), an atlas definition file,
and mixture model parameters (typically estimated by **gamixture**). The
output is a discrete label volume assigning each voxel to a tissue class.

Optionally, a partial volume effect (PVE) label image can be produced, and
the MRF regularization strength can be controlled via the beta parameters.

## OPTIONS

*img*
:   Input MRI volume to segment.

*brainmask*
:   Binary brain mask volume. Use 'default' to treat all non-zero intensity
    voxels as brain.

*atlas_def*
:   Atlas definition file specifying tissue class priors.

*mixture_params*
:   Gaussian mixture model parameter file (from **gamixture**).

*labelimg*
:   Output discrete label image.

*pvelabelimg*
:   Optional output partial volume effect label image.

*beta1*
:   Optional MRF regularization parameter for spatial smoothness.

*beta2*
:   Optional second MRF regularization parameter.

## EXAMPLES

Segment a T1 volume using estimated mixture parameters:

    mrfseg t1.mnc brainmask.mnc atlas_def.txt mixture_params.txt labels.mnc

Segment assuming all non-zero voxels are brain:

    mrfseg t1.mnc default atlas_def.txt mixture_params.txt labels.mnc

Segment with PVE labels and custom beta values:

    mrfseg t1.mnc brainmask.mnc atlas_def.txt params.txt labels.mnc pve_labels.mnc 0.3 0.1

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[gamixture](gamixture), [em_classify](em_classify), [classify](classify)
