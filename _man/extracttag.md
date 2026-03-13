---
section: 1
title: extracttag
author: John G. Sled
group: Non-Uniformity Correction
---
# extracttag

extract tag points from a probability mask volume

`extracttag [options] <prob_mask_filename>`

## DESCRIPTION

**extracttag** extracts tag points from a probability mask volume. Tag points
are spatial coordinates sampled from voxels that meet specified threshold
criteria within the mask. The output can be either a tag file or a tag volume.
This tool is used in the N3 non-uniformity correction pipeline to select
representative sample points for field estimation.

## OPTIONS

`-verbose`
:   Print progress information.

`-clobber`
:   Overwrite an existing output file.

`-debug <n>`
:   Set debug level to n.

`-volume`
:   Generate a tag volume as output.

`-tag`
:   Generate a tag file as output.

`-mintags`
:   Set the minimum number of tags to extract.

`-maxtags`
:   Set the maximum number of tags to extract. Use 0 to extract all qualifying tags.

`-threshold <min> <max>`
:   Set the lower and upper intensity thresholds for tag extraction.

`-top_thres <val>`
:   Set the upper threshold value (default: 1.001).

`-label`
:   Use voxel label values.

`-mask <mask.mnc>`
:   Specify a mask volume to restrict tag extraction.

`-user_mask_value <n>`
:   Set the mask value for inclusion (default: 1).

`-mask_floor <n>`
:   Set the minimum mask value for inclusion (default: 1).

`-mask_ceil <n>`
:   Set the maximum mask value for inclusion.

`-mask_binvalue <n>`
:   Set the binary mask value for inclusion.

`-world`
:   Traverse the mask volume in world coordinates.

`-random`
:   Use random step sizes when traversing the volume.

`-comment`
:   Add a comment to the output tag file.

`-append`
:   Append to an existing tag file instead of overwriting.

## EXAMPLES

    extracttag -tag -maxtags 10000 prob_mask.mnc > tags.tag

    extracttag -mask brain_mask.mnc -threshold 0.5 1.0 prob_mask.mnc > tags.tag

## AUTHOR

John G. Sled - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; 1998 by John G. Sled

## SEE ALSO

[nu_estimate](nu_estimate), [nu_correct](nu_correct), [volume_stats](volume_stats)
