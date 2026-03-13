---
section: 1
title: Display
author: David MacDonald
group: Visual Tools
---
# Display

interactive 3D visualization of MINC volumes and surface objects

`Display [options] <volume1.mnc> [volume2.mnc] [surface.obj] ...`

## DESCRIPTION

**Display** is an interactive 3D visualization tool for viewing MINC volumes and
BIC-format surface objects. It provides three orthogonal slice views (sagittal,
coronal, and axial) of volumetric data, with the ability to overlay polygon-based
surface objects on the slices or in a 3D rendering window.

Display supports simultaneous loading of multiple volumes and surfaces. Users can
navigate through slices, adjust colour maps and intensity windows, paint voxel
labels for manual segmentation, and measure distances and angles interactively.
Surface objects can be rendered with adjustable transparency, lighting, and colour.

The tool is fully interactive and driven by mouse and keyboard commands once
launched. All input files are specified as positional arguments on the command line.
MINC volume files (`.mnc`) are loaded as volumetric data, while BIC object files
(`.obj`) are loaded as 3D surface meshes.

Key features include:

- Three orthogonal slice views with crosshair navigation
- 3D surface rendering with lighting and transparency controls
- Volume overlay and blending of multiple datasets
- Interactive label painting and segmentation
- Colour coding lookup tables and intensity windowing
- Tag point placement and editing
- Surface cutting and clipping planes

## OPTIONS

Display is an interactive graphical application. Files to view are passed as
positional command-line arguments. There are no command-line option flags; all
interaction occurs through the graphical user interface using keyboard shortcuts
and mouse controls.

`<volume.mnc>`
:   One or more MINC volume files to display as orthogonal slices.

`<surface.obj>`
:   One or more BIC object files to overlay as 3D surfaces.

## EXAMPLES

Display a single MINC volume:

    Display brain.mnc

Display a volume with a surface overlay:

    Display brain.mnc cortex.obj

Display two volumes and a surface:

    Display t1.mnc labels.mnc white_surface.obj

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre, Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &copy; 1993-2000 by David MacDonald

## SEE ALSO

[register](register) [ray_trace](ray_trace)
