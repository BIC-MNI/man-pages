---
section: 1
title: gamixture
author: Vladimir S. Fonov
group: MRF Segmentation
---
# gamixture

Genetic algorithm for Gaussian mixture model parameter optimization.

`gamixture [-unsigned] <imagefile> <maskfile> <atlasfile> <fmmparamfile> [parameters]`

## DESCRIPTION

**gamixture** uses a genetic algorithm (GA) to estimate optimal parameters for
a Gaussian mixture model from a volume histogram. The tool reads an input image,
a brain mask, and an atlas file, and writes the estimated mixture model
parameters (means, variances, and mixing proportions) to the specified
output parameter file.

The genetic algorithm evolves a population of candidate solutions using
crossover, mutation, and selection operations to minimize the difference
between the observed histogram and the mixture model. The resulting
parameters can be used as input to MRF-based tissue segmentation tools
such as **mrfseg**.

## OPTIONS

`-unsigned`
:   Treat image intensities as unsigned values.

`-alpha` *value*
:   Set the blended crossover parameter. Default: 0.5.

`-size` *n*
:   Set the population size for the genetic algorithm. Default: 100.

`-terminationthr` *value*
:   Set the termination threshold for convergence. Default: 0.0005.

`-xoverrate` *value*
:   Set the crossover rate. Default: 1.

`-maxgenerations` *n*
:   Set the maximum number of generations. Default: 500.

`-sortpop` *n*
:   Enable permutation operator for population sorting. Default: 1.

`-parzenn` *n*
:   Set the number of Parzen window estimation points. Default: 101.

`-parzensigma` *value*
:   Set the Parzen window width (sigma). Default: 1.

`-equalvar` *n*
:   Constrain all classes to have equal variances. Default: 0 (off).

`-restarts` *n*
:   Number of independent GA runs to perform. Default: 1.

## EXAMPLES

Estimate mixture parameters for a T1 volume:

    gamixture t1.mnc brainmask.mnc atlas.mnc mixture_params.txt

Estimate with increased population size and more generations:

    gamixture -size 200 -maxgenerations 1000 t1.mnc brainmask.mnc atlas.mnc params.txt

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 2011 by Vladimir S. Fonov

## SEE ALSO

[mrfseg](mrfseg), [em_classify](em_classify)
