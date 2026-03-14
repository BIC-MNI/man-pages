---
---
# minc-toolkit documentation project

This is collection of documentation files for various minc tools. It was auto-converted from the 
legacy .man files to github-style markup format and then manually corrected. 

## MINC Core Tools

* [mincinfo](man/mincinfo) - print out general information about a minc file
* [mincheader](man/mincheader) - print out complete header information for a minc file
* [mincstats](man/mincstats) - calculate simple statistics across voxels of a minc file
* [mincdiff](man/mincdiff) - report differences between minc files
* [voxeltoworld](man/voxeltoworld) - convert voxel coordinates to world coordinates
* [worldtovoxel](man/worldtovoxel) - convert world coordinates to voxel coordinates
* [minchistory](man/minchistory) - display the history of processing steps applied to a MINC file
* [mincpik](man/mincpik) - generate image files from MINC volumes
* [minccomplete](man/minccomplete) - check if a MINC or xfm file has been completely written
* [mincmorph](man/mincmorph) - perform morphological operations on MINC volumes

## File Format Conversion

* [rawtominc](man/rawtominc) - converts a stream of binary image data to a minc format file
* [mincconvert](man/mincconvert) - convert between MINC 1 to MINC 2 format
* [dcm2mnc](man/dcm2mnc) - convert sets of DICOM files to one or more MINC format files
* [ecattominc](man/ecattominc) - convert an ecat format file (version 6.x or 7.x) to a minc format file
* [minctoecat](man/minctoecat) - convert a minc format file to an Ecat7 format file
* [minctoraw](man/minctoraw) - copy data from a MINC file
* [mnc2nii](man/mnc2nii) - convert a MINC format file to a NIfTI-1 or Analyze format file
* [nii2mnc](man/nii2mnc) - convert a NIfTI-1 or Analyze 7.5 format file to a MINC format file
* [upet2mnc](man/upet2mnc) - convert a Concorde microPET format file to a MINC format file
* [vff2mnc](man/vff2mnc) - convert set of vff file(s) to one 3D MINC2.0 format file
* [mri_to_minc](man/mri_to_minc) - convert various MRI scanner formats to MINC format
* [ecat2hdf5](man/ecat2hdf5) - convert ECAT format PET data to HDF5 format

## Low-Level File Manipulation

* [minc_modify_header](man/minc_modify_header) - modify the attributes in the header of a minc file
* [minccopy](man/minccopy) - copy minc image values from one minc file to another
* [mincdump](man/mincdump) - convert minc files to ASCII form (CDL)
* [mincedit](man/mincedit) - edit a MINC file header
* [mincexpand](man/mincexpand) - expands a compressed minc file, if necessary
* [mincextract](man/mincextract) - dump a hyperslab of MINC file data
* [invert_raw_image](man/invert_raw_image) - invert 2D image along either or both axes
* [mincgen](man/mincgen) - generate a MINC file from a CDL file
* [mincdefrag](man/mincdefrag) - remove small disconnected fragments from a labelled MINC volume

## Mathematical Operations on Voxel Level

* [minccalc](man/minccalc) - perform complex math operations on minc files
* [minccmp](man/minccmp) - compare one or more minc file using comparator operators
* [minclookup](man/minclookup) - perform lookup table conversions on minc files
* [mincmakescalar](man/mincmakescalar) - convert vector minc files to scalar
* [mincmakevector](man/mincmakevector) - convert a list of scalar minc files into one vector file
* [mincmath](man/mincmath) - perform simple math operations on minc files
* [mincwindow](man/mincwindow) - limit voxel values to a given range

## Volume Operations

