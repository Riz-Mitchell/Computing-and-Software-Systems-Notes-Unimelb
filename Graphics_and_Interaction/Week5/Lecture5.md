# Collision Detection

`Newton's Laws` don't exist in unity by default

Collision detection is all about what happens when objects hit each other / intersect, in the virtual environment.

Typically, you want to give model some physical properties. This will probably prevent objects from just going straight through each other

## 2 High-level Detection Approaches

### Continuous (a priori)

Shoot bullet and draw a ray in the direction of movement and calculate the object that will be hit.

> This doesn't always go to plan as an object could move through the path in the mean time

# Discrete (a posteriori)

Shoot bullet and every frame check for a collision

> Object could move through objects in between the frames and it will not know it was supposed to collide