---
---
# minc-toolkit documentation project

This is collection of documentation files for various minc tools. It was auto-converted from the 
legacy .man files to github-style markup format and then manually corrected. 

## Currently documented minc tools:

* minc file information
  * [mincinfo](man/mincinfo) - print out general information about a minc file
  * [mincheader](man/mincheader) -  print out complete header information for a minc file
  * [mincstats](man/mincstats) - calculate simple statistics across voxels of a minc file
  * [mincdiff](man/mincdiff) - report differences between minc files
  * [voxeltoworld](man/voxeltoworld)
* file format conversion
  * [rawtominc](man/rawtominc) - converts a stream of binary image data to a minc format file
  * [mincconvert](man/mincconvert) - convert between MINC 1 to MINC 2 format
  * [dcm2mnc](man/dcm2mnc) - convert sets of DICOM files to one or more MINC format files
  * [ecattominc](man/ecattominc) - convert an ecat format file (version 6.x or 7.x) to a minc format file
  * [minctoecat](man/minctoecat) - convert a minc format file to an Ecat7 format file
  * [minctoraw](man/minctoraw) - copy data from a MINC file
  * [mnc2nii](man/mnc2nii)- convert a MINC format file to a NIfTI-1 or Analyze format file
  * [nii2mnc](man/nii2mnc) - convert a NIfTI-1 or Analyze 7.5 format file to a MINC format file
  * [upet2mnc](man/upet2mnc) - convert a Concorde microPET format file to a MINC format file
  * [vff2mnc](man/vff2mnc) - convert set of vff file(s) to one 3D MINC2.0 format file
* low-level file manipulation tools
  * [minc_modify_header](man/minc_modify_header) - modify the attributes in the header of a minc file
  * [minccopy](man/minccopy) - copy minc image values from one minc file to another
  * [mincdump](man/mincdump) - convert minc files to ASCII form (CDL)
  * [mincedit](man/mincedit) - edit a MINC file header
  * [mincexpand](man/mincexpand) - expands a compressed minc file, if necessary
  * [mincextract](man/mincextract) - dump a hyperslab of MINC file data
  * [invert_raw_image](man/invert_raw_image) - invert 2D image along either or both axes
  * [mincgen](man/mincgen) - generate a MINC file from a CDL file
* mathematical operations on voxel level
  * [minccalc](man/minccalc) - perform complex math operations on minc files
  * [minccmp](man/minccmp) - compare one or more minc file using comparator operators
  * [minclookup](man/minclookup) - perform lookup table conversions on minc files
  * [mincmakescalar](man/mincmakescalar) - convert vector minc files to scalar
  * [mincmakevector](man/mincmakevector) - convert a list of scalar minc files into one vector file
  * [mincmath](man/mincmath) - perform simple math operations on minc files
* higher level operations
  * [mincconcat](man/mincconcat) - concatenate minc files along a specific dimension
  * [mincaverage](man/mincaverage) - average minc files
  * [mincblob](man/mincblob) - average minc files
  * [mincblur](man/mincblur) - convolve an input volume with a Gaussian blurring kernel
  * [autocrop](man/autocrop) - tool for extracting and manipulating bounds of a MINC file
* registration and resampling
  * [mincresample](man/mincresample) - resamples a minc file along new spatial dimensions
  * [mincreshape](man/mincreshape) - cuts a hyperslab out of a minc file (with dimension re-ordering)
  * [minctracc](man/minctracc) - estimates the spatial transformation required to register two volumes together
  * [mritoself](man/mritoself) - intra-subject registration of two volumetric data sets
  * [mritotal](man/mritotal) - performs multi-scale fitting of a normal human brain to a standard model
  * [xfm2def](man/xfm2def) - convert a MNI transform file to a deformation volume
  * [xfmconcat](man/xfmconcat) - concatenate MNI transform files
  * [xfminvert](man/xfminvert) - invert an MNI transform file
  * [xfmflip](man/xfmflip) - flip an MNI transform file
  * [transformtags](man/transformtags) - apply MNI transform to a tag file
* minc file viewing
  * [mincview](man/mincview) - view a MINC file (primitive viewer)
  * [register](man/register) - interactive volume display and point tagging program
* miscellanious
  * [mincsample](man/mincsample) - generate samplings from minc files
  * [mincwindow](man/mincwindow) - limit voxel values to a given range

