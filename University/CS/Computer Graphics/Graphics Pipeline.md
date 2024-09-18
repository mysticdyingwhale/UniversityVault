# Graphics Pipeline
#cs 

GPU:
- Reads each selected vertex out of the vertex array
- Runs it through **vertex shader**
- Connects the projected vertices to form triangles
Rasterizer:
- Takes each triangle, clips it, and discards parts outside of screen
- Breaks remaining visible parts into pixel-sized fragments
Fragment Shader:
- Takes fragments, receiving various values output by vertex shader and interpolated by the rasterizer as inputs
- Outputs colour and depth values that then get drawn into frame buffer
Framebuffer:
- Final destination for the rendering job's output


### Object-Order Rendering

- Draw objects one-by-one onto screen
	- Find each pixel objects have effects on
	- Rasterize
	- Rasterization-based systems are also called scanline renderers
- Any graphics system has one or more types of primitive object that it can handle directly (triangles, etc..)
- More complex objects are then converted into these primitives


Sequence of Operations for Graphics Pipeline:

- Starts with objects
- ...
- Ends by pixel update in image

## Rasterization