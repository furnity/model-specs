# Creating simple spaces from 2D blueprints

This guide assumes you have a 2D blueprint of a space.


### Convert to PNG

The blueprint needs to be imported into Blender as a texture. Prefer PNG. 

#### PDF Source

If you have a PDF it needs to be converted to PNG. You can do this with any software you like. For WSL/Ubuntu [GraphicsMagick](http://www.graphicsmagick.org/) is recommended.

##### Installing GraphicsMagick

In Ubuntu the command `apt` can install it.

```bash
sudo apt install graphicsmagick
```

Convert the PDF with the following command.

```bash
gm convert -density 300 [inputfile].pdf [outputfile].png
```

### Set tone curve

The blueprint background should not be white, but grey, close to `#606060`. You can use most image editing software to accomplish this in several ways. The simplest way is using Tone Curve and invert the curve. Example from the free softare [FireAlpaca](https://firealpaca.com/) below.

<img width="1124" height="658" alt="image" src="https://github.com/user-attachments/assets/1f380d74-0314-46bc-a0ee-b8489ee965c7" />

Before

<img width="1127" height="662" alt="image" src="https://github.com/user-attachments/assets/7d3683d8-28a9-43e5-b5a2-fd9b6a2ea021" />

After





### Import and Scale blueprint

Start Blender and create a new file.

<img width="935" height="620" alt="image" src="https://github.com/user-attachments/assets/fc1b68d2-71b9-45a2-b31b-2f5e7d5ed11e" />

Import image as Mesh Plane


<img width="773" height="553" alt="image" src="https://github.com/user-attachments/assets/26819755-c977-4f62-8ca4-70acc1728286" />

Find Scale on drawing and measure it. Ensure you are in top-down orthogonal view otherwise the measurement will be inaccurate.


<img width="837" height="250" alt="image" src="https://github.com/user-attachments/assets/97d627aa-983b-4c30-90c4-bab5da35db17" />

Scale the blueprint by dividing `1` with the measured number. In the case above `1/0.038744`.


<img width="836" height="685" alt="image" src="https://github.com/user-attachments/assets/b29e73c6-91cd-4405-99cb-8b22bc23df8f" />

Ensure the scale is correct by comparing to the grid.


### Create perimeter walls 

<img width="702" height="419" alt="image" src="https://github.com/user-attachments/assets/1940e085-64ca-46e8-b447-08f61fdf6d26" />

Create a new Path for the perimeter wall. Name it something identifiable, like "Floor 1 Perimeter Wall Path".

Select the Path and go into **Edit Mode** with `Tab`.

<img width="1562" height="892" alt="image" src="https://github.com/user-attachments/assets/b82134a3-9417-41f1-9a95-71aeafcd080a" />


### Create inner walls

...

### Create windows and doorways

...

### Block off occupied spaces

For each area 

### Add details

* Add kitchens where kitchens are designated.



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
