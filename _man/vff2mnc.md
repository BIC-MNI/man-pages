# vff2mnc

convert set of vff file(s) to one 3D MINC2.0 format file.
`vff2mnc <options> <output-file> <input-list>`
`vff2mnc -help`

## DESCRIPTION

The `vff2mnc` command is used to convert vff format files to MINC2.0 format.

"VFF" stands for "Vextractor File Format". This format is used for storing vector data between sessions. The vff file contains the image information at the very top in text format and the actual image right after the form feed character '\\f' in binary.

## Output file options

`-noswap`  
Do not swap bytes when creating the MINC2.0 file.

`-list`  
Print list of series (don't create files).

## Generic options for all commands

`-help`  
Print summary of command-line options and abort

`-version`  
Print the program and library versions and abort

## AUTHORS

Leila Baghdadi (adopted from JG Sled Perl code)

Please direct all complaints and inquiries to Leila Baghdadi

## BUGS

Probably many. But must discover them first

## COPYRIGHTS

Copyrights 1993-2006 for the Montreal Neurological Institute.
