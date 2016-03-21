---
section: 1
title: transformtags
author: Peter Neelin
---
# transformtags

transformtags apply MNI transform to a tag file
`transformtags -vol1 -vol2 -transformation transform.xfm infile.tag outfile.tag`

## DESCRIPTION

`transformtags` applies the specified transformation to one of the two sets of tags in the tag file. The default is to apply the transformation to the tags of the second volume. Use `-vol1` to transform the first volume's tag. Only one volume at a time may be transformed.

The transformation must be specified using the `-transformation` option.

## OPTIONS

`-vol1`  
Transform tags for volume 1.

`-vol2`  
Transform tags for volume 2 (default).

`-transformation` filename.xfm  
Name of transformation file (default is internal identity transform).

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

## AUTHOR

Peter Neelin

## COPYRIGHTS

Copyright © 1993 Peter Neelin