* [mincaverage](man/mincaverage) - average minc files
* [mincblur](man/mincblur) - convolve an input volume with a Gaussian blurring kernel
* [mincresample](man/mincresample) - resamples a minc file along new spatial dimensions
* [mincreshape](man/mincreshape) - cuts a hyperslab out of a minc file (with dimension re-ordering)
* [mincsample](man/mincsample) - generate samplings from minc files
* [autocrop](man/autocrop) - tool for extracting and manipulating bounds of a MINC file
* [mincblob](man/mincblob) - calculate blobs from minc deformation grids
* [mincconcat](man/mincconcat) - concatenate minc files along a specific dimension
* [mincbbox](man/mincbbox) - calculate the bounding box of non-zero data in a MINC volume
* [mincmask](man/mincmask) - apply a binary mask to a MINC volume
* [mincskel](man/mincskel) - compute the skeleton (medial surface) of a white matter partial volume estimate
* [minctotag](man/minctotag) - convert labelled voxels in a MINC volume to a tag point file
* [autocrop_volume](man/autocrop_volume) - crop a MINC volume by removing outer voxels below a threshold
* [average_voxels](man/average_voxels) - average voxels in blocks within a MINC volume
* [box_filter_volume](man/box_filter_volume) - apply a box filter (uniform averaging) to a MINC volume
* [box_filter_volume_nd](man/box_filter_volume_nd) - apply an n-dimensional box filter to a MINC volume
* [chamfer_volume](man/chamfer_volume) - compute the chamfer distance transform of a binary volume
* [clamp_volume](man/clamp_volume) - clamp voxel values in a MINC volume to a specified range
* [cluster_volume](man/cluster_volume) - label connected components in a thresholded MINC volume
* [copy_stats_to_volume](man/copy_stats_to_volume) - copy per-vertex statistics to a volume using a surface mapping
* [count_thresholded_volume](man/count_thresholded_volume) - count non-zero mask voxels corresponding to volume values within a threshold
* [create_four_volumes](man/create_four_volumes) - create four class volumes from multiple input volumes or tag files
* [dilate_volume](man/dilate_volume) - dilate regions of a specified value in a MINC volume
* [dilate_volume_completely](man/dilate_volume_completely) - fully dilate regions of a specified value until no further dilation is possible
* [evaluate](man/evaluate) - evaluate a volume at the vertices of a surface object
* [find_image_bounding_box](man/find_image_bounding_box) - find the bounding box of an RGB image excluding the background colour
* [find_volume_centroid](man/find_volume_centroid) - find and print the centroid of a MINC volume
* [flip_volume](man/flip_volume) - interchange voxel values with their left-right opposites in a MINC volume
* [histogram_volume](man/histogram_volume) - compute and output a histogram of voxel intensities in a MINC volume
* [make_diff_volume](man/make_diff_volume) - create a 4-class volume based on value ranges in two input volumes
* [make_geodesic_volume](man/make_geodesic_volume) - create a geodesic distance volume from a seed point in a MINC volume
* [make_gradient_volume](man/make_gradient_volume) - compute gradient magnitude or second derivative of a MINC volume
* [mask_volume](man/mask_volume) - mask a MINC volume by setting voxels outside a specified mask range
* [normalize_pet](man/normalize_pet) - intensity normalize a PET MINC volume
* [preprocess_segmentation](man/preprocess_segmentation) - preprocess a classified volume for cortical segmentation
* [random_volume](man/random_volume) - generate a random volume matching a sample volume geometry
* [random_warp](man/random_warp) - create a random warp (deformation) transform from a surface object
* [scale_minc_image](man/scale_minc_image) - scale voxel intensities in a MINC volume by a constant factor
* [scan_object_to_volume](man/scan_object_to_volume) - scan a BIC object into a MINC volume creating a binary mask
* [subsample_volume](man/subsample_volume) - subsample a MINC volume by taking every nth voxel in each dimension
* [threshold_volume](man/threshold_volume) - create a label volume by thresholding an input MINC volume
* [transform_volume](man/transform_volume) - apply a spatial transform to a MINC volume by modifying its voxel-to-world transform
* [volume_object_evaluate](man/volume_object_evaluate) - evaluate volume values at surface object vertex positions
* [voldiff](man/voldiff) - compare classified volumes and produce a difference volume
* [volume_cog](man/volume_cog) - compute the intensity-weighted center of gravity of a MINC volume

## Registration and Transformation

* [minctracc](man/minctracc) - estimates the spatial transformation required to register two volumes together
* [mritoself](man/mritoself) - intra-subject registration of two volumetric data sets
* [mritotal](man/mritotal) - performs multi-scale fitting of a normal human brain to a standard model
* [xfm2def](man/xfm2def) - convert a MNI transform file to a deformation volume
* [xfmconcat](man/xfmconcat) - concatenate MNI transform files
* [xfminvert](man/xfminvert) - invert an MNI transform file
* [xfmflip](man/xfmflip) - flip an MNI transform file
* [transformtags](man/transformtags) - apply MNI transform to a tag file
* [param2xfm](man/param2xfm) - create a MNI transform file from rotation, translation, scale, and shear parameters
* [xfm2param](man/xfm2param) - extract rotation, translation, scale, and shear parameters from a MNI transform file
* [xfmtool](man/xfmtool) - manipulate MNI transformation files
* [xfmdecomp](man/xfmdecomp) - decompose a .xfm transformation into rotation, translation, scale, and shear
* [cmpxfm](man/cmpxfm) - compare two MNI linear transform files element-by-element
* [check_scale](man/check_scale) - check and correct the Z-scale of a MNI linear transform
* [volume_cog](man/volume_cog) - compute the intensity-weighted center of gravity of a MINC volume
* [xcorr_vol](man/xcorr_vol) - compute the normalized cross-correlation between two MINC volumes

## Tag Point Tools

* [transform_tags](man/transform_tags) - apply a spatial transformation to a tag point file
* [minctotag](man/minctotag) - convert labelled voxels in a MINC volume to a tag point file
* [chop_tags](man/chop_tags) - clip tag points to those within specified coordinate ranges
* [clip_tags](man/clip_tags) - clip tag points based on distance from a reference plane
* [extract_tag_slice](man/extract_tag_slice) - extract tag points lying on a specified slice of a volume
* [find_tag_outliers](man/find_tag_outliers) - identify tag points that deviate significantly from expected positions
* [flip_tags](man/flip_tags) - flip tags about the left-right centre of a volume
* [interpolate_tags](man/interpolate_tags) - interpolate tag points between two sets by a given ratio
* [match_tags](man/match_tags) - find corresponding tag points between two tag files
* [stats_tag_file](man/stats_tag_file) - compute and display statistics for a tag file
* [tag_volume](man/tag_volume) - create a volume from tag points sampling at specified y-axis intervals
* [tags_to_spheres](man/tags_to_spheres) - create sphere objects at tag point positions
* [tagtominc](man/tagtominc) - convert a tag file to a labelled MINC volume
* [dump_points_to_tag_file](man/dump_points_to_tag_file) - write surface object points to a tag file

## Surface and Geometry Tools

