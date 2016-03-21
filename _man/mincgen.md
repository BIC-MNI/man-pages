---
section: 1
title: mincgen
author: Modified by Bert Vincent
---
# mincgen

mincgen - generate a MINC file from a CDL file.
`mincgen -b -n -o minc_filename input_file`

## DESCRIPTION

`mincgen` generates a MINC file. The input to `mincgen` is a description of a MINC file in a small language known as CDL (network Common Data form Language), described below. If no options are specified in invoking `mincgen`, it merely checks the syntax of the input CDL file, producing error messages for any violations of CDL syntax. Other options can be used to create the corresponding MINC file.

`mincgen` may be used with the companion program *mincdump* to perform some simple operations on MINC files. For example, to rename a dimension in a MINC file, use *mincdump* to get a CDL version of the MINC file, edit the CDL file to change the name of the dimensions, and use `mincgen` to generate the corresponding MINC file from the edited CDL file.

## OPTIONS

`-b`  
Create a (binary) MINC file. If the `-o` option is absent, a default file name will be constructed from the MINC name (specified after the *netcdf* or *hdf5* keyword in the input) by appending the \`.mnc' extension. If a file already exists with the specified name, it will be overwritten.

`-o` minc_filename  
Name for the binary MINC file created. If this option is specified, it implies the "`-b`" option. (This option is necessary because MINC files cannot be written directly to standard output, since standard output is not seekable.)

## EXAMPLES

Check the syntax of the CDL file \`*foo.cdl*':

mincgen foo.cdl

</blockquote>RE
From the CDL file \`*foo.cdl*', generate an equivalent binary MINC file named \`*x.mnc*':

mincgen -o x.mnc foo.cdl

</blockquote>RE

## USAGE

### CDL Syntax Summary

Below is an example of CDL syntax, describing a MINC file with several named dimensions (xspace, yspace, and zspace), variables (zspace, image), variable attributes (valid_range, signtype), and some data. CDL keywords are in boldface. (This example is intended to illustrate the syntax; a real CDL file would have a more complete set of attributes so that the data would be more completely self-describing.)

    netcdf foo {  // an example MINC specification in CDL

    dimensions:
        xspace = 8;
            yspace = 8;
            zspace = 5;

    variables:
        float  xspace;
            float  yspace;
        float  zspace(zspace);
        short  image(zspace,yspace,xspace);
            double image-min(zspace)
            double image-max(zspace)

        // variable attributes
            image:valid_range = 0,5;
    data:
            image-min = -1,-1,-1,-1,-1;
            image-max = 1,1,1,1,1;
            image = 
            0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
            0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
            1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,
            1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,
            2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,
            2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,
            3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,
            3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,
            5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,
            5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5;
            zspace = 0,2,3.5,7,10;
    }

All CDL statements are terminated by a semicolon. Spaces, tabs, and newlines can be used freely for readability. Comments may follow the characters \`//' on any line.

A CDL description consists of three optional parts: *dimensions*, *variables*, and *data*, beginning with the keyword *dimensions:*, *variables:*, and *data*, respectively. The variable part may contain *variable declarations* and *attribute assignments*.

A MINC *dimension* is used to define the shape of one or more of the multidimensional variables contained in the MINC file. A MINC dimension has a name, a size, and possibly several other attributes.

A *variable* represents a multidimensional array of values of the same type. A variable has a name, a data type, and a shape described by its list of dimensions. Each variable may also have associated *attributes* (see below) as well as data values. The name, data type, and shape of a variable are specified by its declaration in the *variable* section of a CDL description. A variable may have the same name as a dimension; by convention such a variable is one-dimensional and contains coordinates of the dimension it names. Dimensions need not have corresponding variables.

A netCDF *attribute* contains information about a netCDF variable or about the whole netCDF dataset. Attributes are used to specify such properties as units, special values, maximum and minimum valid values, scaling factors, offsets, and parameters. Attribute information is represented by single values or arrays of values. For example, "units" is an attribute represented by a character array such as "celsius". An attribute has an associated variable, a name, a data type, a length, and a value. In contrast to variables that are intended for data, attributes are intended for metadata (data about data).

In CDL, an attribute is designated by a variable and attribute name, separated by \`:'. It is possible to assign *global* attributes not associated with any variable to the file as a whole by using \`:' before the attribute name. The data type of an attribute in CDL is derived from the type of the value assigned to it. The length of an attribute is the number of data values assigned to it, or the number of characters in the character string assigned to it. Multiple values are assigned to non-character attributes by separating the values with commas. All values assigned to an attribute must be of the same type.

The names for CDL dimensions, variables, and attributes must begin with an alphabetic character or \`_', and subsequent characters may be alphanumeric or \`_' or \`-'.

The optional *data* section of a CDL specification is where variables may be initialized. The syntax of an initialization is simple: a variable name, an equals sign, and a comma-delimited list of constants (possibly separated by spaces, tabs and newlines) terminated with a semicolon. For multi-dimensional arrays, the last dimension varies fastest. Thus row-order rather than column order is used for matrices. If fewer values are supplied than are needed to fill a variable, it is extended with a type-dependent \`fill value', which can be overridden by supplying a value for a distinguished variable attribute named \`_FillValue'. The types of constants need not match the type declared for a variable; coercions are done to convert integers to floating point, for example. The constant \`_' can be used to designate the fill value for a variable.

### Primitive Data Types

    char characters
    byte 8-bit data
    short    16-bit signed integers
    long 32-bit signed integers
    int  (synonymous with long)
    float    IEEE single precision floating point (32 bits)
    real (synonymous with float)
    double   IEEE double precision floating point (64 bits)

Except for the added data-type *byte* and the lack of *unsigned*, CDL supports the same primitive data types as C. The names for the primitive data types are reserved words in CDL, so the names of variables, dimensions, and attributes must not be type names. In declarations, type names may be specified in either upper or lower case.

Bytes differ from characters in that they are intended to hold a full eight bits of data, and the zero byte has no special significance, as it does for character data.

Shorts can hold values between -32768 and 32767.

Longs can hold values between -2147483648 and 2147483647. *int* and *integer* are accepted as synonyms for *long* in CDL declarations. Now that there are platforms with 64-bit representations for C longs, it may be better to use the *int* synonym to avoid confusion.

Floats can hold values between about -3.4+38 and 3.4+38. Their external representation is as 32-bit IEEE normalized single-precision floating point numbers. *real* is accepted as a synonym for *float* in CDL declarations.

Doubles can hold values between about -1.7+308 and 1.7+308. Their external representation is as 64-bit IEEE standard normalized double-precision floating point numbers.

### CDL Constants

Constants assigned to attributes or variables may be of any of the basic MINC types. The syntax for constants is similar to C syntax, except that type suffixes must be appended to shorts and floats to distinguish them from longs and doubles.

A *byte* constant is represented by a single character or multiple character escape sequence enclosed in single quotes. For example,

     'a'        // ASCII `a'
     'BSOL0'      // a zero byte
     'BSOLn'      // ASCII newline character
     'BSOL33'     // ASCII escape character (33 octal)
     'BSOLx2b'    // ASCII plus (2b hex)
     'BSOL377'    // 377 octal = 255 decimal, non-ASCII

