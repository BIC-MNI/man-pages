---
section: 1
title: xfmflip
author: Andrew Janke
---
# xfmflip

xfmflip  flip an MNI transform file
xfmflip in.xfm out.xfm 

## DESCRIPTION

`xfmflip` flips an input transform *input.xfm* about an axis (x, y or z) and 
puts the result in the file `result.xfm`. The default flip is about the X axis 
(Left-Right) but can be changed to the Y axis (via the -y option) or Z axis (-z)

## OPTIONS

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

`-verbose`  
Print out extra progress information while running.

`-clobber`  
Overwrite any existing output file

`-fake`  
Dont actually run the commands, just echo them to STDOUT

## AUTHOR

Andrew Janke Vladimir Fonov

## COPYRIGHTS

Copyright © 2007 Andrew Janke - a.janke@gmail.com