* [apply_sphere_transform](man/apply_sphere_transform) - apply a spherical transform to a surface object
* [blur_surface](man/blur_surface) - blur a surface object using a Gaussian kernel
* [coalesce_lines](man/coalesce_lines) - coalesce shared points in a lines object
* [compare_lengths](man/compare_lengths) - compare edge lengths between two polygon meshes
* [contour_slice](man/contour_slice) - create contour lines for a given slice of a volume
* [convex_hull](man/convex_hull) - create a convex hull polyhedron from a surface or volume
* [create_2d_sheet](man/create_2d_sheet) - create a 2D sheet representation of a surface object
* [create_2d_surface](man/create_2d_surface) - create a 2D surface representation of a 3D surface object
* [create_box](man/create_box) - create a rectangular box object file
* [create_landmark_full_volume](man/create_landmark_full_volume) - create a label volume from landmark tag files
* [create_surface_interpolation_lsq](man/create_surface_interpolation_lsq) - create a least-squares surface interpolation from scattered data
* [create_warping_points](man/create_warping_points) - create warping tag points from surface correspondences
* [extract_largest_line](man/extract_largest_line) - extract the largest connected line from a line object
* [find_buried_surface](man/find_buried_surface) - find buried regions on a polygon surface based on curvature radius
* [find_surface_distances](man/find_surface_distances) - compute distances from a surface to threshold boundaries in a volume
* [find_vertex](man/find_vertex) - find a specific vertex in a surface object
* [fit_3d](man/fit_3d) - fit a deformable model to a MINC volume using surface deformation
* [fit_curve](man/fit_curve) - fit a smooth cubic spline curve to a set of points
* [fit_curve2](man/fit_curve2) - fit a piecewise linear curve to a set of points
* [flatten_polygons](man/flatten_polygons) - flatten a polygonal surface into 2D
* [flatten_sheet](man/flatten_sheet) - flatten a surface sheet to a 2D plane
* [flatten_sheet3](man/flatten_sheet3) - flatten a surface sheet to a 2D plane using topological or physical method
* [flatten_to_sphere](man/flatten_to_sphere) - map a surface onto a sphere
* [flatten_to_sphere2](man/flatten_to_sphere2) - map a surface onto a sphere with curvature and stretch weights
* [make_grid_lines](man/make_grid_lines) - create grid lines on a surface object
* [make_line_links](man/make_line_links) - create line segments linking two input line objects
* [make_sphere_transform](man/make_sphere_transform) - create a spherical transform mapping for a surface
* [make_surface_bitlist](man/make_surface_bitlist) - create a surface bitlist volume from a thresholded MINC volume
* [map_colours_to_sphere](man/map_colours_to_sphere) - map colours from a volume onto a spherical surface object
* [map_sheets](man/map_sheets) - map surface sheets between spherical and flat representations
* [map_surface_to_sheet](man/map_surface_to_sheet) - map a 3D surface to a flat 2D sheet image
* [marching_cubes](man/marching_cubes) - create a polygonal surface from a thresholded MINC volume using marching cubes
* [plane_polygon_intersect](man/plane_polygon_intersect) - compute the intersection of a plane with a polygonal surface
* [reparameterize_line](man/reparameterize_line) - reparameterize a line object by redistributing points evenly
* [spherical_resample](man/spherical_resample) - resample a surface using spherical parameterization
* [trimesh_resample](man/trimesh_resample) - subdivide and coalesce a triangular mesh
* [trimesh_set_points](man/trimesh_set_points) - set vertex positions in a triangular mesh from another mesh or object
* [trimesh_to_polygons](man/trimesh_to_polygons) - convert a triangular mesh to a triangular mesh to a polygons file
* [two_surface_resample](man/two_surface_resample) - resample a surface using two model surfaces

## Label and Classification Tools

* [add_labels](man/add_labels) - add or modify value-label pairs in a MINC volume
* [classify_sulcus](man/classify_sulcus) - classify sulcal regions on a cortical surface
* [clean_surface_labels](man/clean_surface_labels) - correct labels on a surface object
* [create_label_map](man/create_label_map) - create a label map volume from a template
* [diff_mahalanobis](man/diff_mahalanobis) - compute the difference in Mahalanobis distances between two groups
* [label_sulci](man/label_sulci) - label sulcal regions on a cortical surface using reference sulcal points and value ranges
* [labels_to_rgb](man/labels_to_rgb) - convert label values to RGB colour values using a lookup table
* [lookup_labels](man/lookup_labels) - list or look up value-label pairs in a MINC volume
* [print_all_label_bounding_boxes](man/print_all_label_bounding_boxes) - print voxel counts and bounding boxes for each label in a MINC volume
* [print_all_labels](man/print_all_labels) - print voxel counts for each label in a MINC volume

## Statistical and Analysis Tools

* [compare_left_right](man/compare_left_right) - compare left and right hemispheres of surface objects
* [compare_left_right_groups](man/compare_left_right_groups) - compare left-right hemisphere differences between groups of surface objects
* [compute_resels](man/compute_resels) - compute resolution elements (resels) from cortical surface meshes
* [dump_deformation_distances](man/dump_deformation_distances) - dump deformation distances from a non-linear transformation
* [dump_rms](man/dump_rms) - compute and dump RMS distance between two surfaces
* [dump_transform](man/dump_transform) - dump the voxel-to-world transform of a MINC volume to an .xfm file
* [dump_uv](man/dump_uv) - dump UV texture coordinates of a surface object
* [f_prob](man/f_prob) - compute F-statistic probability values
* [find_peaks](man/find_peaks) - find local maxima (peaks) in a MINC volume
* [gaussian_blur_peaks](man/gaussian_blur_peaks) - create a volume from Gaussian-blurred peak locations
* [get_tic](man/get_tic) - compute statistics for spherical regions in a MINC volume
* [group_diff](man/group_diff) - compute group differences and F-statistics from surface data files
* [intensity_statistics](man/intensity_statistics) - compute intensity statistics within labelled regions of a volume
* [mask_values](man/mask_values) - mask values in a volume based on a range in another volume
* [print_2d_coords](man/print_2d_coords) - print 2D coordinates corresponding to a 3D point on a surface
* [print_axis_angles](man/print_axis_angles) - print angles between native and Talairach axes
* [print_volume_value](man/print_volume_value) - print the voxel value at a given world coordinate in a volume
* [print_world_value](man/print_world_value) - print the voxel value at a given world coordinate in a volume
* [print_world_values](man/print_world_values) - evaluate volume values at multiple world coordinates from a file
* [regional_thickness](man/regional_thickness) - compute regional cortical thickness statistics from per-vertex data

