minctoecat
1
minctecat
convert a minc format file to an Ecat7 format file
minctoecat
<options>
<infile.mnc>
<outfile.v>
minctoecat
-help
DESCRIPTION
===========

`minctoecat` will convert a 2D image, a 3D volumes or a 4D dynamic volumes written in minc file format to a 2D, 3D or 4D Ecat7 file. Whereas the Ecat7 format has been designed for PET volume issued by Ecat scanners (CTI/SIEMENS - Knoxville, TN, USA) it reads any minc volume type (static PET, dynamic PET, aMRI, fMRI, labels) natively delivered by any tomograph brand and transform it to a viable Ecat7 file in term of number of dimensions, dimension size, dimension step, orientation, spatial position, voxel values and voxel unit. Furthermore, it tries the best as it can to fill optional Ecat7 header fields from the available minc variables and attributes. By default, it extracts these additional information from common minc variables, namely: patient\_variable, study\_variable, acquisition\_variable. In the case of volumes originally delivered by an Ecat PET scanners, then, other variable are generally available within the minc header: ecat\_acquisition\_variable, ecat\_main and ecat\_sub-header\_variable. There, for a such minc volume, the conversion yields a Ecat7 volume almost identical to the original native volume in terms of header fields. The user can alter this behaviour using the ignore-list options (see the option section).

OPTIONS
=======

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

Command specific options
========================

-   `-ignore_patient_variable:` Ignore information from the minc patient variable (MIpatient).

-   `-ignore_study_variable:` Ignore information from the minc study variable (MIstudy).

-   `-ignore_acquisition_variable:` Ignore information from the minc acquisition variable (MIacquisition).

-   `-ignore_ecat_accquisition_variable:` Ignore information from the minc ecat acquisition variable (MIecat\_acquisition).

-   `-ignore_ecat_main_variable:` Ignore information from the minc ecat-mainheader variable (MIecat-main).

-   `-ignore_ecat_subheader_variable:` Ignore information from the minc ecat-subheader variable (MIecat-subheader).

-   `-no_decay_corr_fctr:` do not regenerate the decay correction factors employed as part as the reconstruction of the original PET volume. The correction factors is a field in the ecat sub-headers which can be used by processing programs. By default, if the volume is a PET volume ,those factors are regenerated. This option has no interest in the case of non PET data.

-   `-label:` Treats voxel as integer values instead of floating point values. In this case, the scale factors and the calibration factors are both set to unity. This option is particularly useful when the input minc files is a volume of labels.

-   `-ignore_mid_frame_offset:` Time points as defined in the minc file are then assumed to correspond to the frame start time (by default they are assumed to be the mid frame time value).

General options
===============

-   `-help:` Print summary of command-line options and abort

-   `-version:` Print the program's version and abort

KNOWN BUGS
==========

No bug listed so far :=)

SEE ALSO
========

ecattominc1, rawtominc1, minctoraw1, dicomtominc1

AUTHOR
======

Anthonin Reilhac (anthonin.reilhac@cermep.fr)

COPYRIGHTS
==========

Copyrights 2005 by Anthonin Reilhac
