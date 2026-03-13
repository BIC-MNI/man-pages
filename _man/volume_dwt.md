---
section: 1
title: volume_dwt
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# volume_dwt

Perform forward or backward discrete wavelet transform on a MINC volume.

`volume_dwt --forward <input> <output_LLL> ... <output_HHH>`

`volume_dwt --backward <input_LLL> ... <input_HHH> <output>`

`volume_dwt [--forward|--backward] --packed <input> <output>`

## DESCRIPTION

**volume_dwt** computes the discrete wavelet transform (DWT) on a 3D MINC
volume. The forward transform decomposes the volume into eight subband
components (LLL, LLH, LHL, LHH, HLL, HLH, HHL, HHH), where L denotes
low-pass and H denotes high-pass filtering along each axis.

The inverse (backward) transform reconstructs the original volume from
the eight subband components.

A packed mode is available where all subbands are stored in a single volume.

## OPTIONS

`--forward`
:   Perform the forward discrete wavelet transform (decomposition).

`--backward`
:   Perform the backward (inverse) discrete wavelet transform (reconstruction).

`--packed`
:   Use packed mode where all subbands are stored in a single volume.

## EXAMPLES

Forward DWT producing eight subband volumes:

    volume_dwt --forward input.mnc LLL.mnc LLH.mnc LHL.mnc LHH.mnc HLL.mnc HLH.mnc HHL.mnc HHH.mnc

Inverse DWT reconstructing from subbands:

    volume_dwt --backward LLL.mnc LLH.mnc LHL.mnc LHH.mnc HLL.mnc HLH.mnc HHL.mnc HHH.mnc output.mnc

Forward DWT in packed mode:

    volume_dwt --forward --packed input.mnc packed_dwt.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[fast_blur](fast_blur)