## Image Composition and Visualization

* [composite_images](man/composite_images) - composite multiple RGB images into a single output
* [composite_minc_images](man/composite_minc_images) - composite two MINC images
* [composite_volumes](man/composite_volumes) - composite multiple MINC volumes into a single volume
* [compute_bounding_view](man/compute_bounding_view) - compute the world limits of an object in an orthogonal view
* [concat_images](man/concat_images) - concatenate two RGB images into one
* [dim_image](man/dim_image) - darken an RGB image by a given strength factor
* [make_slice](man/make_slice) - extract a 2D slice from a MINC volume as an image
* [minc_to_rgb](man/minc_to_rgb) - convert a MINC volume to an RGB image
* [place_images](man/place_images) - place multiple RGB images at specified positions in an output image
* [rgb_to_minc](man/rgb_to_minc) - convert RGB images to a MINC volume

## Non-Uniformity Correction

* [correct_field](man/correct_field) - apply a bias field correction to a MINC volume using a mask
* [evaluate_field](man/evaluate_field) - evaluate a compact spline field representation and write it as a MINC volume
* [extracttag](man/extracttag) - extract tag points from a probability mask volume
* [field2imp](man/field2imp) - convert a bias field MINC volume to an IMP format compact representation
* [imp2field](man/imp2field) - convert an IMP format compact representation to a bias field MINC volume
* [make_template](man/make_template) - create a sampling template volume for N3 non-uniformity correction
* [nu_correct](man/nu_correct) - correct intensity non-uniformity artifacts in MRI volumes
* [nu_estimate](man/nu_estimate) - estimate the non-uniformity field in an MRI volume
* [nu_estimate_np_and_em](man/nu_estimate_np_and_em) - estimate non-uniformity using non-parametric and EM methods
* [nu_evaluate](man/nu_evaluate) - evaluate and apply a non-uniformity correction to an MRI volume
* [resample_labels](man/resample_labels) - resample a labelled MINC volume to match a template
* [sharpen_hist](man/sharpen_hist) - create a mapping for minclookup to sharpen a volume histogram
* [sharpen_volume](man/sharpen_volume) - apply histogram sharpening to a MINC volume
* [spline_smooth](man/spline_smooth) - smooth and extrapolate data in MINC volumes using spline fitting
* [volume_hist](man/volume_hist) - create histograms of intensity values in a MINC volume
* [volume_stats](man/volume_stats) - compute and print statistics for a MINC volume

## Intensity Normalization

* [headmask](man/headmask) - create a head mask for MRI intensity normalization
* [inormalize](man/inormalize) - intensity normalize a MINC volume following a registered model volume
* [lgmask](man/lgmask) - create a large-structure brain mask for intensity normalization
* [normalize_mri](man/normalize_mri) - normalize MRI intensity values using a standard approach
* [nu_correct_norm](man/nu_correct_norm) - perform combined non-uniformity correction and intensity normalization

## Classification

* [classify](man/classify) - classify voxels in MRI volumes into tissue classes
* [crispify](man/crispify) - create a crisp labelled volume from multiple fuzzy classification volumes
* [voldiff](man/voldiff) - compare classified volumes and produce a difference volume

## MRF Segmentation

* [gamixture](man/gamixture) - genetic algorithm for Gaussian mixture model parameter optimization
* [mrfseg](man/mrfseg) - MRF-based brain tissue segmentation
* [mrfseg.pl](man/mrfseg.pl) - MRF-based tissue segmentation pipeline

## EZminc Analysis Tools

* [dircos_to_xfm](man/dircos_to_xfm) - convert direction cosines to an .xfm transformation file
* [em_classify](man/em_classify) - classify voxels using expectation-maximization algorithm
* [fast_blur](man/fast_blur) - fast Gaussian blurring of a MINC volume
* [fdr_threshold](man/fdr_threshold) - compute False Discovery Rate (FDR) threshold for statistical maps
* [minc_anlm](man/minc_anlm) - adaptive non-local means denoising of MRI images
* [minc_downsample](man/minc_downsample) - downsample a MINC volume by specified factors
* [minc_nuyl](man/minc_nuyl) - intensity normalization using piece-wise linear histogram matching
* [minc_rank](man/minc_rank) - convert voxel intensities to rank values in the range 0-100
* [minc_taylor_reg](man/minc_taylor_reg) - apply Taylor series-based registration using vector coefficient volumes
* [noise_estimate](man/noise_estimate) - estimate noise level in MRI volumes
* [sharpness_estimate](man/sharpness_estimate) - estimate image sharpness based on median gradient magnitude
* [t2_fit](man/t2_fit) - fit T2 relaxation curves from multiple echo images
* [volume_dwt](man/volume_dwt) - perform forward or backward discrete wavelet transform on a MINC volume
* [volume_pol](man/volume_pol) - polynomial intensity normalization between volumes

## EZminc Volume Similarity

