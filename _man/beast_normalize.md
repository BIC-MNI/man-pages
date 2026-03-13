---
section: 1
title: beast_normalize
author: Simon Fristed Eskildsen
group: Brain Extraction
---
# beast_normalize

preprocess and normalize a MINC volume for BEaST brain extraction

`beast_normalize <input.mnc> <output.mnc> <output_mask.mnc> [model_dir]`

## DESCRIPTION

**beast_normalize** is a Bash script that preprocesses and normalizes a MINC
volume for use with **mincbeast** brain extraction. The script performs intensity
normalization, linear registration to MNI stereotaxic space, and brain mask
extraction to prepare input data in the format expected by the BEaST library.

The preprocessing pipeline includes:

1. Intensity non-uniformity correction using **nu_correct**
2. Linear registration to the MNI152 template using **bestlinreg**
3. Intensity normalization to match the BEaST library intensity range
4. Resampling to stereotaxic space
5. Generation of a brain mask in the native space of the input volume

The optional *model_dir* argument specifies the directory containing the MNI
model files used for registration. If not provided, the default model directory
from the minc-toolkit installation is used.

## OPTIONS

beast_normalize does not accept option flags. All arguments are positional.

`<input.mnc>`
:   Input MINC volume (typically a T1-weighted MRI).

`<output.mnc>`
:   Output normalized MINC volume in stereotaxic space.

`<output_mask.mnc>`
:   Output brain mask in stereotaxic space.

`[model_dir]`
:   Optional path to the directory containing MNI model files for registration.
    Defaults to the standard minc-toolkit model directory.

## EXAMPLES

Normalize a T1 volume using default model directory:

    beast_normalize t1_native.mnc t1_stx.mnc brain_mask.mnc

Normalize using a custom model directory:

    beast_normalize t1_native.mnc t1_stx.mnc brain_mask.mnc /opt/models/icbm152

## AUTHOR

Simon Fristed Eskildsen, Pierrick Coupe - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2011 by Simon Fristed Eskildsen and Pierrick Coupe

## SEE ALSO

[mincbeast](mincbeast)
