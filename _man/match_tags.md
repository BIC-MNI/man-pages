---
section: 1
title: match_tags
author: David MacDonald
group: Tag Point Tools
---
# match_tags

find corresponding tag points between two tag files

`match_tags [options] infile1.tag file2.tag outfile2.tag`

## DESCRIPTION

**match_tags** finds corresponding tag points between two tag files. For
each tag in *infile1.tag*, the program searches *file2.tag* for the closest
tag point within the maximum allowed distance. Matched tags from *file2.tag*
are written to *outfile2.tag* in the same order as the tags in *infile1.tag*.

This is useful for establishing point correspondences between two sets of
anatomical landmarks, such as when comparing tag points identified in
different scans or by different raters.

## OPTIONS

`-max_distance` distance
:   Maximum distance for two tag points to be considered a match.
    Default: 3.4e38 (effectively unlimited).

## EXAMPLES

    match_tags scan1.tag scan2.tag matched.tag

    match_tags -max_distance 5.0 scan1.tag scan2.tag matched.tag

## SEE ALSO

[transformtags](transformtags), [interpolate_tags](interpolate_tags),
[find_tag_outliers](find_tag_outliers)

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1996 by David MacDonald
