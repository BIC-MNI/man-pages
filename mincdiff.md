# MINCDIFF

mincdiff report differences between minc files

`mincdiff -header -body -l diff options file1 file2`

## DESCRIPTION

The `mincdiff` shell script compares two minc files by running *diff(1)* on the headers of the two minc files, and *cmp(1)* on the image variable. You can view only the header differences using `-header` or only the body (image variable) differences using `-body`. The option `-l` is passed on to *cmp* of the image variable. Any unrecognized options (e.g. -u) are passed verbatim to the *diff* of the headers.

## OPTIONS

`-header` Compare only the headers of the two files.; `-body` Compare only the image data of the two files.; `-l` Print the byte offset in decimal and the byte value in octal  
for each difference encountered in the image variable.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 by Peter Neelin

## SEE ALSO

diff, cmp
