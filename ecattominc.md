ecattominc
1
ecattominc
convert an ecat format file (version 6.x or 7.x) to a minc format file
ecattominc
<options>
<infile>
<outfile.mnc>
ecattominc
-help
DESCRIPTION
===========

`ecattominc` will convert an ecat data file (version 6.x or 7.x) to a minc file format Unless the `-small_header` option is specified, `ecattominc` will conserve the maximum informations from the ecat header and subheader fields which will be respectively stored as attributes of the ecat-main and ecat-subhdr minc variables. By default the whole 3D or 4D volume is converted, however, `ecattominc` allows for the selection of slice and frame ranges to be copied. The voxel values of the generated minc file are decay corrected, unless the *nodecay\_correct* flag is specified. Finally, blood data file can be inserted within the minc file with the `-bloodfile` option.

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

General options
===============

-   `-byte:` Write out data as bytes (default).

-   `-short:` Write out data as short integers.

-   `-clobber:` Overwrite existing file.

-   `-noclobber:` Don't overwrite existing file (default).

-   `-verbose:` List files as they are converted (default)

-   `-quiet:` Do not list files as they are converted.

Command specific options
========================

`-decay_correct:` Do decay correction on images (default).

-   `-nodecay_correct:` Don't do decay correction.

-   `-slices:`Range of slices to copy (counting from 0).

-   `-frames:` Range of frames to copy (counting from 0).

-   `-frame:` Single frame to copy (counting from 0).

-   `-small_header:` Copy only basic header information.

-   `-all_header:` Copy all header information (default).

-   `-bloodfile:` Insert blood data from this file.

Generic options for all commands
================================

-   `-help:` Print summary of command-line options and abort

KNOWN BUGS
==========

No bug listed so far :=)

SEE ALSO
========

minctoecat1, rawtominc1, minctoraw1, dicomtominc1

AUTHOR
======

Peter Neelin and Anthonin Reilhac (anthonin.reilhac@cermep.fr)

COPYRIGHTS
==========

Copyrights 2005 by Peter Neelin
