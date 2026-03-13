---
section: 1
title: noise_estimate
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# noise_estimate

Estimate noise level in MRI volumes.

`noise_estimate [options] <input>`

## DESCRIPTION

**noise_estimate** estimates the noise level in a MINC MRI volume. The method
is based on Coupe, Manjon, Gedamu, Arnold, Robles, and Collins (2009),
"Robust Rician Noise Estimation for MR Images" (MICCAI). The tool outputs
either the estimated noise standard deviation or the signal-to-noise ratio
(SNR) to standard output.

## OPTIONS

`--verbose`
:   Print detailed information during processing.

`--noise`
:   Output the estimated noise level (standard deviation). This is the default.

`--snr`
:   Output the estimated signal-to-noise ratio instead of the noise level.

`--bins` *n*
:   Set the number of histogram bins used for noise estimation. Default: 2000.

`--mask` *mask.mnc*
:   Restrict the noise estimation to voxels within the specified binary mask.

`--gauss`
:   Assume Gaussian noise distribution instead of Rician.

## EXAMPLES

Estimate noise level in a T1 volume:

    noise_estimate t1.mnc

Estimate SNR within a brain mask:

    noise_estimate --snr --mask brainmask.mnc t1.mnc

Estimate noise with Gaussian assumption:

    noise_estimate --gauss t1.mnc

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[minc_anlm](minc_anlm), [mincnlm](mincnlm), [sharpness_estimate](sharpness_estimate)
