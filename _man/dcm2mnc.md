---
section: 1
title: dcm2mnc
author: 
- Peter Neelin 
- Richard D. Hoge
---
# dcm2mnc

dcm2mnc convert sets of DICOM files to one or more MINC format files.

`dcm2mnc <options> <input-list> <output-dir>`

## DESCRIPTION

The `dcm2mnc` command is used to convert DICOM format files to MINC format.

DICOM (Digital Imaging and Communications in Medicine) format is used by many vendors of medical imaging equipment as a standard means of data interchange. The DICOM specification is extremely complex and includes protocols for data interchange and communications as well as the specifics of the data format. In most cases, tens or even hundreds of DICOM files must be combined to produce a single MINC file.

In normal operation, the *input-list* will consist of the names of one or more files or directories. The program scans all specified input files and directories and attempts to identify groups of files that should be combined into a single MINC file. Once these groups (or "series") of DICOM files are identified, the program analyzes the data for each series and attempts to determine the correct geometry and ancillary information to be incorporated into the MINC file.

If all goes well, one or more MINC files will be created in one or more subdirectories created in the specified directory *output-dir*. These directories and files will be automatically named according to the patient's name, the acquisition date, acquisition time, series identifier, and modality.

For a variety of reasons, medical imaging manufacturers have chosen to implement a number of proprietary extensions to the DICOM format. This program attempts to be very general, but it does some extra checking for specific proprietary fields where useful or necessary. However, as device settings change and software is updated, the precise details of the DICOM output for a given device may shift. Different devices from the same manufacturer may produce substantially different DICOM output.

## OPTIONS

Note that options can be specified in abbreviated form (as long as they are unique) and can be given anywhere on the command line.

## Output file options

`-clobber`  
Overwrite existing files. By default, `dcm2mnc` will not write over an existing file.

`-anon`  
Do not store the patient name in the MINC file. The string "anonymous" will be used instead. Note that all other identifying information will still be stored in the file.

`-nosplitecho`  
Do not split echoes into separate files. If multiple echoes are present in a series, they will all be stored in a single MINC file with a dimension named "echo".

`-splitdynamic`  
Split dynamic scans into separate files. Normally dynamic scans are stored in a single MINC file with a "time" dimension. If this option is specified, each time slice will be saved in a separate file.

`-fname` `<format-spec>`
Set the format of the output file name. See FILENAMES section for details on this option.

`-dname` `<format-spec>`
Set the format of the output subdirectory name. See FILENAMES section for details on this option. Set this to the empty string to avoid creating a subdirectory.

## Siemens mosaic specific options

These two options control the manner in which Siemens mosaic data is converted. Siemens scanners commonly represent fMRI data as a "mosaic" of subimages combined into a single large image. Normally these are in what we call "ascending" order, but if your functional image is not converted properly, you may need to specify one of these options. NOTE that the mosaic order is often not the same as the slice acquisition order.

`-descending`  
The mosaic image is stored in descending order.

`-interleaved`  
The mosaic image is stored in alternating (odd/even) order.

## Other options

`-stdin`  
This option tells `dcm2mnc` to read a list of input files from the standard input in addition to any files specified on the command line.

`-cmd`<string>  
This option will apply the given command string to each output file after it is created. Can be used to run gzip or compress on each output file, for example.

`-minmax`  
Use the values for the largest and smallest pixel value as stored in the DICOM file. This is useful especially with GE PET data, but may be needed to get a quantitatively accurate conversion with other manufacturers. If this option is not specified. .B dcm2mnc uses the full range of the datatype as specified by the number of bits stored per voxel (field \# 0028,0101). When this option is specified, the 0028,0106 and 0028,0107 will be used to set the valid range of pixels.

`-list`  
List files in series, but do not perform conversion. Sometimes useful for verifying the validity of a dataset, and for debugging problems with `dcm2mnc`.

`-verbose`  
Verbose operation. Prints a large amount of additional information about the program's operation. This information can probably only be interpreted by someone familiar with both this program and the DICOM standard.

`-debug`  
Extremely verbose operation. Prints a huge amount of additional information about the program's operation. This information can probably only be interpreted by someone familiar with both this program and the DICOM standard.

`-usecoordinates`  
This option requests that the conversion rely on the slice coordinates rather than the standard DICOM fields for slice thickness and spacing. It is useful if for some reason the standard DICOM fields for slice thickness and spacing are incorrect.

`-opts`<value>  
This is a private option intended only for debugging purposes. Please avoid using it.

## Generic options for all commands

`-help`  
Print summary of command-line options and abort

`-version`  
Print the program and library versions and abort

## FILENAMES

To avoid naming collisions when converting a large set of input DICOM files to a smaller set of MINC output files, `dcm2mnc` automatically generates the names of output files according to various parameters of the DICOM file information. The normal behavior is to place all of the output files in a subdirectory of the given output directory which has its name derived from the patient's name and the study date and time as follows:

`patientname_yyyymmdd_hhmmss/`

The individual files are named according to the patient name, study date and time, series identifer, and modality information as follows:

`patientname_yyyymmdd_hhmmss_series_scan_modality.mnc`

The optional scan information includes the echo number ('e<n>'), slice number ('sl<n>'), time series position ('d<n>'), phase number ('p<n>'), or chemical shift ('cs<n>').

The optional modality information consists of either the string "_pet" or "_mri". No suffix is added for unrecognized modalities.

The `-fname` and `-dname` commands allow the user to override the standard file naming behavior by specifying alternative output directory and file formats. The arguments to these options are template strings that will be expanded to include information from the DICOM sequences in specified locations. Replacements are specified by a '%' character followed by a single alphabetic character, as follows:

- `%N` - Name of patient 
- `%D` - Date of scan
- `%T` - Time of scan 
- `%S` - Study ID (typically 'yyyymmdd.hhmmss')
- `%A` - Acquisition or series ID
- `%s` - Optional slice label
- `%e` - Optional echo number
- `%t` - Optional dynamic scan number
- `%p` - Optional phase number
- `%c` - Optional chemical shift number
- `%m` - Optional modality

The default file name convention is therefore given by the format string: `%N_%D_%T_%A%s%e%t%p%c%m`
and the default directory name is given by the format string: `%N_%D_%T`

If you wish to avoid creating a subdirectory, you may do so by giving a zero-length string as the argument to the `-dname` option:

`dcm2mnc -dname '' filenames...`

## AUTHORS

Peter Neelin and Richard D. Hoge

Please direct all complaints and inquiries to [Robert Vincent](bert@bic.mni.mcgill.ca)

## BUGS

Probably many. For best results, output files should be checked by a competent human to verify that the conversion was performed properly. DICOM is a very complex format, and it is difficult to anticipate all of the possible combinations of fields and values that may be encountered. If you have a problem, please contact the maintainer. It will be extremely useful if you can provide an example dataset that exhibits the problem you have discovered.

## SEE ALSO

For more information on DICOM, visit the NEMA (National Electrical Manufacturer's Association) website at <http://dicom.nema.org> and also see David Clunie's excellent website on medical image formats at *<http://www.dclunie.com>*

Many manufacturers create "DICOM Conformance Statements" for each software release associated with their medical imaging products. These can be useful sources of information.

## COPYRIGHTS

Copyrights 1993-2005 by Peter Neelin for the Montreal Neurological Institute.
