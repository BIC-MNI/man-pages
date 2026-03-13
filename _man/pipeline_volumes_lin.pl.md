---
section: 1
title: pipeline_volumes_lin.pl
author: Vladimir S. Fonov
group: BIC Processing Pipelines
---
# pipeline_volumes_lin.pl

compute brain tissue volumes from linear registration

`pipeline_volumes_lin.pl <mask> <cls> <xfm> <output.txt> [options]`

## DESCRIPTION

**pipeline_volumes_lin.pl** computes brain tissue volumes using a linear
(affine) registration to stereotaxic space. The script takes a brain mask,
tissue classification volume, and linear transform, and calculates the total
volume of each tissue class (white matter, grey matter, cerebrospinal fluid)
and the total intracranial volume (ICV).

Volumes are corrected for the scaling component of the linear transform to
report values in native-space cubic millimetres. The output is a text file
containing the computed volumes along with optional metadata such as age,
scanner information, and input filenames.

## OPTIONS

`--verbose`
:   Print progress information during processing.

`--clobber`
:   Overwrite the output file if it already exists.

`--age <n>`
:   Subject age in years, included as metadata in the output file.

`--scanner <name>`
:   Scanner model or identifier, included as metadata in the output file.

`--scanner_id <id>`
:   Scanner serial number or unique identifier, included as metadata in the
    output file.

`--t1 <file>`
:   Path to the T1-weighted input volume, recorded in the output file.

`--t2 <file>`
:   Path to the T2-weighted input volume, recorded in the output file.

`--pd <file>`
:   Path to the proton-density input volume, recorded in the output file.

## EXAMPLES

Compute tissue volumes:

    pipeline_volumes_lin.pl brain_mask.mnc classified.mnc tal.xfm volumes.txt

Compute volumes with metadata:

    pipeline_volumes_lin.pl brain_mask.mnc classified.mnc tal.xfm volumes.txt \
      --age 25 --scanner Siemens_Trio --scanner_id S001

Compute volumes with input file references:

    pipeline_volumes_lin.pl brain_mask.mnc classified.mnc tal.xfm volumes.txt \
      --t1 t1_native.mnc --t2 t2_native.mnc --pd pd_native.mnc --clobber

## AUTHOR

Vladimir S. Fonov - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## SEE ALSO

[pipeline_volumes_nl.pl](pipeline_volumes_nl.pl)
