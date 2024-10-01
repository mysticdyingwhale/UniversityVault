# Raytracing
#cs 

Raytracing is a technique for generating an image by tracing the path of light through pixels in an image plane and simulating the effects of its encounters with virtual objects.



| Projective                                          | Raytracing                                      |
| --------------------------------------------------- | ----------------------------------------------- |
| Project 3D triangles to 2D triangles on screen      | Compute ray from viewpoint through pixel center |
| Project vertices                                    | Find first object hit by ray                    |
| Shade 2D triangles                                  | Determine intersection point                    |
| OpenGL, DirectX                                     | Calculate pixel shading                         |
| Fast, good for real-time applications               | Produces high degree of realism                 |
| 2 or more triangles can project onto the same pixel |                                                 |
| Object-order rendering                              | Image-order rendering                           |


OOR: For each object, find and update all pixels it influences.

IOR: For each pixel, find all objects that 