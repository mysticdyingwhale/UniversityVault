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


## Rasterization