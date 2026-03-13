---
section: 1
title: tag2csv
author: Vladimir S. Fonov
group: EZminc Analysis Tools
---
# tag2csv

convert a MINC .tag file into comma-separated values (CSV)

`tag2csv <input.tag> [output.csv]`

## DESCRIPTION

**tag2csv** converts MNI tag point files (`.tag`) into CSV (comma-separated
values) format. Tag files are used in the MINC ecosystem to store labeled 3D
point coordinates, commonly used for anatomical landmarks, fiducial markers, or
point-based correspondence data.

The output CSV file contains the tag point coordinates and any associated labels
or weights, one point per line, formatted for easy import into spreadsheets or
statistical analysis tools.

If the output filename is omitted, the CSV data is written to standard output.

## OPTIONS

`--verbose`
:   Print progress information during conversion.

`<input.tag>`
:   Input MNI tag point file.

`[output.csv]`
:   Optional output CSV file. If omitted, output is written to stdout.

## EXAMPLES

Convert a tag file to CSV:

    tag2csv landmarks.tag landmarks.csv

Convert a tag file and pipe to another tool:

    tag2csv landmarks.tag | sort -t, -k1 -n

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2009 by Vladimir S. Fonov

## SEE ALSO

[transformtags](transformtags) [tagtominc](tagtominc)
