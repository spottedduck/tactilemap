# tactilemap
Steps for creating a tactile map from scratch, inspired by Touch Mapper (https://touch-mapper.org). 

Fusion 360 and Illustrator can be substituted for your preferred software.

## Obtaining roads and building vectors for extrusion
- Option 1: no drawing or tracing required
  - Select monochrome template when creating new style in https://studio.mapbox.com
  - Turn off visibility for all layers
  - Pan and zoom to region of interest
  - To obtain the road layer
    - Toggle visibility of Walking, cycling, etc. (surface) > road-path
    - Change color to black
    - Take screenshot or select Print > export (limit 100 per month)
    - Do not pan or zoom the map
  - To obtain the building layer
Toggle visibility of Buildings (built) > building
Change fill color and stroke color to black
Take screenshot or select Print > export (limit 100 per month)
For each, open the image in Adobe Illustrator and run Image Trace 
Change stroke weight to adjust width of roads
Option 2: tracing or drawing a map you want to recreate
Paste an image of a map you would like to recreate in Illustrator. Ensure the map has North facing up. 
Trace the map roads and buildings, being sure to reduce detail/jagged edges for roads (we only need the general direction of the road). 
Use the smoothing tool to further smooth the roads. 
Create a new layer and create your symbols. 
Symbols for tactile maps should have enough space from other features and be distinct from each other. 
Do not use both square and circle symbols at the same time.
Some options are stars, 
Save the roads, buildings, and symbols layer each individually as .svg 
Hide all other layers > select your object > file > gather assets for export > select to export as .svg 
Symbols can be gathered and exported as 1 single asset. They can be individually moved and changed in the 3D modeling software. 

## Braille
Use https://www.touchsee.me/ to generate STL of bus stop labels in braille using U.S. English uncontracted. 
Remove the base (optional)
In Autodesk Fusion
Insert > insert mesh
Orient your view so that you see the label from either one of the sides 
Mesh > modify > plane cut 
Select the object > select cut plane by clicking on the axis line
Click and drag across the base > release > adjust the height of the cut using the arrows until base is removed and only braille dots remain.
Click OK
File > export > export as .STL

## Create 3D printable model in Autodesk Fusion 360
# Base
Orient your view so that the XY plane faces you

Solid > create sketch > select 2-point rectangle > select the XY plane 
Draw and create a square, recommended 17x17 cm or 20x20 cm which fits most 3D printers
Solid > extrude 1-5 mm, depending on how thick you want the base height to be
# Frame
Repeat base steps to create another cube that sits on top of the original base.
Create a sketch and select the XY plane of the cube you just created, which allows the sketch to sit on the surface of the cube.
Draw and create a square 1-2 mm smaller than the surface of the base.
Hide the base layer, so that only the second cube and sketch remain.
Extrude > select the square sketch > drag the arrow all the way through the cube to create a frame. 
# Map elements
Insert > insert SVG to open your symbols, roads, and buildings files and extrude them. Ensure they are oriented properly so they lay on the XY plane.
Extrude roads 2 mm
Extrude buildings 1 mm
Extrude symbols 3+ mm
For line symbols (roads, paths), use the Filet tool to round the edges.
Insert > insert mesh and open your Braille STL files.
Use solid > modify > align to align features to sit on top of the base layer.
Use move/copy and scale to adjust as needed.
Create a legend with the symbols and Braille labels. Ensure Braille complies with minimum standards. 
Create an orientation marker by placing a cube in the upper right corner of the frame

Export the map as .STL 
Slice the file in your preferred slicing program and print it. We used PLA filament.
