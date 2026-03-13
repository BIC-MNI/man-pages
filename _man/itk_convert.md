---
section: 1
title: itk_convert
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_convert

convert between medical image formats using ITK (MINC, NIfTI, NRRD, etc.)

`itk_convert <input> <output> [options]`

## DESCRIPTION

**itk_convert** converts medical image volumes between file formats supported by
the Insight Toolkit (ITK). Supported formats include MINC (.mnc), NIfTI (.nii,
.nii.gz), NRRD (.nrrd, .nhdr), Analyze (.hdr/.img), MetaImage (.mha, .mhd),
and other ITK-recognized formats. The conversion format is determined
automatically from the file extensions of the input and output arguments.

The tool can change voxel data types during conversion, normalize intensity
values, invert axis directions, apply compression, and handle special modalities
such as diffusion-weighted imaging (DWI) and diffusion tensor imaging (DTI).

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--quiet`
:   Suppress all informational output.

`--char`
:   Store output voxels as signed 8-bit characters.

`--byte`
:   Store output voxels as unsigned 8-bit bytes.

`--short`
:   Store output voxels as signed 16-bit short integers.

`--ushort`
:   Store output voxels as unsigned 16-bit short integers.

`--int`
:   Store output voxels as signed 32-bit integers.

`--uint`
:   Store output voxels as unsigned 32-bit integers.

`--float`
:   Store output voxels as 32-bit floating point.

`--double`
:   Store output voxels as 64-bit double-precision floating point.

`--inv-x`
:   Invert the X axis direction cosine.

`--inv-y`
:   Invert the Y axis direction cosine.

`--inv-z`
:   Invert the Z axis direction cosine.

`--center`
:   Set the volume origin to the center of the volume.

`--normalize`
:   Normalize voxel intensity values to the range [0, 1].

`--comp`
:   Write compressed output (e.g., gzip for NIfTI).

`--clamp`
:   Clamp voxel values to the valid range of the output data type.

`--dwi`
:   Treat the input as a diffusion-weighted image volume.

`--dti`
:   Treat the input as a diffusion tensor image volume.

`--use-b-matrix`
:   Use the B-matrix instead of gradient directions for DWI/DTI conversion.

`--nii-scale`
:   Apply NIfTI intensity scaling (scl_slope and scl_inter) during conversion.

`--spacing` *x,y,z*
:   Override the output voxel spacing with the given values (comma-separated, in mm).

`--labels`
:   Treat the volume as a label (discrete integer) image, using nearest-neighbour semantics where applicable.

`--relx`
:   Relax file format checks to allow non-standard header content.

## EXAMPLES

Convert a MINC volume to compressed NIfTI format:

    itk_convert input.mnc output.nii.gz --comp

Convert a NIfTI file to MINC with unsigned short data type:

    itk_convert input.nii output.mnc --ushort --clobber

Convert with axis inversion and normalization:

    itk_convert input.mnc output.nii --inv-z --normalize

Convert a diffusion tensor image from NRRD to MINC:

    itk_convert input.nrrd output.mnc --dti --float

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[itk_resample](itk_resample), [mincconvert](mincconvert), [itk_convert_xfm](itk_convert_xfm), [mincreshape](mincreshape)