* [fuzzy_volume_similarity](man/fuzzy_volume_similarity) - calculate fuzzy volume similarity metrics for tissue probability maps
* [multiple_volume_similarity](man/multiple_volume_similarity) - calculate multiple volume discrete label similarity (GTC) metrics
* [volume_gtc_similarity](man/volume_gtc_similarity) - calculate generalized Tanimoto coefficient and overlap metrics for discrete labels
* [volume_similarity](man/volume_similarity) - calculate volume similarity metrics for binary label volumes

## EZminc PCA and Linear Modelling

* [grids_pca](man/grids_pca) - perform principal component analysis on deformation grid files
* [volumes_lm](man/volumes_lm) - compute per-voxel linear models from a training list of volumes
* [volumes_lsq](man/volumes_lsq) - compute per-voxel least-squares decomposition using linear model components
* [volumes_pca](man/volumes_pca) - perform principal component analysis on a set of MINC volumes
* [volumes_pca_preprocess](man/volumes_pca_preprocess) - preprocess volumes for PCA analysis

## EZminc Registration Scripts

* [bestlinreg.pl](man/bestlinreg.pl) - perform best linear registration between two MINC volumes
* [bestlinreg_g](man/bestlinreg_g) - perform best linear registration (generalized variant)
* [bestlinreg_s](man/bestlinreg_s) - perform best linear registration (symmetric variant)
* [bestlinreg_s2](man/bestlinreg_s2) - perform best linear registration (symmetric variant 2)
* [nlfit_f](man/nlfit_f) - non-linear fitting at fine resolution step
* [nlfit_l](man/nlfit_l) - non-linear fitting at large/coarse resolution step
* [nlfit_o2](man/nlfit_o2) - non-linear fitting optimization pass 2
* [nlfit_s](man/nlfit_s) - non-linear fitting at standard resolution step

## EZminc QC and Visualization Scripts

* [minc_aqc.pl](man/minc_aqc.pl) - automated quality control assessment of MINC volumes
* [minc_pretty_pic.pl](man/minc_pretty_pic.pl) - generate publication-quality images from MINC volumes
* [minc_pretty_pic_m.pl](man/minc_pretty_pic_m.pl) - generate publication-quality montage images from MINC volumes
* [minc_qc.pl](man/minc_qc.pl) - generate quality control images from MINC volumes
* [minc_qc2.pl](man/minc_qc2.pl) - generate quality control images from MINC volumes (version 2)
* [minc_qc_rgb.pl](man/minc_qc_rgb.pl) - generate RGB quality control images from MINC volumes
* [minc_qc_t2t1.pl](man/minc_qc_t2t1.pl) - generate T2/T1 overlay quality control images

## EZminc Utility Scripts

* [deface_minipipe.pl](man/deface_minipipe.pl) - defacing mini-pipeline for anonymizing MRI volumes
* [deface_volume.pl](man/deface_volume.pl) - deface (remove facial features from) a MINC volume
* [icc_mask.pl](man/icc_mask.pl) - create an intra-cranial cavity mask for brain volume estimation
* [lobe_segment.pl](man/lobe_segment.pl) - segment brain lobes using atlas-based label propagation
* [lobes_to_volumes.pl](man/lobes_to_volumes.pl) - compute lobe volumes from a lobe-segmented MINC volume
* [make_face.pl](man/make_face.pl) - extract a face surface from an MRI volume
* [make_random_grid.pl](man/make_random_grid.pl) - generate a random deformation grid for testing
* [uniformize_minc.pl](man/uniformize_minc.pl) - resample a MINC volume to a uniform axis-aligned grid
* [volume_denoise.pl](man/volume_denoise.pl) - NLM-based volume denoising with automatic noise estimation
* [xfm_normalize.pl](man/xfm_normalize.pl) - normalize an XFM or grid transform to a standard uniform axis-aligned format

## EZminc Analysis Tools (Additional)

* [resample_grid](man/resample_grid) - apply an arbitrary transform to a deformation grid
* [tag2csv](man/tag2csv) - convert a MINC .tag file into comma-separated values (CSV)

## ITK Image Processing

* [itk_convert](man/itk_convert) - convert between medical image formats using ITK (MINC, NIfTI, NRRD, etc.)
* [itk_convert_xfm](man/itk_convert_xfm) - convert transformation files between ITK and MINC .xfm formats
* [itk_diffusion](man/itk_diffusion) - apply anisotropic diffusion filtering to a volume
* [itk_distance](man/itk_distance) - calculate a distance transform on a volume
* [itk_fill_hole](man/itk_fill_hole) - apply hole-filling operation to a volume
* [itk_g_morph](man/itk_g_morph) - perform gray-scale morphological operations on a volume
* [itk_laplace](man/itk_laplace) - apply Laplacian of Gaussian filter to a volume
* [itk_laplacian_sharpening](man/itk_laplacian_sharpening) - apply Laplacian sharpening filter to a volume
* [itk_morph](man/itk_morph) - perform binary morphological image operations (dilate, erode, open, close)
* [itk_resample](man/itk_resample) - resample a MINC volume using ITK with spline interpolation and .xfm transforms
* [itk_similarity](man/itk_similarity) - calculate various ITK image similarity metrics between two volumes
* [itk_vesselness](man/itk_vesselness) - apply vesselness filter for vessel-like structure enhancement

## Deformable Registration

