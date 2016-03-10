MINCCMP
1
$Date: 2010-03-02 12:12:20 $
minccmp
compare one or more minc file using comparator operators
minccmp
&lt;options&gt;
&lt;in1.mnc&gt;
&lt;in2.mnc&gt;
&lt;inn.mnc&gt;
DESCRIPTION
===========

`minccmp` will calculate simple statistical measures between two minc files or more by comparing all subsequent files to the first. The results for each subseqent file are then returned in order. By default all statistics are calculated. If specifitc statistics are requested via a command-line option, then only the requested statistics are printed.

A very useful feature of this program is the ability to restrict the set of voxels included in the statistic calculation, either by restricting the range of included values (-floor, -ceil or -range), or by using a mask file (-mask) with a restricted range.

The comparison statistics available in minccmp are given below. Note that two of these (-xcorr and -zscore) are a very close approximation to what is used in minctracc.

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

General options
===============

`-clobber`  
Overwrite an existing file.

`-noclobber`  
Don't overwrite an existing file (default).

`-debug`  
Dump a lot of extra information (for when things go haywire).

`-verbose`  
Print out extra information (more than the default).

`-quiet`  
Print out only the requested numbers

`-max_buffer_size_in_kb` size  
Specify the maximum size of the internal buffers (in kbytes). Default is 4 MB.

`-check_dimensions`  
Check that all input files have matching sampling in world dimensions (default).

`-nocheck_dimensions`  
Ignore any differences in world dimensions sampling for input files .

Volume range options
====================

`-floor` min  
A lower bound for ranges of data to include in statistic calculations.

`-ceil` max  
An upper bound for ranges of data to include in statistic calculations.

`-range` min,*max*  
A lower and upper bound for the ranges of data to include in statistics.

`-mask` filename.mnc  
Name of file to be used for masking data included in statistic calculations.

Basic statistics
================

`-all`  
Compute all statistical measures. This is the default.

`-ssq`  
Print the Sum Squared Difference between two input files SSQ = Sum( (A-B)^2 )

`-rmse`  
Print the Root Mean Squared Error between two input files RMSE = sqrt( 1/n \* Sum((A-B)^2))

`-xcorr`  
Print the Cross Correlation between two input files XCORR = Sum((A\*B)^2) / (sqrt(Sum(A^2)) \* sqrt(Sum(B^2))

`-zscore`  
Print the z-score difference between two input files ZSCORE = Sum( |((A - mean(A)) / stdev(A)) - ((B - mean(B)) / stdev(B))| ) / n

`-similarity`  
Calculate the confusion matrix, assuming that the volume values represent a discrete class of possible values. The maximum label value is currently limited to ten (10). Prints the Dice similarity statistic as well as specificity, sensitivity, accuracy, and kappa for each class and for the overall volumes.

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

Copyright © 2010 by Andrew Janke
