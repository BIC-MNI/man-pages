MINCSTATS
1
$Date: 2004-05-20 21:52:09 $
mincstats
calculate simple statistics across voxels of a minc file
mincstats
&lt;options&gt;
&lt;in1&gt;.mnc
DESCRIPTION
===========

*Mincstats* will calculate simple statistical measures across all voxels of a minc file. Note that these are global statistical measures and not voxel-by-voxel measures (see *mincaverage* for that). By default all statistics are calculated. If any statistics are requested via a command-line option, then only the requested statistics are printed.

A very useful feature of this program is the ability to restrict the set of voxels included in the statistic calculation, either by restricting the range of included values, or by using a mask file with a restricted range. Multiple ranges for the input file or mask file can be specified. For each range of included volume values, and for each range of mask values, the relevant statistics are printed out (n\*m values, where n is the number of volume ranges and m the number of mask ranges). These calculations are done in a single pass through the data, so specifying multiple ranges is much faster than running the program repeatedly. This is quite helpful when calculating many regional averages with a VOI mask volume.

Special mention should be given to histograms and related statistical measures. The default range of the histogram is from the smallest value in the file to the largest. In the not uncommon, but special, case when the number of histogram bins exactly matches the number of possible values in the file (e.g. 256 bins for full-range byte data), the histogram can end up with some odd features when using the default histogram range. This arises from the discretization of the data that are then rebinned into a slightly mismatched histgram. For the example of byte data, the values that should be used are 256 bins and a histogram range that extends half a bin below the smallest value and half a bin above the largest. Use option `-discrete_histogram` to work this out automatically, or use `-integer_histogram` to have bins of unit width if the input data are inherently integer (e.g. label data). In general, one should be careful about the rebinning of discretized data to a histogram with a bin size that is close to the level of discretization.

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line. The order in which the statistics are printed will be always the same irrespective or the order in which they are requested on the command line

