---
section: 1
title: pipeline_relx_cls.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_relx_cls.pl

T2 relaxometry-based tissue classification

`pipeline_relx_cls.pl <t1> <t2> <pd> <t2_relx> <output_cls> [options]`

## DESCRIPTION

**pipeline_relx_cls.pl** performs tissue classification that incorporates T2
relaxometry information in addition to the standard T1, T2, and PD contrast
volumes. By using the T2 relaxation map as an additional feature, the
classifier can better distinguish between tissue types that may have similar
intensities on conventional contrasts but different relaxation properties.

The script takes T1-weighted, T2-weighted, and proton-density volumes along
with a pre-computed T2 relaxation map, and produces a discrete tissue
classification. Atlas priors for GM, WM, and CSF can be specified, and the
age parameter allows age-appropriate classification thresholds.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--mask <file>`
:   Brain mask to restrict classification to the brain region.

`--atlas <file>`
:   Atlas prior probability map for tissue classification.

`--atlas_gm <file>`
:   Atlas prior probability map specifically for grey matter.

`--atlas_wm <file>`
:   Atlas prior probability map specifically for white matter.

`--atlas_csf <file>`
:   Atlas prior probability map specifically for cerebrospinal fluid.

`--xfm <file>`
:   Linear transformation mapping the input volumes to the atlas space.

`--age <n>`
:   Subject age in years, used to adjust classification parameters for
    age-appropriate tissue boundaries. Default is 20.

`--blur <n>`
:   Blurring kernel size in millimetres applied to the atlas priors.
    Default is 4.

## EXAMPLES

Classify using T2 relaxometry with default settings:

    pipeline_relx_cls.pl t1_tal.mnc t2_tal.mnc pd_tal.mnc \
      t2_relx.mnc relx_cls.mnc

Classify with custom atlas priors and age:

    pipeline_relx_cls.pl t1_tal.mnc t2_tal.mnc pd_tal.mnc \
      t2_relx.mnc relx_cls.mnc \
      --atlas_gm gm_prior.mnc --atlas_wm wm_prior.mnc \
      --atlas_csf csf_prior.mnc --age 65

Classify with a brain mask and transform:

    pipeline_relx_cls.pl t1_tal.mnc t2_tal.mnc pd_tal.mnc \
      t2_relx.mnc relx_cls.mnc --mask brain_mask.mnc --xfm tal.xfm

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_relx.pl](pipeline_relx.pl), [pipeline_classify.pl](pipeline_classify.pl)
