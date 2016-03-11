# MINCINFO

mincinfo print out specified information about a minc file

`mincinfo <options> <file> <file>`

## DESCRIPTION

`mincinfo` will print out either a general description of a minc file (type, sign and range of data, plus a brief description of dimensions and their order), or specific information about dimensions, variables or attributes in the file. This program can be very useful for building shell scripts that access minc files.

All information given by `mincinfo` is presented as read from the file with no transformation. This means that start and step values, for example, are not in the world coordinate system. To display the start values for a file in world coordinates, use *voxeltoworld*.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line. Dimensions, variables and attributes are all specified by name. Attributes are specified by *variable:attribute* where *variable* can be omitted to specify global attributes. More than one option can be specified, in which case the return value from each option is printed on a separate line (`-image_info` prints on many lines) in the order of the options on the command line.

`-image_info`  
Print out the default general information about the file. This information includes the type, sign and range of the pixel data, the order of the dimensions, and a list of dimensions giving name, length, start and step for each one.

`-dimnames`  
Print out a space-separated list of the dimensions in the file.

`-varnames`  
Print out a space-separated list of the variables in the file.

`-dimlength` dimension  
Print the length of the specified dimension.

`-vartype` variable  
Print the type of the variable.

`-vardims` variable  
Print a space-separated list of the dimensions that subscript the variable (in C order).

`-varatts` variable  
Print a space-separated list of the attribute names for the specified variable.

`-varvalues` variable  
Print a newline-separated list of the values of the specified variable.

`-atttype` variable:attribute  
Print out the type of the specified attribute.

`-attvalue` variable:attribute  
Print out a space-separated list of the values of the specified attribute.

`-error_string` string  
Specifies a string to print out if an error occurs. This will cause the program to exit with normal status. The default is to print an appropriate error message and exit with an error status.

`-help`  
Print summary of command-line options and abort.

`-version`  
Print the program's version number and exit.

## EXAMPLES

Print out standard information about a minc file.

mincinfo file.mnc

Print out contents of global history attribute.

mincinfo file.mnc -attvalue :history

Print out step value for x dimension, setting the default value to 1.

mincinfo file.mnc -attvalue xspace:step -error 1

Print out the step values for x, y and z, setting the default value to 1.

mincinfo file.mnc -error 1 BSOL -attvalue xspace:step BSOL -attvalue yspace:step BSOL -attvalue zspace:step

Print out the names of the dimensions subscripting the image variable.

mincinfo file.mnc -vardims image

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin

## SEE ALSO

[voxeltoworld](voxeltoworld) [minc_modify_header](minc_modify_header) [mincheader](mincheader)