* [DemonsRegistration](man/DemonsRegistration) - diffeomorphic demons registration between two volumes
* [LogDomainDemonsRegistration](man/LogDomainDemonsRegistration) - log-domain diffeomorphic demons registration between two volumes
* [grid_2_log](man/grid_2_log) - convert deformation field to log-domain velocity field (or compute exponent)
* [grid_proc](man/grid_proc) - perform operations on deformation grids: log, exp, magnitude, determinant, inverse
* [grid_statistics](man/grid_statistics) - compute statistics on deformation grid: Jacobian, harmonic energy, magnitude
* [log_resample](man/log_resample) - resample image using log-domain vector field transforms

## Distortion Correction

* [adni_preprocess.pl](man/adni_preprocess.pl) - preprocess ADNI images for distortion correction analysis
* [c_fit_harmonics_grids](man/c_fit_harmonics_grids) - fit cylindrical harmonic coefficients to deformation grids for distortion correction
* [c_param2grid](man/c_param2grid) - convert cylindrical harmonic parameters to deformation grid
* [calc_distortions.pl](man/calc_distortions.pl) - calculate geometric distortion fields from phantom measurements
* [fit_harmonics_grids](man/fit_harmonics_grids) - fit spherical harmonic coefficients to deformation grids
* [fit_harmonics_grids_diff](man/fit_harmonics_grids_diff) - spherical harmonic fitting using paired linear/nonlinear transform differentials
* [fit_harmonics_grids_regularize](man/fit_harmonics_grids_regularize) - spherical harmonic fitting with Legendre polynomial regularization
* [lego_core_extract.pl](man/lego_core_extract.pl) - extract core markers from a LEGO phantom scan
* [par2xfm.pl](man/par2xfm.pl) - convert distortion parameters to an XFM grid transform
* [param2grid](man/param2grid) - convert spherical harmonic parameters to deformation grid
* [phantom_distortion_measure.pl](man/phantom_distortion_measure.pl) - calculate geometric distortion from phantom scans via hierarchical nonlinear registration
* [phantom_distortion_measure_v2.pl](man/phantom_distortion_measure_v2.pl) - measure geometric distortion using paired phantom scan and mask inputs (version 2)
* [phantomfit.pl](man/phantomfit.pl) - hierarchical nonlinear fitting constrained by spherical harmonics using minctracc
* [phantomfit_ANTS.pl](man/phantomfit_ANTS.pl) - hierarchical nonlinear fitting constrained by spherical harmonics using ANTs
* [phantomfit_DD.pl](man/phantomfit_DD.pl) - hierarchical nonlinear fitting constrained by spherical harmonics using Diffeomorphic Demons
* [phantomfit_elastix.pl](man/phantomfit_elastix.pl) - hierarchical nonlinear fitting constrained by spherical harmonics using Elastix

## Patch-Based Morphology

* [hcag_segmentation_pipeline.pl](man/hcag_segmentation_pipeline.pl) - run hippocampus and amygdala segmentation pipeline
* [itk_merge_discrete_labels](man/itk_merge_discrete_labels) - merge multiple discrete label volumes by overlay (non-zero overwrite)
* [itk_merge_labels](man/itk_merge_labels) - merge multiple probability maps into a single label image by maximum probability voting
* [itk_minc_nonlocal_filter](man/itk_minc_nonlocal_filter) - patch-based non-local means denoising
* [itk_patch_grading](man/itk_patch_grading) - patch-based non-local grading using SVM, NNLS, or exponential weighting
* [itk_patch_morphology](man/itk_patch_morphology) - patch-based segmentation using expert priors (Coupe et al. 2010)
* [itk_patch_morphology_mc](man/itk_patch_morphology_mc) - multi-channel patch-based segmentation
* [itk_patch_segmentation](man/itk_patch_segmentation) - perform patch-based label fusion segmentation
* [itk_split_labels](man/itk_split_labels) - split discrete label volume into per-label probability volumes with anti-aliasing
* [patch_segmentation_pipeline.pl](man/patch_segmentation_pipeline.pl) - RASCAL patch-based label fusion segmentation pipeline
* [snipe_grading_pipeline.pl](man/snipe_grading_pipeline.pl) - SNIPE grading pipeline for Alzheimer's disease classification
* [ventricles_segmentation_pipeline.pl](man/ventricles_segmentation_pipeline.pl) - ventricle segmentation pipeline using patch-based methods
* [volume_patches](man/volume_patches) - legacy non-local patch-based segmentation using MINC1 I/O

## BIC Processing Pipelines