General options
===============

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-verbose`  
Print out extra information (more than the default).

`-quiet`  
Print out only the requested numbers

`-max_buffer_size_in_kb` size  
Specify the maximum size of the internal buffers (in kbytes). Default is 4 MB.

Invalid value options
=====================

`-ignore_nan`  
Exclude invalid values (outside valid range) from statistic calculations. This is the default.

`-include_nan`  
Treat invalid values as zeros and include them in statistic calculations.

`-replace_nan` value  
Replace invalid values with the specified value and include the new value in statistic calculations.

Volume range options
====================

`-floor` min1,*min2*,...  
Comma-separated list of lower bounds for ranges of data to include in statistic calculation.

`-ceil` max1,*max2*,...  
Comma-separated list of upper bounds for ranges of data to include in statistic calculation.

`-range` min1,*max1*,*min2*,*max2*,...  
Comma-separated list of lower and upper bounds for ranges of data to include in statistic calculation.

`-binvalue` val1,*val2*,...  
Comma-separated list of integer values to include in statistic calculation. A range of +/- 0.5 is defined around each specified value.

`-mask` filename.mnc  
Name of file to be used for masking data included in statistic calculation. For this to have any effect, you must specify a mask range with one of the following options.

`-mask_floor` min1,*min2*,...:  
Like `-floor`, but applied to the mask file.

`-mask_ceil` max1,*max2*,...  
Like `-ceil`, but applied to the mask file.

`-mask_range` min1,*max1*,*min2*,*max2*,...  
Like `-range`, but applied to the mask file.

`-mask_binvalue` val1,*val2*,...  
Like `-binvalue`, but applied to the mask file.

Histogram options
=================

`-histogram` filename  
Specify the name of a file into which the histogram is written. If multiple ranges or mask ranges are specified, then all histograms are written in this file, separated by blank lines. Information describing each histogram is written before it in lines starting with the hash (pound) character. These files can be loaded into gnuplot.

`-hist_bins` number-of-bins  
Specify the number of bins in the histogram.

`-bins` number-of-bins  
Synonym for `-hist_bins`.

`-hist_floor` min  
Specify lower bound for histogram.

`-hist_ceil` max  
Specify upper bound for histogram.

`-hist_range` min *max*  
Specify a range for the histogram

`-integer_histogram`  
Create bins of unit width, centred around integer values. This is useful for integer data such as labels. The histogram range is rounded to the nearest integer, then the min is lowered and the max is raised by 0.5. The number of bins is taken as the difference of these two values. Note that 0.01 is added to the minimum and subtracted from the maximum prior to the rounding in order to ensure that a correctly specified range (e.g. \[0.5,255.5\]) is preserved. If you want to have integer bins that are wider than one, you will have to work out the histogram range and number of bins yourself and not use this option.

`-discrete_histogram`  
Attempt to match the histogram to the discretization of the input data. This is appropriate for continuous data that are stored in an integer representation and when a bin width close to the discretization is desired. This is similar to `-integer_histogram`, except that the the histogram range is first converted to voxel values which are rounded and extended by half a bin on either side. This new voxel range is then converted back to real values. The number of bins is taken as the difference in the voxel value range. Note that this does not account for variations in slice-to-slice scaling, so odd histogram effects may still occur. This option is intended to give behaviour similar to that of *volume\_stats*.

`-int_max_bins` number-of-bins  
Specify the largest histogram that can be automatically sized with the above options. The limit prevents accidental creation of huge histograms. This option replaced the old `-max_bins` option in MINC 1.1.

Basic statistics
================

`-all`  
Compute all statistical measures. This is the default.

`-none`  
Synonym for `-count` (for similarity to volume\_stats). Note that although this was necessary for *volume\_stats*, it is not needed here, since specifying any of these options automatically turns off `-all`

`-count`  
Count the number of voxels that are within the range and mask.

`-percent`  
Print the percentage of voxels within the range and mask

`-volume`  
Print the volume of the voxels within the range and mask (in mm-cubed).

`-min`  
Print the minimum value.

`-max`  
Print the maximum value.

`-sum`  
Print the sum of all values.

`-sum2`  
Print the sum of the squares of all values.

`-mean`  
Print the mean.

`-variance`  
Print the variance.

`-stddev`  
Print the standard deviation.

`-skewness`  
Print the sample skewness (3rd moment) .

`-kurtosis`  
Print the sample kurtosis (4th moment) .

`-CoM`  
Print the centre of mass. Both the voxel coordinate and the world coordinates are printed. The voxel coordinates are printed in file order, whilst the world coordinates are printed in x,y,z order.

`-com`  
Synonym for `-CoM`.

`-world_only`  
Print the centre of mass in world coordinates only.

Histogram statistics
====================

Note that histogram statistics are derived solely from the histogram counts and bin centres, so results such as the median will not be exactly the same as the true value for all included voxels. For example, the error on the median can be as large as a half bin width. Furthermore, if the histogram range is less than that of included voxels, then the result applies only to voxels included in the histogram.

`-hist_count`  
Print number of voxels in histogram. This may be different from the number of included and masked voxels if the histogram range is less than the range of the included data.

`-hist_percent`  
Print percentage of voxels included in histogram.

`-median`  
Print the histogram median.

`-majority`  
Print the bin centre (intensity value) for the bin with the most counts.

`-biModalT`  
Print the bi-modal threshold separating the volume into two classes The default is to use the otsu method (see options below)

`-otsu`  
Use the method described in Otsu N, "A Threshold Selection Method from Grey-level Histograms", IEEE Trans on Systems, Man and Cybernetics. 1979, 9:1; 62-66 to calculate the threshold

`-kittler`  
Use the Kittler&Illingworth '86 algorithm to calculate the for bimodal threshold. Kittler, J. & Illingworth J., "Minimum error thresholding", Pattern Recognition, vol 19, pp 41-47, 1986.

`-kapur`  
Use the Kapur et al. '85 algorithm to calculate the bimodal threshold. Kapur, Sahoo & Wong "A new method for Gray-level picture thresholding using the entropy of the histogram", Computer Vision, Graphics, and Image Processing, vol 29, pp 273-285, 1985.

`-simple`  
Use simple mean-of-means algorithm to calculate the bimodal threshold This is more computationally expensive than some of the alternatives, and doesn't seem to do a great job. But it does seem more robust than some of the other methods.

`-pctT`  
Print the threshold needed for a particular critical percentage of the histogram.

`-entropy`  
Print the Shannon entropy.

H(x) = - Sum(P(i) \* log2(P(i))

where P(i) is the bin probability

Generic options for all commands:
=================================

`-help`  
Print summary of command-line options and exit.

`-version`  
Print the program's version number and exit.

AUTHOR
======

Andrew Janke

COPYRIGHTS
==========

Program: Copyright © 2000 by Andrew Janke

Man page: Copyright © 2001 by Peter Neelin
