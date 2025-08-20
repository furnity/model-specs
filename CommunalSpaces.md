# Creating simple spaces from 2D drawings

This guide assumes you have a 2D drawing of a space.

- [Convert to PNG](#convert-to-png)
  - [PDF Source](#pdf-source)
    - [Installing GraphicsMagick](#installing-graphicsmagick)
- [Import and Scale drawing](#import-and-scale-drawing)
- [Create perimeter walls](#create-perimeter-walls)

TOC created using [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)</small>


### Convert to PNG

The drawing needs to be imported into Blender as a texture. Prefer PNG. 

#### PDF Source

If you have a PDF it needs to be converted to PNG. You can do this with any software you like. For WSL/Ubuntu [GraphicsMagick](http://www.graphicsmagick.org/) is recommended.

##### Installing GraphicsMagick

```bash
sudo apt install graphicsmagick
```

```bash
gm convert -density 300 [inputfile].pdf [outputfile].png
```

### Import and Scale drawing

Start Blender and create a new file.

<img width="935" height="620" alt="image" src="https://github.com/user-attachments/assets/fc1b68d2-71b9-45a2-b31b-2f5e7d5ed11e" />

Import image as Mesh Plane


<img width="773" height="553" alt="image" src="https://github.com/user-attachments/assets/26819755-c977-4f62-8ca4-70acc1728286" />

Find Scale on drawing and measure it. Ensure you are in top-down orthogonal view otherwise the measurement will be inaccurate.


<img width="837" height="250" alt="image" src="https://github.com/user-attachments/assets/97d627aa-983b-4c30-90c4-bab5da35db17" />

Scale the drawing by dividing `1` with the measured number. In the case above `1/0.038744`.


<img width="836" height="685" alt="image" src="https://github.com/user-attachments/assets/b29e73c6-91cd-4405-99cb-8b22bc23df8f" />

Ensure the scale is correct by comparing to the grid.



### Create perimeter walls 

<img width="702" height="419" alt="image" src="https://github.com/user-attachments/assets/1940e085-64ca-46e8-b447-08f61fdf6d26" />

The first thing you want to do is create a new Path.



Select the Path and go into **Edit Mode** (`Tab`)




### Export GLTF

### Upload to Furnity Studio Admin

Go to Worlds in admin and create a new world. Upload your GLTF and ensure all floors have been identified.


### Share link with project
