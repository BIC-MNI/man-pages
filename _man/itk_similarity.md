---
section: 1
title: itk_similarity
author: Vladimir S. Fonov
group: ITK Image Processing
---
# itk_similarity

calculate various ITK image similarity metrics between two volumes

`itk_similarity <src> <target> [options]`

## DESCRIPTION

**itk_similarity** computes image similarity metrics between two input volumes
using the Insight Toolkit (ITK). The tool supports a range of intensity-based
and overlap-based metrics commonly used to evaluate registration quality,
compare segmentation results, or measure inter-subject image correspondence.

Both volumes must be defined on the same sampling grid (same dimensions,
voxel sizes, and orientation). An optional mask can restrict the computation
to a specific region of interest.

Available metrics include mutual information (MI), normalized mutual
information (NMI), Mattes mutual information (MMI), mean squared difference
(MSQ), cross-correlation (CC), normalized cross-correlation (NCC), and
Cohen's kappa for label overlap (kappa).

## OPTIONS

`--verbose`
:   Print verbose information during processing.

`--clobber`
:   Overwrite any output file if it already exists.

`--mi`
:   Compute mutual information (Viola-Wells formulation).

`--nmi`
:   Compute normalized mutual information.

`--mmi`
:   Compute Mattes mutual information.

`--msq`
:   Compute mean of squared differences.

`--cc`
:   Compute cross-correlation.

`--ncc`
:   Compute normalized cross-correlation.

`--kappa`
:   Compute Cohen's kappa coefficient for label overlap comparison.

`--mask` *file*
:   Restrict the similarity computation to voxels within the given mask volume. Only voxels with non-zero values in the mask are included.

`--bins` *n*
:   Set the number of histogram bins used for mutual-information-based metrics. Default is 64.

## EXAMPLES

Compute mutual information between two volumes:

    itk_similarity source.mnc target.mnc --mi

Compute normalized cross-correlation within a brain mask:

    itk_similarity source.mnc target.mnc --ncc --mask brain_mask.mnc

Compute Mattes mutual information with 128 histogram bins:

    itk_similarity source.mnc target.mnc --mmi --bins 128

Compute kappa overlap for label volumes:

    itk_similarity labels_a.mnc labels_b.mnc --kappa

Compute multiple metrics at once:

    itk_similarity source.mnc target.mnc --mi --msq --ncc

## AUTHOR

Vladimir S. Fonov - Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright (C) Vladimir S. Fonov, McConnell Brain Imaging Centre, McGill University.

## SEE ALSO

[multiple_volume_similarity](multiple_volume_similarity), [minccalc](minccalc), [itk_resample](itk_resample), [mincstats](mincstats)
