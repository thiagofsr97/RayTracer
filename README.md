# RayTracer
Fernando Máximo Alves - 11500204

Thiago Filipe Soares da Rocha -  11502567

# Ray Triangle Intersection - Activity 2

## Image

The image generated with the render is a cat made of triangles and has exactly 9 triangles, with the colors varying according to the z coordinate of each vertex.

![Alt text](Trabalho2/Screenshotfrom2019-02-0900-28-51.png?raw=true "Title")
## Implementation

The technique used in rendering was the rayTracer that casts "rays" from an origin position following a direction d in the objects that are in the scene, to know if a ray struck an object an intersection routine is executed. In this present work the implemented intersection routines were to test the intersection between radius and triangle.

Two triangle intersection routines were implemented, the first one found in Peter Shirley's book and the second one in Moller and Trumbore which presented higher speed and lower cost of memory.

To demonstrate the difference between the two methods, a for was used to create 1000 cat images totaling a number of 9000 triangles and the runtime was calculated for each of the routines using the time.h library.

Using the routine found in Peter Shirley's book the render took a time of 22.82 seconds to render the scene. In the routine of Moller's article the render took a shorter time, which was a total of 18.9 seconds to render the scene.