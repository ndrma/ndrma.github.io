---
title: 'GIS_things'
date: 2024-04-08T19:08:03+01:00
draft: false
ShowReadingTime: true
ShowToc: true
summary: "lines of code / process for when trying to modify maps"
hipfile: hip/01_Spiral.hiplc

cover:
    image: /blog/images/QGIS_Cover.png
    alt: "Cover Photo"
    caption: ""
    relative: true
tags: ["GIS"]
categories: ["GIS", "snippets"]
---


### ⬛️  Stubborn, non matching layer interpolation
<br />
Alright, two layers (states) with different point count, different everything which resemble the state of an event days apart.
Interpolation and fruffy stuff that creates curves and other weird gradient shit doesn't work.  So:

1. Create two tables (decimal(real) number type), let's call them <u>"Midpoint_X"</u> , and <u>"Midpoint_Y"</u> those will be midpoint of the position between the coordinates of two points **WHERE IT CAN FIND THEM AND WHERE THEY MAKE SENSE OTHERWISE WILL NEED CORRECTIONS DOWN THE LINE**
2. then you need to average the distance from your layer to the other, code below:
    ```
    (x($geometry) + x(geometry(get_feature('OTHERLAYER', 'fid', $id)))) / 2
    (y($geometry) + y(geometry(get_feature('OTHERLAYER', 'fid', $id)))) / 2

    ```
that should be run to update the respective fields/tables.

3. Ok now we got points.
4. Those will require inspection to see where they have ended up, as well as corrections. For static features, they should not have ever been interpolated so they can just be deleted. For moving features such as the fire progression for example it is a matter of determining which points to keep and which to throw away. 
5. These points can be used for PointsToPaths. \[Optionally Clean them\]
6. Then split the paths.
7. Explode them as well. (usually just the explodey part is enough)
8. Happy times of manually cleaning weird geo (vertex tool + delete paths-lines)
9. If it doesn't commit the changes to the shapefile, export as
10. Dissolve (error logs here, will help with identifying the element and removing it before moving to the next step)
11. Test lines to polygons.
12. If the polygon shaped makes sense, save it and move on. If it doesn't geo probably needs more fixing.

<br />
<br />

### ⚫️  Attribute to geo
<br />

for things like the circles of range etc

1. create the attribute and assign values per point (if not available)
2. use `Geometry by expression` and having the layer with the info selected use:
    ```
    make_circle($geometry,r_VALUE*2,segments=36)
    ```
3.  if required split the geo into separate shapes for further use / port
    
<br />
<br />

### 🔶️ Add specific point
<br />
Ok, this is easy :P (quite handy for documenting events that the coordinates are known, point by point and are developing live instead of being an easily created/accessible csv, or for comparisons)

```
make_point("X", "Y")
```
x=lat, y=lon keep in mind the coordinate system

bonus line between points that share the same id:
```
make_line(make_point("X", "Y"), geometry(get_feature('LAYERNAME', 'fid', $id)))
```
this gets quite unstable when, you guessed it, have non-equal point count to match ids
<br />
<br />

### ◻️ Add the points' coordinates as an actual attribute (for further use)
<br />
Create the fields for x=lat, y=lon

Initially those will have to be for EPSG:4326.

```
x(transform($geometry, layer_property(@layer, 'crs'),'EPSG:4326'))
y(transform($geometry, layer_property(@layer, 'crs'),'EPSG:4326'))
```
update the respective field for each
<br />
<br />

### 🗨️ Display bubbles in GIS, html for mouseover display
<br />
This displays information based on the exported file + folder with material + material id in the csv on mouseover.

```
<span style="font-weight:bolder;">[%"desc"%]</span></br>
<img src="file:///[%@project_home%]/test/[%"img_id"%]" width="500" />
```

Also, specifying a type, which in my case I call (Cd) as well for further use, allows for per category labelling of the same layer. 

### 🏔️ GIS DEM Generation / fix for displacement map

* soon (TM)

Links:

- https://vvzen.github.io/houdini/dem
- https://somethingaboutmaps.wordpress.com/blender-relief-tutorial-getting-set-up/
- 

