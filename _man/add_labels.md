---
section: 1
title: add_labels
author: David MacDonald
group: Label and Classification Tools
---
# add_labels

add or modify value-label pairs in a MINC volume

`add_labels [-clobber] input.mnc output.mnc -label val1 str1 [val2 str2 ...] `
`add_labels [-clobber] input.mnc output.mnc lookup_file`

## DESCRIPTION

`add_labels` creates a new MINC file by adding a set of value-label pairs to
those already present in the input MINC file. Value-label pairs can be specified
directly on the command line or read from a lookup file. If a label string is
empty, the corresponding value is deleted from the label list.

## OPTIONS

`-clobber`
:   Overwrite the output file if it already exists.

`-label` val1 str1 [val2 str2 ...]
:   Specify one or more value-label pairs on the command line, where each
    pair consists of a numeric value followed by a string label.

## EXAMPLES

Add two labels to a volume:

    add_labels input.mnc output.mnc -label 1 CSF 2 Grey_Matter

Add labels from a lookup file:

    add_labels input.mnc output.mnc labels.txt

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[lookup_labels](lookup_labels) [create_label_map](create_label_map)
