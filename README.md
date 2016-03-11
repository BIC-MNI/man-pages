# minc-toolkit documentation project

This is collection of documentation files for various minc tools. It was auto-converted from the 
legacy .man files to github-style markup format and then manually corrected. 

## Currently documented minc tools:

* minc file information
  * (mincinfo)[mincinfo.md] - print out general information about a minc file
  * (mincheader)[mincheader.md] -  print out complete header information for a minc file
  * (mincstats)[mincstats.md] - calculate simple statistics across voxels of a minc file
  * (mincdiff)[mincdiff.md] - report differences between minc files
  * (voxeltoworld)[voxeltoworld.md]
* file format conversion
  * (rawtominc)[rawtominc.md]
  * (mincconvert)[mincconvert.md]
  * (dcm2mnc)[dcm2mnc.md]
  * (ecattominc)[ecattominc.md]
  * (minctoecat)[minctoecat.md]
  * (minctoraw)[minctoraw.md]
  * (mnc2nii)[mnc2nii.md]
  * (nii2mnc)[nii2mnc.md]
  * (upet2mnc)[upet2mnc.md]
  * (vff2mnc)[vff2mnc.md]
* low-level file manipulation tools
  * (minc_modify_header)[minc_modify_header.md]
  * (minccopy)[minccopy.md] 
  * (mincdump)[mincdump.md]
  * (mincedit)[mincedit.md]
  * (mincexpand)[mincexpand.md]
  * (mincextract)[mincextract.md]
  * (invert_raw_image)[invert_raw_image.md]
  * (mincgen)[mincgen.md]
* mathematical operations on voxel level
  * (minccalc)[minccalc.md]
  * (minccmp)[minccmp.md]
  * (minclookup)[minclookup.md]
  * (mincmakescalar)[mincmakescalar.md]
  * (mincmakevector)[mincmakevector.md]
  * (mincmath)[mincmath.md]
* higher level operations
  * (mincconcat)[mincconcat.md]
  * (mincaverage)[mincaverage.md]
  * (mincblob)[mincblob.md]
  * (mincblur)[mincblur.md]
  * (autocrop)[autocrop.md]
* registration and resampling
  * (mincresample)[mincresample.md]
  * (mincreshape)[mincreshape.md]
  * (minctracc)[minctracc.md]
  * (mritoself)[mritoself.md]
  * (mritotal)[mritotal.md]
  * (xfm2def)[xfm2def.md]
  * (xfmconcat)[xfmconcat.md]
  * (xfmflip)[xfmflip.md]
  * (xfminvert)[xfminvert.md]
  * (transformtags)[transformtags.md]
* minc file viewing  
  * (mincview)[mincview.md]
  * (register)[register.md]
* miscellanious
  * (mincsample)[mincsample.md]
  * (mincwindow)[mincwindow.md]

## Installation

To convert back into .man pages pandoc with troff support is needed
Command line: `pandoc -S -s -f markdown_github -t man <input>.md -o <output>.man`

