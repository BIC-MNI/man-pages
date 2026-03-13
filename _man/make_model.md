---
section: 1
title: make_model
author: Louis Collins
group: Registration
---
# make_model

create a model for use with mritotal

`make_model <input.mnc> <output_base>`

## DESCRIPTION

**make_model** is a shell script that creates a multi-resolution model from a
MINC volume for use with **minctracc** registration. The script generates blurred
versions and gradient derivative volumes at multiple resolutions (blur levels),
which are required by the hierarchical registration strategy used by minctracc
and mritotal.

For each resolution step, make_model produces:

- A blurred version of the input volume (Gaussian smoothing)
- Gradient magnitude and directional derivative volumes

The *output_base* argument specifies the base filename for the generated model
files. Multiple files will be created with suffixes indicating the blur level
(e.g., `_blur8.mnc`, `_blur4.mnc`, `_blur2.mnc`) and derivative type.

## OPTIONS

make_model does not accept option flags. Both arguments are positional.

`<input.mnc>`
:   Input MINC volume to use as the basis for the model.

`<output_base>`
:   Base filename for the output model files. Multiple files are created with
    resolution and derivative suffixes appended.

## EXAMPLES

Create a registration model from a template volume:

    make_model mni152_t1.mnc mni152_model

This creates files such as `mni152_model_blur2.mnc`, `mni152_model_blur4.mnc`,
`mni152_model_blur8.mnc`, and their corresponding derivative volumes.

## AUTHOR

Louis Collins - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Louis Collins

## SEE ALSO

[minctracc](minctracc) [mincblur](mincblur)
