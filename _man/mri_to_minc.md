---
section: 1
title: mri_to_minc
author: Peter Neelin
group: Format Conversion
---
# mri_to_minc

convert various MRI scanner formats to MINC format

`mri_to_minc [options] <input_dir> <output_dir>`

## DESCRIPTION

**mri_to_minc** is a Perl script that converts raw MRI scanner output files to
MINC format. It supports input from several major scanner manufacturers including
GE, Siemens, Philips, and Bruker. The script reads the scanner-specific file
format, extracts image data and header information (patient demographics, scan
parameters, spatial orientation), and writes properly formatted MINC files.

The *input_dir* specifies the directory containing the raw scanner files. The
*output_dir* specifies where the converted MINC files will be written. The script
automatically detects the scanner format and groups related files into multi-
dimensional MINC volumes.

## OPTIONS

`-verbose`
:   Print detailed progress information during conversion.

`-clobber`
:   Overwrite existing output files.

`-noclobber`
:   Do not overwrite existing output files (default).

`-list`
:   List the files that would be created without actually performing the conversion.

`-tape`
:   Read input from a tape device instead of a directory.

`-inputdir`
:   Explicitly specify the input directory (alternative to positional argument).

`-outputdir`
:   Explicitly specify the output directory (alternative to positional argument).

## EXAMPLES

Convert scanner files from a directory:

    mri_to_minc /data/scanner_output /data/minc_files

List files that would be created without converting:

    mri_to_minc -list /data/scanner_output /data/minc_files

Convert with verbose output, overwriting existing files:

    mri_to_minc -verbose -clobber /data/ge_raw /data/converted

## AUTHOR

Peter Neelin - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993 by Peter Neelin

## SEE ALSO

[dcm2mnc](dcm2mnc) [rawtominc](rawtominc) [nii2mnc](nii2mnc)
