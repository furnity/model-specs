# Creating simple spaces from 2D blueprints

This guide assumes you have a 2D blueprint of a space.


## Quick Reference

### Colors

* Perimeter wall: `#D4CFC0`
* Inner wall: `#F4EFEC`
* Block offs: `#7A7A7A`
* Blueprint base: `#606060`

### Measurements

* Perimeter wall height: `2.8`
* Inner wall height: `2.5`


## Instructions

### Convert to PNG

The blueprint needs to be imported into Blender as a texture. Prefer PNG. 

#### PDF Source

If you have a PDF it needs to be converted to PNG. You can do this with any software you like. For WSL/Ubuntu [GraphicsMagick](http://www.graphicsmagick.org/) is recommended. For Mac/Windows [Affinity](https://www.affinity.studio/download) is recommended. 

##### Installing GraphicsMagick

In Ubuntu the command `apt` can install it.

```bash
sudo apt install graphicsmagick
```

Convert the PDF with the following command.

```bash
gm convert -density 300 -rotate 0 [inputfile].pdf [outputfile].png
```

Example below. Notice quotes `"` and page notation `[0]`. If the PDF have multiple pages you can specify them inside the brackets starting from 0. So if you want page 3 in a PDF the filename should be specified as `"My blueprint.pdf""[2]"`. You can constrol the resolution of the output file with the `-density 600` switch. Since most PDFs are based on paper sizes that needs to be converted to pixel resolution for the PNG file. On case the PDF needs to be rotated you can control that with the `-rotate 0` command. Replace `0` with the degrees you want to rotate, usually either `0`, `90`, `180`, or `270`.
```
gm convert -density 600 -rotate 0 "Ritning Furnity Torpagatan 32.pdf""[0]" "Torpagatan 32.png"
```

### Set tone curve

The blueprint background should not be white, but grey, close to `#606060`. You can use most image editing software to accomplish this in several ways. The simplest way is using Curves adjustments and invert the curve. Below this is shown in Affinity.

<img width="2529" height="1550" alt="image" src="https://github.com/user-attachments/assets/0df969e4-de5b-445b-bfe7-53738b70e1e6" />






### Import and Scale blueprint

Start Blender and create a new file.

<img width="935" height="620" alt="image" src="https://github.com/user-attachments/assets/fc1b68d2-71b9-45a2-b31b-2f5e7d5ed11e" />

Import image as Mesh Plane


<img width="1722" height="1073" alt="image" src="https://github.com/user-attachments/assets/296b9899-a283-4190-a0d7-e3c46050660a" />

Change Viewport Shading to Material Preview to see the texture.


<img width="1774" height="1073" alt="image" src="https://github.com/user-attachments/assets/0001263f-c346-4b2d-ab3a-b0209ea36959" />

Rotate the Mesh Plane so that the texture faces upwards. In this case the X rotation was changed from `90` to `0`.


<img width="773" height="553" alt="image" src="https://github.com/user-attachments/assets/26819755-c977-4f62-8ca4-70acc1728286" />

Find Scale on drawing and measure it. Ensure you are in top-down orthogonal view otherwise the measurement will be inaccurate.


<img width="837" height="250" alt="image" src="https://github.com/user-attachments/assets/97d627aa-983b-4c30-90c4-bab5da35db17" />

Scale the blueprint by dividing `1` with the measured number. In the case above `1/0.038744`. The scale can be changed at any time all the way to export, so don't stress too much about getting it perfect.


<img width="836" height="685" alt="image" src="https://github.com/user-attachments/assets/b29e73c6-91cd-4405-99cb-8b22bc23df8f" />

Ensure the scale is correct by comparing to the grid.


### Outline petimeter walls

Start by creating the path for the perimeter wall (outside walls). We separate outside and inner walls to make it easier to change colors and thickness in case we need that.

<img width="702" height="419" alt="image" src="https://github.com/user-attachments/assets/1940e085-64ca-46e8-b447-08f61fdf6d26" />

Create a new Path for the perimeter wall. Name it something identifiable, like "Floor 1 Perimeter Wall Path".


<img width="1438" height="805" alt="image" src="https://github.com/user-attachments/assets/fccabafb-a134-4074-9fac-d5a0b2ab7a66" />

Select the Path and go into **Edit Mode** with `Tab`. You can now start adding points using `Ctrl + Right Mouse Button`. 


<img width="806" height="673" alt="image" src="https://github.com/user-attachments/assets/c76cc616-a4bd-4813-93e4-b08efcf70887" />

Per default the path will be a bezier path which means it will curve. Correct this by making sure you are in **Edit Mode**, having all points selected (`A`), and setting the Spine Type to Poly with the Context Menu.


<img width="1722" height="1073" alt="image" src="https://github.com/user-attachments/assets/86edfa6b-5fcf-43ca-b801-3c91c955490b" />

When the building perimeter is surrounded, you can configure the path to close it automatically by checking the `Cyclic U` option.


### Create perimeter wall profile

Our perimeter wall is only a line now. In this step we are going to make the wall solid by creating another path to act as the perimeter wall profile that will follow the outer wall.

<img width="1722" height="1074" alt="image" src="https://github.com/user-attachments/assets/09f5122e-f78f-4e7b-8af5-e5ab08870030" />

Create another new Path, set Spline type to Poly, and name it similar to "Perimeter Wall Profile". Then make it into a shape that is approximately 2.5 meters tall, and 0.2 meters wide. Also set this to `Cyclic U`.


<img width="1795" height="1073" alt="image" src="https://github.com/user-attachments/assets/32edcd2f-4c0f-441f-bc1c-a8930779089f" />

Select the Perimeter wall path and set the Perimeter wall profile as Bevel Object. You should now see the perimeter wall as a solid.


<img width="1722" height="1074" alt="image" src="https://github.com/user-attachments/assets/1c511791-e4aa-4f40-ac81-8c8acc07471e" />

Depending how the scene is set up, the wall may be lying down. This is because the Bevel object is applied using the profile path origin point as "attachment point" for the perimeter path. This can be fixed by going into Edit mode and move the points. In this case the points were rotated and moved so that the base of the profile was on the center of the origin point.


<img width="1722" height="1073" alt="image" src="https://github.com/user-attachments/assets/d23f7c41-bd52-41fa-9b56-3a16f10294e3" />

Be careful to keep all points on the Z plane so that all points are on Z = 0.


### Create inner walls

Creating the inner walls is done in the same manner as perimeter walls. The only difference in that you don't want to mark this path as `Cyclic U` as you want many standalone walls instead of one that circles the building. 

Repeat the steps in the previous step.

* Add new Path
* Name it something recognizable (`Floor 1 Inner Wall Path`)
* Set Spline type to `Poly`
* Set out new points using `Ctrl + Right Mouse`.
* Make a new segment by unselecting using `Left Mouse` and then start new with `Ctrl + Right Mouse` again.

<img width="1876" height="1246" alt="image" src="https://github.com/user-attachments/assets/f25da9f8-5368-428b-8c5c-351f27acbfa2" />

To better see which walls you have completed - set a wall profile early and assign it a vibrant material.


<img width="2038" height="1156" alt="image" src="https://github.com/user-attachments/assets/be30eaf2-5fe6-4e9e-920b-7660ab67c4c6" />

A few minutes later - all walls have been set out!


<img width="2037" height="1156" alt="image" src="https://github.com/user-attachments/assets/8f33c022-969f-4bec-846f-4e3227bf2091" />

If the walls looks smooth ensure Shading is set to Flat in `Object Mode`.





...

### Create windows and doorways

Windows and doorways are created by placing cube meshes where we want holes for windows and doors. These meshes will later be used to cut out holes in walls using the boolean modifier.

#### Windows

<img width="635" height="909" alt="image" src="https://github.com/user-attachments/assets/08bd432a-4b97-4122-b6e0-7b9191d999c8" />

Create a new collection by right clicking in the [Outliner](https://docs.blender.org/manual/en/latest/editors/outliner/introduction.html). Name it `Gaps` of something descriptive.


<img width="1756" height="1173" alt="image" src="https://github.com/user-attachments/assets/a80a310f-b164-45bc-9e58-46f2474fbadc" />

Create a cube to represent a window. Name it something descriptive like `Window.000` and move it into the new collection by dragging it into the collection in the Outliner. Set the height and placement from the ground if it is known. If it is unknown use 1.2m height and 1.4 meter above ground with a centered origin. A centered origin is default for newly created cubes.


<img width="1756" height="1174" alt="image" src="https://github.com/user-attachments/assets/6b198ea9-a867-447b-b9a8-e5c98b59cf3e" />

Set width according to blueprint. The depth must be thicker than the wall. A common practice is to use the same depth as width.


<img width="1756" height="1174" alt="image" src="https://github.com/user-attachments/assets/1644583d-e25d-42b7-a3b4-eb58a6380b04" />

Ensure you are in orthographic camera mode. Then duplicate the window mesh **as reference** by pressing `Alt + D` and move it to the next window on the blueprint. Repeat for every window in the blueprint. Adjust width if necessary. You can select multiple window meshes at once and duplicate and move.


#### Doorways

Doorways are created in the same manner but uses a height of approximately 2.1 meters and stretches all the way from Z=0 (the ground). 

Follow the same steps:

* Create Mesh and name it something descriptive like `Doorway.001`.
* Set height, width, depth and position from ground.
* Duplicate to position a mesh over each door in blueprint.


<img width="1756" height="1174" alt="image" src="https://github.com/user-attachments/assets/804186e2-8f31-429c-844d-50374a61e1b4" />

When done it should look similar to the screenshot.


#### Cutting out holes

In order to use a boolean modifier the walls must be converted from path into mesh. 


<img width="1992" height="1173" alt="image" src="https://github.com/user-attachments/assets/af5da379-cbb9-41a9-99f7-ef0c678c2f01" />

Since this is a destructive operation, it is a good idea to make a copy of the wall before with `Shift + D`. If it was named something with path, the copy can be named something with mesh; for example `Floor 1 Perimeter Wall Path` > `Floor 1 Perimeter Wall Mesh`. Hide the path after the copy has been made.


<img width="1992" height="1173" alt="image" src="https://github.com/user-attachments/assets/46240da9-2890-486e-85fe-6cc3d054a014" />

Now convert the object named mesh into a mesh. This can be done by right clicking the wall curves and selecting `Convert To > Mesh`. The green icon that can be seen under the object in the outliner should change from a path icon (curve) to a mesh icon (triangle).


<img width="1992" height="1173" alt="image" src="https://github.com/user-attachments/assets/7afe3184-1e58-475e-bae7-ef1a77b9c30e" />

Add the boolean modifier to the mesh.


<img width="1992" height="1173" alt="image" src="https://github.com/user-attachments/assets/5d1b15eb-4862-4d9c-b155-9a2e10d122b5" />

Set operand type to `Collection` and select the collection with windows and doorways in.


<img width="1992" height="1173" alt="image" src="https://github.com/user-attachments/assets/8ff2dec3-faa7-4e6b-9d5d-94c1437a89e2" />

Hide the Gaps collection by clicking the eye in the outliner to show the door and window holes.


<img width="1992" height="1174" alt="image" src="https://github.com/user-attachments/assets/19a6a1b2-6478-4d3f-b431-f9e9adf90148" />

Repeat the exact same steps for inner walls.



...

### Block off occupied spaces

Everything that should be restricted from having items placed on it, should be blocked off by a cuboid mesh or what is most suitable.

<img width="787" height="747" alt="image" src="https://github.com/user-attachments/assets/e3979a65-7c35-4b5f-bb5d-0c3b0690d16d" />

Material: Color `#7A7A7A` - Alpha `0.5`


### Add details

* Add kitchens where kitchens are designated.


### Add Areas

An area is a mesh that represents a volume or surface in an interior. It is used for Furnity Studio to understand where an item is. This is in order to create an index of items per volume or surface, like a room inside a house. 

An area can be any mesh with a `furntiy.area` as custom property. The custom property value will be used as the name of the area. For areas we use a material with color `#E72930` and `0.5` alpha. Areas will not be visible in Furnity Studio.


<img width="786" height="516" alt="image" src="https://github.com/user-attachments/assets/34d574d1-0427-46b3-b0f3-21a9211ab9eb" />

It is recommended to use planes for areas. Start by creating a collection called `Areas`, then create a plane and name it `Area.001`. Move it to the first room and assign it a custom property of type string on the object called `furnity.area`. Write the room name from the blueprint as the value. Repeat for every room by duplicating (`Alt + D`), move and scale it, and update the name for the new area.


<img width="2020" height="1173" alt="image" src="https://github.com/user-attachments/assets/cad055ea-7806-4c8e-954e-d6b25241197d" />

It is recommended to put all areas in their own collection and give the appropriate names.



### Define Spaces

There is one or more floors in each blueprint. Each floor is defined as a space in Blender to allow Furnity Studio to identify them.

#### Creating a floor space

* Choose an object to be the parent object for a space. Create a new empty object if needed.
* Add string custom property with name `furnity.space` and set it to `floor`.
* Add another string custom property with name `furnity.space.id` and set it to something random ([UUID](https://www.uuidgenerator.net/)).
* Set everything that belongs to this space as [child to the parent object](https://www.google.com/search?q=blender+set+object+to+child+of+parent).

<img width="329" height="168" alt="image" src="https://github.com/user-attachments/assets/6b4f3c81-81f2-4bac-9b13-14a045ce5559" />



### Export GLTF

### Upload to Furnity Studio Admin

Go to Worlds in admin and create a new world. Upload your GLTF and ensure all floors have been identified.


### Upload to Admin

* Go to [Furnity Studio Admin](https://admin.furnity.se/)
* Go to **Worlds** and create a new world.
* Name it something easily identifiable like project name followed by real world address; for example *Göteborgs stad - Prästvägen 18*.
* Upload the exported GLTF.
* Ensure spaces have been identified and save.
* Create a new Layout from the world and test in **Furnity Studio**.

### Share link with project
