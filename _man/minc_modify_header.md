---
section: 1
title: minc_modify_header
author: Peter Neelin
---
# minc_modify_header

minc_modify_header modify the attributes in the header of a minc file
`minc_modify_header <options> <file>.mnc`

## DESCRIPTION

*Minc_modify_header* allows the modification, insertion or deletion of attributes in a minc file. If possible, the file is modified in place, without copying the data. This will happen when inserting (modifying) an attribute that already exists and that ends up being the same length or shorter in the new file. If an attribute is deleted or lengthened, then a complete copy of the data is made, resulting in a completely new file that replaces the original.

If the file is compressed, then it is first decompressed into a file whose name is either the same as that of the original file up to the ".mnc" extension or the same minus the compression extension (".bz", ".bz2", ".gz", ".Z", ".z" or ".zip"). The new file will not be re-compressed.

Care is taken to completely overwrite any existing attribute when inserting a new attribute so that information is guaranteed to be removed from the file.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

`-sinsert` var:attr=value  
Insert a string attribute into the header. If the attribute does not exist or the new string is longer than the existing one, then all data in the file will be copied.

`-sappend` var:attr=value  
Similar to `-sinsert`, but appends the string to the attribute's value. If the attribute already exists it must be of string type.

`-dinsert` var:attr=value(,...)  
Insert a double precision attribute into the header. If the attribute does not exist or the new attribute is longer than the existing one, then all data in the file will be copied. A comma-separated array of values can be specified.

`-dappend` var:attr=value(,...)  
Similar to `-dinsert`, but appends the list of double precision values to the attribute's value. If the attribute already exists it must be of double precision type.

`-delete` var:attr  
Delete an attribute from the header. USE OF THIS OPTION WILL FORCE A COMPLETE COPY OF ALL DATA TO BE MADE. Use `-sinsert` with an empty string to delete information without copying data (the attribute will continue to exist).

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## EXAMPLES:

To replace the patient name with an identifier string:

minc_modify_header file.mnc -sinsert 'patient:full_name=C02-F0023'

To delete the patient name completely (forcing a copy of all data):

minc_modify_header file.mnc -delete 'patient:full_name'

To hide the patient name without copying data, assuming that we know that the attribute exists (the attribute will remain in the file, but it will be empty):

minc_modify_header file.mnc -sinsert 'patient:full_name='

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1995 by Peter Neelin
