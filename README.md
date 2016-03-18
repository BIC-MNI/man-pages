---
---
# minc-toolkit documentation project

This is collection of documentation files for various minc tools. It was auto-converted from the 
legacy .man files to github-style markup format and then manually corrected. 

## Currently documented minc tools:

* minc file information
  * [mincinfo](mincinfo.md) - print out general information about a minc file
  * [mincheader](mincheader.md) -  print out complete header information for a minc file
  * [mincstats](mincstats.md) - calculate simple statistics across voxels of a minc file
  * [mincdiff](mincdiff.md) - report differences between minc files
  * [voxeltoworld](voxeltoworld.md)
* file format conversion
  * [rawtominc](rawtominc.md) - converts a stream of binary image data to a minc format file
  * [mincconvert](mincconvert.md) - convert between MINC 1 to MINC 2 format
  * [dcm2mnc](dcm2mnc.md) - convert sets of DICOM files to one or more MINC format files
  * [ecattominc](ecattominc.md) - convert an ecat format file (version 6.x or 7.x) to a minc format file
  * [minctoecat](minctoecat.md) - convert a minc format file to an Ecat7 format file
  * [minctoraw](minctoraw.md) - copy data from a MINC file
  * [mnc2nii](mnc2nii.md)- convert a MINC format file to a NIfTI-1 or Analyze format file
  * [nii2mnc](nii2mnc.md) - convert a NIfTI-1 or Analyze 7.5 format file to a MINC format file
  * [upet2mnc](upet2mnc.md) - convert a Concorde microPET format file to a MINC format file
  * [vff2mnc](vff2mnc.md) - convert set of vff file(s) to one 3D MINC2.0 format file
* low-level file manipulation tools
  * [minc_modify_header](minc_modify_header.md) - modify the attributes in the header of a minc file
  * [minccopy](minccopy.md) - copy minc image values from one minc file to another
  * [mincdump](mincdump.md) - convert minc files to ASCII form (CDL)
  * [mincedit](mincedit.md) - edit a MINC file header
  * [mincexpand](mincexpand.md) - expands a compressed minc file, if necessary
  * [mincextract](mincextract.md) - dump a hyperslab of MINC file data
  * [invert_raw_image](invert_raw_image.md) - invert 2D image along either or both axes
  * [mincgen](mincgen.md) - generate a MINC file from a CDL file
* mathematical operations on voxel level
  * [minccalc](minccalc.md) - perform complex math operations on minc files
  * [minccmp](minccmp.md) - compare one or more minc file using comparator operators
  * [minclookup](minclookup.md) - perform lookup table conversions on minc files
  * [mincmakescalar](mincmakescalar.md) - convert vector minc files to scalar
  * [mincmakevector](mincmakevector.md) - convert a list of scalar minc files into one vector file
  * [mincmath](mincmath.md) - perform simple math operations on minc files
* higher level operations
  * [mincconcat](mincconcat.md) - concatenate minc files along a specific dimension
  * [mincaverage](mincaverage.md) - average minc files
  * [mincblob](mincblob.md) - average minc files
  * [mincblur](mincblur.md) - convolve an input volume with a Gaussian blurring kernel
  * [autocrop](autocrop.md) - tool for extracting and manipulating bounds of a MINC file
* registration and resampling
  * [mincresample](mincresample.md) - resamples a minc file along new spatial dimensions
  * [mincreshape](mincreshape.md) - cuts a hyperslab out of a minc file (with dimension re-ordering)
  * [minctracc](minctracc.md) - estimates the spatial transformation required to register two volumes together
  * [mritoself](mritoself.md) - intra-subject registration of two volumetric data sets
  * [mritotal](mritotal.md) - performs multi-scale fitting of a normal human brain to a standard model
  * [xfm2def](xfm2def.md) - convert a MNI transform file to a deformation volume
  * [xfmconcat](xfmconcat.md) - concatenate MNI transform files
  * [xfminvert](xfminvert.md) - invert an MNI transform file
  * [xfmflip](xfmflip.md) - flip an MNI transform file
  * [transformtags](transformtags.md) - apply MNI transform to a tag file
* minc file viewing
  * [mincview](mincview.md) - view a MINC file (primitive viewer)
  * [register](register.md) - interactive volume display and point tagging program
* miscellanious
  * [mincsample](mincsample.md) - generate samplings from minc files
  * [mincwindow](mincwindow.md) - limit voxel values to a given range

## Installation

To convert back into .man pages pandoc with troff support is needed
Command line: `pandoc -S -s -f markdown_github -t man <input>.md -o <output>.man`

