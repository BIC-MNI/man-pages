---
---
# mnc2mnc

convert a MINC format file to a NIfTI-1 or Analyze format file.

`mnc2nii <options> <infile.mnc> <outfile.mnc>`
`mnc2nii -help`

## DESCRIPTION

The `mnc2nii` command is used to convert MINC format files to either NIfTI-1 or Analyze format. The NIfTI-1 format was developed by the members of the Neuroinformatics Technology Initiative's Data Format Working Group (DFWG). The NIfTI-1 format is based upon the Mayo Clinic's Analyze 7.5 format.

The name of the program is derived from the common filename suffixes used for NIfTI-1 and MINC files. NIfTI-1 defines two possible formats, a "header plus raw image" 2-file format, and a single-file format that includes both header information and the image data. As with Analyze 7.5, the 2-file format consists of one file with the suffix ".hdr" and another file with the extension ".img". In NIfTI-1 single-file format, the two files may be combined into a single file with a ".nii" filename suffix.

In addition to the NIfTI-1 formats, `mnc2nii` can convert MINC files to the Analyze 7.5 format.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## Output file format

`-dual`  
Save file in NIfTI-1 two-file format (.hdr and .img)

`-ASCII`  
Save file in non-standard NIfTI-1 ASCII file format

`-nii`  
Save file in NIfTI-1 single-file format (.nii)

`-analyze`  
Save file in Analyze 7.5 compatible format

## Output voxel format

`-float`  
Save voxels in 32-bit floating point format

`-double`  
Save voxels in 64-bit floating point format

`-byte`  
Save voxels in 8-bit integer format

`-short`  
Save voxels in 16-bit integer format

`-int`  
Save voxels in 32-bit integer format

`-signed`  
Save voxels in signed (2's complement) integer format

`-unsigned`  
Save voxels in unsigned integer format

## Other options

`-noscanrange`  
Don't scan data to determine valid range.

`-quiet`  
Quiet operation - do not print progress or debugging information.

## Generic options for all commands

`-help`  
Print summary of command-line options and abort

`-version`  
Print the program and library versions and abort

## KNOWN BUGS

Current handling of NIfTI-1 qform and sform coordinate transforms should probably be revised as the NIfTI group clarifies the correct usage of these fields.

## SEE ALSO

[nii2mnc](nii2mnc)

## AUTHOR

Robert Vincent (bert@bic.mni.mcgill.ca) with assistance from the NIfTI-1 library authored by Robert Cox et al.

## COPYRIGHTS

Copyrights 2005 by Robert Vincent for the Montreal Neurological Institute.