* [pipeline_classify.pl](man/pipeline_classify.pl) - brain tissue classification using classify_clean
* [pipeline_dbm.pl](man/pipeline_dbm.pl) - deformation-based morphometry from nonlinear transforms
* [pipeline_deface.pl](man/pipeline_deface.pl) - defacing pipeline for anonymizing MRI data
* [pipeline_deface_grid.pl](man/pipeline_deface_grid.pl) - generate a random distortion grid for defacing
* [pipeline_em_classify.pl](man/pipeline_em_classify.pl) - EM-based brain tissue classification
* [pipeline_face.pl](man/pipeline_face.pl) - FACE anatomical feature extraction pipeline
* [pipeline_jacobian.pl](man/pipeline_jacobian.pl) - compute Jacobian determinant from a nonlinear deformation grid
* [pipeline_launch_all_segment.pl](man/pipeline_launch_all_segment.pl) - launch all segmentation pipeline variants for a subject visit
* [pipeline_launch_pve.pl](man/pipeline_launch_pve.pl) - launch all partial volume estimation pipeline variants
* [pipeline_longitudinal.pl](man/pipeline_longitudinal.pl) - longitudinal brain analysis pipeline
* [pipeline_mritotal.pl](man/pipeline_mritotal.pl) - stereotaxic registration pipeline with BEaST brain masking
* [pipeline_nlr.pl](man/pipeline_nlr.pl) - nonlinear registration pipeline
* [pipeline_pve.pl](man/pipeline_pve.pl) - partial volume estimation pipeline
* [pipeline_qc.pl](man/pipeline_qc.pl) - generate QC images for T1/mask and T1/T2 overlays
* [pipeline_qc_face.pl](man/pipeline_qc_face.pl) - generate QC face renderings from three angles
* [pipeline_qc_nl.pl](man/pipeline_qc_nl.pl) - generate QC images for nonlinear classification and lobe segmentation
* [pipeline_qc_reg.pl](man/pipeline_qc_reg.pl) - generate QC image for nonlinear registration quality
* [pipeline_qc_t1w.pl](man/pipeline_qc_t1w.pl) - generate QC image for T1w in Talairach space with outline overlay
* [pipeline_qc_t2t1.pl](man/pipeline_qc_t2t1.pl) - generate QC image for T1/T2 co-registration overlay
* [pipeline_relx.pl](man/pipeline_relx.pl) - T2 relaxometry fitting from multiple echo volumes
* [pipeline_relx_cls.pl](man/pipeline_relx_cls.pl) - T2 relaxometry-based tissue classification
* [pipeline_segment.pl](man/pipeline_segment.pl) - lobe segmentation using atlas templates
* [pipeline_smooth.pl](man/pipeline_smooth.pl) - smooth tissue probability maps with optional Jacobian modulation
* [pipeline_t2tot1.pl](man/pipeline_t2tot1.pl) - register T2/PD to T1 in Talairach space
* [pipeline_tal_mask.pl](man/pipeline_tal_mask.pl) - apply brain mask to T1/T2/PD volumes in Talairach space
* [pipeline_talnoscale.pl](man/pipeline_talnoscale.pl) - remove scaling from Talairach transform and resample
* [pipeline_thomas.pl](man/pipeline_thomas.pl) - tissue-class Jacobian-modulated blurred maps for THOMAS
* [pipeline_volumes_lin.pl](man/pipeline_volumes_lin.pl) - compute brain tissue volumes from linear registration
* [pipeline_volumes_nl.pl](man/pipeline_volumes_nl.pl) - compute brain and lobe volumes from nonlinear registration
* [pipeline_watermark.pl](man/pipeline_watermark.pl) - apply a visible watermark to an MRI volume

## Registration Scripts

* [compute_icbm_vols](man/compute_icbm_vols) - compute ICBM volumes from a classified image
* [mritotal_suppress](man/mritotal_suppress) - suppress fat signal from MRI data during mritotal registration
* [multispectral_stx_registration](man/multispectral_stx_registration) - perform stereotaxic registration using multi-spectral MRI data
* [nlfit_smr](man/nlfit_smr) - perform non-linear fitting with surface-based multi-resolution
* [remap_to_lobes](man/remap_to_lobes) - remap a detailed segmentation label file to lobe-level labels
* [smooth_mask](man/smooth_mask) - smooth a binary mask volume
* [sphere_resample_obj](man/sphere_resample_obj) - resample a surface object onto a standard sphere tessellation
* [suppress_fat](man/suppress_fat) - suppress fat signal in MRI volumes

## Brain Extraction

* [mincbeast](man/mincbeast) - BEaST brain extraction tool
* [beast_normalize](man/beast_normalize) - preprocess and normalize a MINC volume for BEaST brain extraction
* [beast_prepareADNIlib](man/beast_prepareADNIlib) - prepare an ADNI library for use with BEaST brain extraction

## Visual Tools

* [Display](man/Display) - interactive 3D visualization of MINC volumes and surface objects
* [mincview](man/mincview) - view a MINC file (primitive viewer)
* [register](man/register) - interactive volume display and point tagging program
* [ray_trace](man/ray_trace) - render 3D surface objects using ray tracing
* [xdisp](man/xdisp) - an image display utility for the X Window System
* [postf](man/postf) - a medical image display utility

## Noise Filtering

* [minc_anlm](man/minc_anlm) - adaptive non-local means denoising of MRI images
* [mincnlm](man/mincnlm) - non-local means denoising filter for MINC volumes

## Registration Scripts

* [mritoself](man/mritoself) - intra-subject registration of two volumetric data sets
* [mritotal](man/mritotal) - performs multi-scale fitting of a normal human brain to a standard model
* [minctracc](man/minctracc) - estimates the spatial transformation required to register two volumes together
* [check_scale](man/check_scale) - check and correct the Z-scale of a MNI linear transform
* [param2xfm](man/param2xfm) - create a MNI transform file from rotation, translation, scale, and shear parameters
* [xfm2param](man/xfm2param) - extract rotation, translation, scale, and shear parameters from a MNI transform file
* [xfmtool](man/xfmtool) - manipulate MNI transformation files
* [xfmdecomp](man/xfmdecomp) - decompose a .xfm transformation into rotation, translation, scale, and shear
* [xfmconcat](man/xfmconcat) - concatenate MNI transform files
* [xfminvert](man/xfminvert) - invert an MNI transform file
* [xfmflip](man/xfmflip) - flip an MNI transform file
* [cmpxfm](man/cmpxfm) - compare two MNI linear transform files element-by-element
* [xcorr_vol](man/xcorr_vol) - compute the normalized cross-correlation between two MINC volumes
* [volume_cog](man/volume_cog) - compute the intensity-weighted center of gravity of a MINC volume
* [mincbbox](man/mincbbox) - calculate the bounding box of non-zero data in a MINC volume

