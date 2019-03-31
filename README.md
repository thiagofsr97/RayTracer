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

# Perspective Camera Implementation - Activity 3

The project is about the implementation of the perspective camera (pinhole), complementing the 
Ray Tracer project forked at https://github.com/capagot/RT-Template

## Algorithm Used 

The implementation of the perspective camera was made based on the content presented on the website https://www.scratchapixel.com/lessons/3d-basic-rendering/ray-tracing-generating-camera-rays/generating-camera-rays.
The resulting code of the camera implementation is the given below:

```cpp

#include "perspective_camera.h"

const float PerspectiveCamera::kDegreesToRadians_ = static_cast< float >( M_PI ) / 180.0f;

PerspectiveCamera::PerspectiveCamera( void )
{ }

PerspectiveCamera::PerspectiveCamera( 
                                      const glm::ivec2 &resolution,
                                      const glm::vec3 &position,
                                      const glm::vec3 &up_vector,
                                      const glm::vec3 &look_at,
                                      const float min_x,
                                      const float max_x,
                                      const float min_y,
                                      const float max_y,
                                      float aspect,
                                      float fov_degrees ) :
        Camera::Camera{ resolution,
                        position,
                        up_vector,
                        look_at },
        min_x_{ min_x },
        max_x_{ max_x },
        min_y_{ min_y },
        max_y_{ max_y },
        aspect_{ aspect },
        fov_degrees_{ fov_degrees }
{ }

Ray PerspectiveCamera::getWorldSpaceRay( const glm::vec2 &pixel_coord ) const
{
    float witdh  = max_x_ - min_x_;
    float height = max_y_ - min_y_;

    float x_value = ((witdh * pixel_coord[0]/static_cast< float >(resolution_[0])) - (witdh/2) ) * aspect_ * tan(fov_degrees_ * 0.5f * PerspectiveCamera::kDegreesToRadians_);
    float y_value = ((height/2) -  (height*(pixel_coord[1]/static_cast< float >(resolution_[1])))) * tan(fov_degrees_ * 0.5f * PerspectiveCamera::kDegreesToRadians_);
    
    glm::vec3 ray_local_dir{ x_value , y_value , -1.0f};

    return Ray{ position_, glm::normalize( onb_.getBasisMatrix() * ray_local_dir ) };
}

```

## Model Samples 

Below are some of model samples that were loaded and rendered using the Ray Tracer with Perspective Camera.

- **All the models are in the format .blend (Blender), using triangular faces and standard coordinate system.**

- **All the images presents a resolution of 512x512.**

### Model 1 - Monkeys Tree

- Time to load and render model: 52.6757 seconds.
- Number of primitives used: 10637.
- Image description: 11 monkey heads of the same size located in different positions so as to form a design similar to a tree, presenting in its constitution random colors.

![Alt text](Trabalho3/models/model2/output_image.jpg?raw=true "Title")

### Model 2 - The four monkeys

- Time to load and render model: 25.7383 seconds.
- Number of primitives used: 3868.
- Image description: 4 monkey heads of the same size located in different positions, presenting in their constitution random colors, demonstrating well the concept of camera perspective.

![Alt text](Trabalho3/models/model3/output_image.jpg?raw=true "Title")

### Model 3 - The 10 Colored Men

- Time to load and render model: 105.276 seconds.
- Number of primitives used: 19680.
- Image description: set of several models of a human being positioned in several different positions, all being the same size.

![Alt text](Trabalho3/models/model4/output_image.jpg?raw=true "Title")

# Pathtracer Implementation - Activity 4

The project is about the implementation of the path trace algorithm. Before the implementation of the algorithm it was necessary some changes like: to add material to the primitives and a certain quandity of light emission.

## Implementation

The principle for the implementation of path tracing is based on the Monte Carlo integration method, where from several samples that are randomly launched the algorithm integrates all the illuminance received at a single point on the surface of an object. As this is done for the m points of n objects in the scene, then a large number of samples per pixel is required to achieve more realistic and low noise results. To calculate the ray reflection angle a c ++ library was used to distribute the random numbers uniformly.

- **All the images presents a resolution of 512x512.**

### Render 1

- 100 samples per pixel with depth 5
- Time to load and render model: 83.407 seconds.
- Number of primitives used: 7.
- Image description: 2 triangles blue and 5 spheres of color, red, yellow, white, purple and the fifth is the light source that was positioned above the scene.

![Alt text](Trabalho4/Render1.png?raw=true "Title")

### Render 2

- 500 samples per pixel with depth 5
- Time to load and render model: 409.19 seconds.
- Number of primitives used: 7.
- Image description: 2 triangles blue and 5 spheres of color, red, yellow, white, purple and the fifth is the light source that was positioned above the scene.

![Alt text](Trabalho4/Render2.png?raw=true "Title")

### Render 3

- 1000 samples per pixel with depth 5
- Time to load and render model: 816.926 seconds.
- Number of primitives used: 7.
- Image description: 2 triangles blue and 5 spheres of color, red, yellow, white, purple and the fifth is the light source that was positioned above the scene.

![Alt text](Trabalho4/Render2.png?raw=true "Title")




























