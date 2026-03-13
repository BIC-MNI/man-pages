---
section: 1
title: minchistory
author: Andrew Janke
group: MINC Core Tools
---
# minchistory

display the history of processing steps applied to a MINC file

`minchistory <file.mnc>`

## DESCRIPTION

**minchistory** is a Perl script that displays the processing history stored in
a MINC file's `:history` global attribute. Each time a MINC tool processes a
file, it appends a timestamped record of the command that was executed to the
`:history` attribute. This provides a complete audit trail of all transformations
and processing steps applied to the data.

The history is printed to standard output, with each processing step on a
separate line showing the date, time, and full command line used.

This tool is useful for understanding the provenance of a MINC file, debugging
processing pipelines, and documenting the exact sequence of operations applied
to a dataset.

## OPTIONS

minchistory does not accept option flags. The single argument is the MINC file
to query.

`<file.mnc>`
:   The MINC file whose processing history will be displayed.

## EXAMPLES

Display the processing history of a MINC file:

    minchistory processed_brain.mnc

Save the history to a text file:

    minchistory processed_brain.mnc > processing_log.txt

## AUTHOR

Andrew Janke - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2000 by Andrew Janke

## SEE ALSO

[mincinfo](mincinfo) [mincheader](mincheader)
