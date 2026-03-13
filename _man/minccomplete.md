---
section: 1
title: minccomplete
author: Andrew Janke
group: MINC Core Tools
---
# minccomplete

check if a MINC or xfm file has been completely written

`minccomplete [options] <file.mnc>`

## DESCRIPTION

**minccomplete** is a Perl script that checks whether a MINC file (or `.xfm`
transform file) has been completely and correctly written. It verifies that the
file can be opened and read, and that its headers and data are intact.

This is particularly useful in batch processing pipelines where jobs may fail
or be interrupted, leaving behind incomplete or corrupt output files.
minccomplete can be used to verify outputs before proceeding to subsequent
processing steps.

The script returns exit code 0 if the file is complete and valid, or exit code
1 if the file is missing, incomplete, or corrupt. When used with the
`-error_string` option, a custom string is printed to stdout for incomplete
files instead of relying solely on the exit code.

## OPTIONS

`-verbose`
:   Print additional information about the file check.

`-error_string <str>`
:   Print the specified string to stdout if the file is not complete. This is
    useful for scripting when checking multiple files.

## EXAMPLES

Check if a MINC file is complete:

    minccomplete output.mnc

Check a file and print a custom error string on failure:

    minccomplete -error_string "INCOMPLETE" output.mnc

Use in a pipeline to verify outputs:

    if minccomplete result.mnc; then
        echo "File is valid"
    else
        echo "File is corrupt or incomplete"
    fi

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[mincinfo](mincinfo) [mincheader](mincheader)
