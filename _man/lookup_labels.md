---
section: 1
title: lookup_labels
author: David MacDonald
group: Label and Classification Tools
---
# lookup_labels

list or look up value-label pairs in a MINC volume

`lookup_labels input.mnc`

`lookup_labels input.mnc -value val1 val2 ...`

`lookup_labels input.mnc -label label1 label2 ...`

## DESCRIPTION

**lookup_labels** lists all value-label pairs stored in a MINC file. When
called with no additional arguments, it prints every value-label mapping
present in the volume.

When the **-value** option is given followed by one or more numeric values,
the tool looks up and prints the corresponding label names for those values.

When the **-label** option is given followed by one or more label names, the
tool looks up and prints the corresponding numeric values.

## OPTIONS

`-value` val1 val2 ...
:   Look up the label names corresponding to the specified numeric values.

`-label` label1 label2 ...
:   Look up the numeric values corresponding to the specified label names.

## EXAMPLES

List all labels in a volume:

    lookup_labels classified.mnc

Look up the label for value 3:

    lookup_labels classified.mnc -value 3

## SEE ALSO

[labels_to_rgb](labels_to_rgb), [print_all_labels](print_all_labels),
[minclookup](minclookup)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
