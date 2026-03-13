---
section: 1
title: pipeline_pve.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_pve.pl

partial volume estimation pipeline

`pipeline_pve.pl <t1_tal> <classified> <output_base>`

## DESCRIPTION

**pipeline_pve.pl** performs partial volume estimation (PVE) on a classified
brain volume. While tissue classification assigns each voxel to a single tissue
class, PVE estimates the fractional content of white matter, grey matter, and
cerebrospinal fluid within each voxel. This is particularly important at tissue
boundaries where a single voxel may contain a mixture of tissue types.

The script takes a T1-weighted volume in Talairach space and its corresponding
discrete tissue classification as input, and produces partial volume maps with
the given output base name. The output files typically include separate volumes
for the fractional content of each tissue class.

## OPTIONS

`-verbose`
:   Print progress information during processing.

`-clobber`
:   Overwrite output files if they already exist.

## EXAMPLES

Compute partial volume estimates:

    pipeline_pve.pl t1_tal.mnc classified.mnc pve_output

Compute with verbose output:

    pipeline_pve.pl t1_tal.mnc classified.mnc pve_output -verbose

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_classify.pl](pipeline_classify.pl), [pipeline_smooth.pl](pipeline_smooth.pl)