Character constants are enclosed in double quotes. A character array may be represented as a string enclosed in double quotes. The usual C string escape conventions are honored. For example

    "a"     // ASCII `a'
    "TwoBSOLnlinesBSOLn"    // a 10-character string with two embedded newlines
    "a bell:BSOL007"  // a string containing an ASCII bell

Note that the character array "a" would fit in a one-element variable, since no terminating NULL character is assumed. However, a zero byte in a character array is interpreted as the end of the significant characters by the *mincdump* program, following the C convention. Therefore, a NULL byte should not be embedded in a character string unless at the end: use the *byte* data type instead for byte arrays that contain the zero byte. MINC and CDL have no string type, but only fixed-length character arrays, which may be multi-dimensional.

*short* integer constants are intended for representing 16-bit signed quantities. The form of a *short* constant is an integer constant with an \`s' or \`S' appended. If a *short* constant begins with \`0', it is interpreted as octal, except that if it begins with \`0x', it is interpreted as a hexadecimal constant. For example:

    -2s // a short -2
    0123s   // octal
    0x7ffs  //hexadecimal

*Long* integer constants are intended for representing 32-bit signed quantities. The form of a *long* constant is an ordinary integer constant, although it is acceptable to append an optional \`l' or \`L'. If a *long* constant begins with \`0', it is interpreted as octal, except that if it begins with \`0x', it is interpreted as a hexadecimal constant. Examples of valid *long* constants include:

    -2
    1234567890L
    0123        // octal
    0x7ff       // hexadecimal

Floating point constants of type *float* are appropriate for representing floating point data with about seven significant digits of precision. The form of a *float* constant is the same as a C floating point constant with an \`f' or \`F' appended. For example the following are all acceptable *float* constants:

    -2.0f
    3.14159265358979f   // will be truncated to less precision
    1.f

Floating point constants of type *double* are appropriate for representing floating point data with about sixteen significant digits of precision. The form of a *double* constant is the same as a C floating point constant. An optional \`d' or \`D' may be appended. For example the following are all acceptable *double* constants:

    -2.0
    3.141592653589793
    1.0e-20
    1.d

## AUTHOR

Originally written by members of the Unidata Program at the University Corporation for Atmospheric Research.

Modified by Bert Vincent (bert@bic.mni.mcgill.ca) for use with both netCDF and HDF5 files.

## COPYRIGHTS

Copyright © University Corporation for Atmospheric Research

## SEE ALSO

ncdump1, ncgen1, netcdf3

## BUGS

The CDL syntax makes it easy to assign what looks like an array of variable-length strings to a variable, but the strings will simply be concatenated into a single array of characters, since MINC cannot represent an array of variable-length strings in one MINC variable.

MINC and CDL do not yet support a type corresponding to a 64-bit integer.
