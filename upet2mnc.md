upet2mnc
1
May 03 2005
$Revision: 1.3 $
convert a Concorde microPET format file to a MINC format file.
upet2mnc
&lt;options&gt;
&lt;infile&gt;
&lt;outfile.mnc&gt;
upet2mnc
-help
DESCRIPTION
===========

The `upet2mnc` command is used to convert Concorde microPET format files to MINC format.

The microPET format consists of two files, a binary image and a text header. The header file generally has the same name as the image with the suffix ".hdr" appended. Normally you can specify the name of either the binary image or the text header file on the command line. However, both of the files should be in the same directory for the converter to locate both files correctly.

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

`-head`  
Orient the image according to typical neurological conventions, with the Y axis oriented from the posterior to anterior, the Z axis oriented from inferior to superior, and X oriented from patient left to patient right.

`-body`  
Orient the image such that the Y axis is oriented from superior to inferior, the Z axis is oriented from posterior to anterior, and X from patient left to patient right.

`-quiet`  
Quiet operation - do not print progress or debugging information.

Generic options for all commands
================================

`-help`  
Print summary of command-line options and abort

`-version`  
Print the program and library versions and abort

AUTHOR
======

Robert Vincent (bert@bic.mni.mcgill.ca)

COPYRIGHTS
==========

Copyrights 2005 by Robert Vincent for the Montreal Neurological Institute.