## Miscellaneous Tools

* [ecat2hdf5](man/ecat2hdf5) - convert ECAT format PET data to HDF5 format
* [xfmdecomp](man/xfmdecomp) - decompose a .xfm transformation into rotation, translation, scale, and shear
* [make_model](man/make_model) - create a model for use with mritotal
* [make_phantom](man/make_phantom) - create a synthetic MINC volume containing a geometric phantom object

## Registration

* [check_scale](man/check_scale) - check and correct the Z-scale of a MNI linear transform
* [cmpxfm](man/cmpxfm) - compare two MNI linear transform files element-by-element
* [mincchamfer](man/mincchamfer) - compute the chamfer distance transform of a MINC volume
* [minctracc](man/minctracc) - estimates the spatial transformation required to register two volumes together
* [param2xfm](man/param2xfm) - create a MNI transform file from rotation, translation, scale, and shear parameters
* [volume_cog](man/volume_cog) - compute the intensity-weighted center of gravity of a MINC volume
* [xfm2param](man/xfm2param) - extract rotation, translation, scale, and shear parameters from a MNI transform file
* [xfmtool](man/xfmtool) - manipulate MNI transformation files
* [xcorr_vol](man/xcorr_vol) - compute the normalized cross-correlation between two MINC volumes

## Statistical Analysis

* [glim_image](man/glim_image) - fit a generalized linear model to voxel intensities across MINC volumes

## Uncategorized

* [autocrop](man/autocrop) - tool for extracting and manipulating bounds of a MINC file
* [dcm2mnc](man/dcm2mnc) - convert sets of DICOM files to one or more MINC format files
* [ecattominc](man/ecattominc) - convert an ecat format file (version 6.x or 7.x) to a minc format file
* [invert_raw_image](man/invert_raw_image) - invert 2D image along either or both axes
* [minc_modify_header](man/minc_modify_header) - modify the attributes in the header of a minc file
* [mincaverage](man/mincaverage) - average minc files
* [mincbbox](man/mincbbox) - calculate the bounding box of non-zero data in a MINC volume
* [mincbeast](man/mincbeast) - BEaST brain extraction tool
* [mincblob](man/mincblob) - calculate blobs from minc deformation grids
* [mincblur](man/mincblur) - convolve an input volume with a Gaussian blurring kernel
* [minccalc](man/minccalc) - perform complex math operations on minc files
* [minccmp](man/minccmp) - compare one or more minc file using comparator operators
* [mincconcat](man/mincconcat) - concatenate minc files along a specific dimension
* [mincconvert](man/mincconvert) - convert between MINC 1 to MINC 2 format
* [minccopy](man/minccopy) - copy minc image values from one minc file to another
* [mincdiff](man/mincdiff) - report differences between minc files
* [mincdump](man/mincdump) - convert minc files to ASCII form (CDL)
* [mincedit](man/mincedit) - edit a MINC file header
* [mincexpand](man/mincexpand) - expands a compressed minc file, if necessary
* [mincextract](man/mincextract) - dump a hyperslab of MINC file data
* [mincgen](man/mincgen) - generate a MINC file from a CDL file
* [mincheader](man/mincheader) - prints out complete header information for a minc file
* [mincinfo](man/mincinfo) - print out specified information about a minc file
* [minclookup](man/minclookup) - perform lookup table conversions on minc files
* [mincmakescalar](man/mincmakescalar) - convert vector minc files to scalar
* [mincmakevector](man/mincmakevector) - convert a list of scalar minc files into one vector file
* [mincmath](man/mincmath) - perform simple math operations on minc files
* [mincresample](man/mincresample) - resamples a minc file along new spatial dimensions
* [mincreshape](man/mincreshape) - cuts a hyperslab out of a minc file (with dimension re-ordering)
* [mincsample](man/mincsample) - generate samplings from minc files
* [mincstats](man/mincstats) - calculate simple statistics across voxels of a minc file
* [minctoecat](man/minctoecat) - convert a minc format file to an Ecat7 format file
* [minctoraw](man/minctoraw) - copy data from a MINC file
* [mincview](man/mincview) - view a MINC file
* [mincwindow](man/mincwindow) - limit voxel values to a given range
* [mnc2nii](man/mnc2nii) - convert a MINC format file to a NIfTI-1 or Analyze format file
* [mrisim](man/mrisim) - (no description available)
* [mritoself](man/mritoself) - intra-subject registration of two volumetric data sets
* [mritotal](man/mritotal) - performs multi-scale fitting of a normal human brain to a standard model
* [nii2mnc](man/nii2mnc) - convert a NIfTI-1 or Analyze 7.5 format file to a MINC format file
* [postf](man/postf) - a medical image display utility
* [rawtominc](man/rawtominc) - converts a stream of binary image data to a minc format file
* [register](man/register) - interactive volume display and point tagging program
* [upet2mnc](man/upet2mnc) - convert a Concorde microPET format file to a MINC format file
* [vff2mnc](man/vff2mnc) - convert set of vff file(s) to one 3D MINC2.0 format file
* [voxeltoworld](man/voxeltoworld) - convert voxel coordinates to world coordinates
* [worldtovoxel](man/worldtovoxel) - convert world coordinates to voxel coordinates
* [xfm2def](man/xfm2def) - convert a MNI transform file to a deformation volume
* [xfmconcat](man/xfmconcat) - concatenate MNI transform files
* [xfmflip](man/xfmflip) - flip an MNI transform file
* [xfminvert](man/xfminvert) - invert an MNI transform file
* [xdisp](man/xdisp) - an image display utility for the X Window System
