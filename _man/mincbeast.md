---
section: 1
title: mincbeast
author: 
- Simon Fristed Eskildsen
- Vladimir S. Fonov
- Pierrick Coupe
- Jose V. Manjon
---
# MINCBEAST

BEaST brain extraction tool
`mincbeast <library dir> <input> <output>`

## DESCRIPTION

`mincbeast` will extract brain using library of presegmented images
For the detailed explanation of the algorithm see: 
Eskildsen SF, Coupe P, Fonov V, Manjon JV, Leung KK, Guizard N, Wassef SN, Ostergaard LR, Collins DL; Alzheimer's Disease Neuroimaging Initiative.
BEaST: brain extraction based on nonlocal segmentation technique. Neuroimage. 2012 Feb 1;59(3):2362-73. [DOI: j.neuroimage.2011.09.012](http://dx.doi.org/10.1016/j.neuroimage.2011.09.012)


## Common options

`-help`
Print summary of command-line options and exit.

`-clobber`
Overwrite an existing file.

`-version`
Print the program's version number and exit.

## Algorithm specific options

`-probability`
  Output the probability map instead of crisp mask.
  
`-flip`
  Flip images around the mid-sagittal plane to increase patch count.
  
`-load_moments`
  Do not calculate moments instead use precalculated library moments. (for optimization purposes)
  
`-fill`
  Fill holes in the binary output.
  
`-median`
  Apply a median filter on the probability map.
  
`-nlm_filter`
  Apply an NLM filter on the probability map (experimental).

`-abspath`
  File paths in the library are absolute (default is relative to library root).
  
`-voxel_size`
  Specify voxel size for calculations (4, 2, or 1). Assumes no multiscale. Use configuration file for multiscale.  *Default value: 4*
  
`-patch_size`
  Specify patch size for single scale approach.  *Default value: 1*
  
`-search_area`
  Specify size of search area for single scale approach. *Default value: 2*
  
`-alpha`
  Specify confidence level Alpha.  *Default value: 0.5*
  
`-beta`
  Specify smoothness factor Beta.  *Default value: 0.25*
  
`-threshold`
  Specify threshold for patch selection.  *Default value: 0.95*
  
`-selection_num`
  Specify number of selected images.  *Default value: 20*
  
`-positive`
  Specify mask of positive segmentation (inside mask) instead of the default mask.
  
`-output_selection`
  Specify file to output selected files.
  
`-count`
  Specify file to output the patch count.
  
`-configuration`
  Specify configuration file.
  
`-mask`
  Specify a segmentation mask instead of the the default mask.
  
`-same_resolution`
  Output final mask with the same resolution as input file.
  
`-no_mask`
  Do not apply a segmentation mask. Perform the segmentation over the entire image.
  
`-no_positive`
  Do not apply a positive mask.

## AUTHORS

Simon Fristed Eskildsen, Vladimir S. Fonov, Pierrick Coupe, Jose V. Manjon

## COPYRIGHTS

Copyright © 2011 Simon Fristed Eskildsen, Vladimir S. Fonov, Pierrick Coupe, Jose V. Manjon
