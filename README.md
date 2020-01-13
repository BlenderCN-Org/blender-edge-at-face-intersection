# Blender Introduce an Edge at Face Intersection

[**WEB**](https://tomashubelbauer.github.io/blender-edge-at-face-intersection)

In this repository I try to figure out how to introduce an edge where two faces intersect in Blender 2.8.

- Remove the default cube (X > Enter)
- Add a new plane (Shift + A > Mesh > Plane)
- Zoom to focus on the plane (/)
- Add another plane
- Rotate it by 90 degrees on any axis so that the planes are no longer coplanar and share an intersection edge
- Join the two planes together into one mesh (Ctrl + J)
- Enter edit mode (Tab) and choose edge select mode (2)
- Notice how there is no edge where the two faces/planes intersect
- [ ] Figure out how to introduce an edge there without the loop cut hack
- [ ] Figure out how to handle the same if the planes were different sizes or shifted against one another
  - The edge might not reach the edges of the larger faces on either side (one plane is smaller than the other and centered)
  - The edge reaches one edge of the larger face (one plane is smaller and shifted so that the intersection reaches or exceeds the edge of the larger plane)
  - The edge reaches both edges of the other face (they are same size or one is larger than the other, so the first point but from the other perspective)

https://blender.stackexchange.com/q/137765/68286

## Loop Cut

A hacky way of solving this specific scenario would be to use two loop cuts, one of each of the planes.
The share origin and loop cuts center within the face so the loop cut introduced edge would coincide with the intersection edge.
This will not work if the faces do not share the same origin thus causing a coincidence where the loop cut (50 % of the size)
works out to be where the actual intersection also is.

## Boolean Modifier

Using a boolean modifier kinda works. Select the first plane and go to Modifies in the Properties Panel.

 - [ ] Find out if there is a shortcut for entering and focusing the Properties Panel.

Go to Modifiers > Add Modifier > Boolean. Click the picker next to the Object field and select the other plane.
Do the same for the other plane. Join the planes together getting a single mesh with four faces.
This will not work if the faces' edge loops do not themselves intersect.

## To-Do
