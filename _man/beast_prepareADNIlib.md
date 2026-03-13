---
section: 1
title: beast_prepareADNIlib
author: Simon Fristed Eskildsen
group: Brain Extraction
---
# beast_prepareADNIlib

prepare an ADNI library for use with BEaST brain extraction

`beast_prepareADNIlib <library_dir>`

## DESCRIPTION

**beast_prepareADNIlib** is a Bash script that prepares ADNI (Alzheimer's Disease
Neuroimaging Initiative) brain image data into a library format compatible with
**mincbeast** brain extraction. The script downloads and processes ADNI brain
images, normalizes them, and organizes the resulting volumes and brain masks into
the directory structure expected by the BEaST segmentation library.

The prepared library contains normalized template volumes and their corresponding
manually segmented brain masks at multiple resolutions. These are used as the
training library for the patch-based label fusion approach in mincbeast.

The *library_dir* argument specifies the target directory where the prepared
library will be created. The directory will be populated with the necessary
volume files, mask files, and configuration files.

## OPTIONS

beast_prepareADNIlib does not accept option flags. The single argument is
positional.

`<library_dir>`
:   Target directory where the ADNI library will be created and populated.

## EXAMPLES

Prepare the ADNI library in a specified directory:

    beast_prepareADNIlib /opt/beast/ADNI_library

## AUTHOR

Simon Fristed Eskildsen, Pierrick Coupe - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 2011 by Simon Fristed Eskildsen and Pierrick Coupe

## SEE ALSO

[mincbeast](mincbeast) [beast_normalize](beast_normalize)
