---
---
# MINCDUMP

mincdump - Convert minc files to ASCII form (CDL)
`mincdump -c -h -v var1, -b lang -f lang -l len -n name -p f\_digits ,d\_digits  file`

## DESCRIPTION

`mincdump` is based upon the netCDF tool *ncdump*, modified to work with both 
MINC 1 (netCDF) and MINC 2 (HDF5) format files. It is intended for use primarily 
with scripts such as *mincdiff* and *mincheader*. Since it was not created at 
the Montreal Neurological Insititute it does not follow the usual conventions 
for MINC programs.

`mincdump` generates an ASCII representation of a specified minc file on 
standard output. The ASCII representation is in a form called CDL (LDQUOnetwork 
Common Data form LanguageRDQUO) that can be viewed, edited, or serve as input to 
*ncgen*. *ncgen* is a companion program that can generate a binary minc file 
from a CDL file. Hence *ncgen* and `mincdump` can be used as inverses to 
transform the data representation between binary and ASCII representations. See 
*ncgen* for a description of CDL and netCDF representations.

`mincdump` defines a default format used for each type of netCDF data, but this 
can be changed if a \`C\_format' attribute is defined for a netCDF variable. In 
this case, `mincdump` will use the \`C\_format' attribute to format each value. 
For example, if floating-point data for the netCDF variable \`Z' is known to be 
accurate to only three significant digits, it would be appropriate to use the 
variable attribute

Z:C\_format = "%.3g"

`mincdump` may also be used as a simple browser for netCDF data files, to 
display the dimension names and sizes; variable names, types, and shapes; 
attribute names and values; and optionally, the values of data for all variables 
or selected variables in a netCDF file.

`mincdump` uses \`\_' to represent data values that are equal to the 
\`\_FillValue' attribute for a variable, intended to represent data that has not 
yet been written. If a variable has no \`\_FillValue' attribute, the default 
fill value for the variable type is used if the variable is not of byte type.

## OPTIONS

`-c`  
Show the values of *coordinate* variables (variables that are also dimensions) 
as well as the declarations of all dimensions, variables, and attribute values. 
Data values of non-coordinate variables are not included in the output. This is 
the most suitable option to use for a brief look at the structure and contents 
of a netCDF file.

`-h`  
Show only the *header* information in the output, that is the declarations of 
dimensions, variables, and attributes but no data values for any variables. The 
output is identical to using the `-c` option except that the values of 
coordinate variables are not included. (At most one of `-c` or `-h` options may 
be present.)

`-v` var1,...,varn  
The output will include data values for the specified variables, in addition to 
the declarations of all dimensions, variables, and attributes. One or more 
variables must be specified by name in the comma-delimited list following this 
option. The list must be a single argument to the command, hence cannot contain 
blanks or other white space characters. The named variables must be valid netCDF 
variables in the input-file. The default, without this option and in the absence 
of the `-c` or `-h` options, is to include data values for *all* variables in 
the output.

`-b` lang  
A brief annotation in the form of a CDL comment (text beginning with the 
characters LDQUO//RDQUO) will be included in the data section of the output for 
each \`row' of data, to help identify data values for multidimensional 
variables. If *lang* begins with \`C' or \`c', then C language conventions will 
be used (zero-based indices, last dimension varying fastest). If *lang* begins 
with \`F' or \`f', then Fortran language conventions will be used (one-based 
indices, first dimension varying fastest). In either case, the data will be 
presented in the same order; only the annotations will differ. This option is 
useful for browsing through large volumes of multidimensional data.

`-f` lang  
Full annotations in the form of trailing CDL comments (text beginning with the 
characters LDQUO//RDQUO) for every data value (except individual characters in 
character arrays) will be included in the data section. If *lang* begins with 
\`C' or \`c', then C language conventions will be used (zero-based indices, last 
dimension varying fastest). If *lang* begins with \`F' or \`f', then Fortran 
language conventions will be used (one-based indices, first dimension varying 
fastest). In either case, the data will be presented in the same order; only the 
annotations will differ. This option may be useful for piping data into other 
filters, since each data value appears on a separate line, fully identified.

`-l` len  
Changes the default maximum line length (80) used in formatting lists of 
non-character data values.

`-n` name  
CDL requires a name for a netCDF data set, for use by `ncgen -b` in generating a 
default netCDF file name. By default, `mincdump` constructs this name from the 
last component of the pathname of the input netCDF file by stripping off any 
extension it has. Use the `-n` option to specify a different name. Although the 
output file name used by `ncgen -b` can be specified, it may be wise to have 
`mincdump` change the default name to avoid inadvertantly overwriting a valuable 
netCDF file when using `mincdump`, editing the resulting CDL file, and using 
`ncgen -b` to generate a new netCDF file from the edited CDL file.

`-p` float\_digits\[,double\_digits\]  
Specifies default precision (number of significant digits) to use in displaying 
floating-point or double precision data values for attributes and variables. 
If specified, this value overrides the value of the \`C\_format' attribute for 
any variable that has such an attribute. 
Floating-point data will be displayed with *float\_digits* significant digits. 
If *double\_digits* is also specified, double-precision values will be displayed 
with that many significant digits. In the absence of any `-p` specifications, 
floating-point and double-precision data are displayed with 7 and 15 significant 
digits respectively. CDL files can be made smaller if less precision is 
required. If both floating-point and double-presision precisions are specified, 
the two values must appear separated by a comma (no blanks) as a single argument 
to the command. If you really want every last bit of precision from the netCDF 
file represented in the CDL file for all possible floating-point values, you 
will have to specify this with `-p 9,17` (according to Theorem 15 of the paper 
listed under REFERENCES).

## EXAMPLES

Look at the structure of the data in the netCDF file \`*foo.mnc*':

mincdump -c foo.mnc


Produce an annotated CDL version of the structure and data in the netCDF file 
\`*foo.mnc*', using C-style indexing for the annotations:

mincdump -b c foo.mnc > foo.cdl


Output data for only the variables \`uwind' and \`vwind' from the netCDF file 
\`*foo.mnc*', and show the floating-point data with only three significant 
digits of precision:

mincdump -v uwind,vwind -p 3 foo.mnc


Produce a fully-annotated (one data value per line) listing of the data for the 
variable \`omega', using Fortran conventions for indices, and changing the 
netCDF dataset name in the resulting CDL file to \`omega':

mincdump -v omega -f fortran -n omega foo.mnc > Z.cdl


## AUTHOR

Originally written by members of the Unidata Program at the University 
Corporation for Atmospheric Research.

Modified by Bert Vincent (bert@bic.mni.mcgill.ca) for use with both netCDF and 
HDF5 files.

## COPYRIGHTS

Copyright © University Corporation for Atmospheric Research

## REFERENCES

*What Every Computer Scientist should Know About Floating-Point Arithmetic*, D. 
Goldberg, *ACM Computing Surveys, Vol. 23, No. 1*, March 1991, pp. 5-48.

## SEE ALSO

[ncdump](ncdump), [ncgen](ncgen), netcdf

## BUGS

Character arrays that contain a null-byte are treated like C strings, so no 
characters after the null byte appear in the output.

Multidimensional character string arrays are not handled well, since the CDL 
syntax for breaking a long character string into several shorter lines is weak.

There should be a way to specify that the data should be displayed in \`record' 
order, that is with the all the values for \`record' variables together that 
have the same value of the record dimension.
