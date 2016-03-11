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
  * [mincconvert](mincconvert.md) - convert between MINC 1 to MINC 2 format.
  * [dcm2mnc](dcm2mnc.md) - convert sets of DICOM files to one or more MINC format files.
  * [ecattominc](ecattominc.md) - convert an ecat format file (version 6.x or 7.x) to a minc format file
  * [minctoecat](minctoecat.md) - convert a minc format file to an Ecat7 format file
  * [minctoraw](minctoraw.md) - copy data from a MINC file
  * [mnc2nii](mnc2nii.md)
  * [nii2mnc](nii2mnc.md)
  * [upet2mnc](upet2mnc.md)
  * [vff2mnc](vff2mnc.md)
* low-level file manipulation tools
  * [minc_modify_header](minc_modify_header.md)
  * [minccopy](minccopy.md) 
  * [mincdump](mincdump.md)
  * [mincedit](mincedit.md)
  * [mincexpand](mincexpand.md)
  * [mincextract](mincextract.md)
  * [invert_raw_image](invert_raw_image.md)
  * [mincgen](mincgen.md)
* mathematical operations on voxel level
  * [minccalc](minccalc.md)
  * [minccmp](minccmp.md)
  * [minclookup](minclookup.md)
  * [mincmakescalar](mincmakescalar.md)
  * [mincmakevector](mincmakevector.md)
  * [mincmath](mincmath.md)
* higher level operations
  * [mincconcat](mincconcat.md)
  * [mincaverage](mincaverage.md)
  * [mincblob](mincblob.md)
  * [mincblur](mincblur.md)
  * [autocrop](autocrop.md)
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
  * [mincview](mincview.md)
  * [register](register.md)
* miscellanious
  * [mincsample](mincsample.md)
  * [mincwindow](mincwindow.md)

## Installation

To convert back into .man pages pandoc with troff support is needed
Command line: `pandoc -S -s -f markdown_github -t man <input>.md -o <output>.man`

