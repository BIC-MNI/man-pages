---
section: 1
title: create_box
author: David MacDonald
group: Surface and Geometry Tools
---
# create_box

create a rectangular box object file

`create_box filename.obj x1 x2 y1 y2 z1 z2`

## DESCRIPTION

`create_box` creates a rectangular box (cuboid) as a polygonal surface
object file. The box is defined by its world coordinate bounds along each
axis: x ranges from `x1` to `x2`, y ranges from `y1` to `y2`, and z
ranges from `z1` to `z2`.

## OPTIONS

This tool uses positional arguments only. There are no named options.

`filename.obj`
:   The output object file for the box.

`x1`
:   The minimum x coordinate of the box.

`x2`
:   The maximum x coordinate of the box.

`y1`
:   The minimum y coordinate of the box.

`y2`
:   The maximum y coordinate of the box.

`z1`
:   The minimum z coordinate of the box.

`z2`
:   The maximum z coordinate of the box.

## EXAMPLES

Create a box from (-50,-60,-40) to (50,70,60):

    create_box box.obj -50 50 -60 70 -40 60

## AUTHOR

David MacDonald - McConnell Brain Imaging Centre,
Montreal Neurological Institute, McGill University.

## COPYRIGHTS

Copyright &amp;copy; by David MacDonald

## SEE ALSO

[convex_hull](convex_hull) [Display](Display)
