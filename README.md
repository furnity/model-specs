# Furnity Studio Model Specs
Specifications for 3D models compatible with the Furnity Studio Platform


## Articles

* Binary GLTF (.glb)
* Embedded textures
* Y is Up
* File size typically: 1-5 MB including textures

### Origins

All origins should be centered horizontally on the article footprint (the surface that touches floor). By default origin are set at bottom vertically.

Exceptions to vertical origin:
- Pendants: vertical top


## Interiors

### Interaction

In order for interiors to behave correctly, objects must be annotated with `furnity.behaviour` custom property. The following properties exist and can be combined with white space separation.

* `perimeter`
  Objects that enclose the interior like outer walls of a house or apartment.

* `floor`
  Objects that make up the lowest point of a space.

* `ceiling`
  Objects that make up the highest point of a space.

* `island`
  Objects that duck out of the way when they obscure camera.



### Orientation

Below are approximate guidelines

* Street side points towards X+
* Garden side points towards X-


### Checklist
- [ ] Create meshes
- [ ] Define behaviors
  - [ ] perimeter walls `furnity.behavior`: `perimeter wall`
  - [ ] interior islands `furnity.behavior`: `island`
  - [ ] interior floor `furnity.behavior`: `floor`
  - [ ] interior ceiling `furnity.behavior`: `ceiling`

- [ ] Create parent for each space (floor)
  - [ ] Set custom data `furnity.space`: `floor`
  - [ ] Set custom data `furnity.space.id`: [unique string]
