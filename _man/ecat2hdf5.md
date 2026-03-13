---
section: 1
title: ecat2hdf5
author: Andrew Janke
group: Miscellaneous Tools
---
# ecat2hdf5

convert ECAT format PET data to HDF5 format

`ecat2hdf5 [options] <input.v> <output.mnc>`

## DESCRIPTION

**ecat2hdf5** is a Perl script that converts ECAT7 PET (Positron Emission
Tomography) image files to HDF5-based MINC2 format. ECAT7 is a proprietary
format used by CTI/Siemens PET scanners to store reconstructed PET image data.

The script reads the ECAT7 file headers and image data, preserving scan
parameters, timing information, and spatial geometry, and writes the data into
the MINC2 (HDF5-based) file format for use with the MINC toolkit processing
pipeline.

## OPTIONS

`-verbose`
:   Print detailed progress information during conversion.

`-clobber`
:   Overwrite the output file if it already exists.

`<input.v>`
:   Input ECAT7 format PET image file.

`<output.mnc>`
:   Output MINC2 (HDF5-based) volume file.

## EXAMPLES

Convert an ECAT7 PET file to MINC2:

    ecat2hdf5 pet_scan.v pet_scan.mnc

Convert with verbose output:

    ecat2hdf5 -verbose pet_scan.v pet_scan.mnc

## AUTHOR

Claude Bherer - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2003 by Claude Bherer

## SEE ALSO

[ecattominc](ecattominc) [minctoecat](minctoecat) [upet2mnc](upet2mnc)
