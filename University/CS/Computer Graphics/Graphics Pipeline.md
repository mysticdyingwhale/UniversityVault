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

![[Pasted image 20241023114637.png||300]]

### Object-Order Rendering

- Draw objects one-by-one onto screen
	- Find each pixel objects have effects on
	- Rasterize
	- Rasterization-based systems are also called scanline renderers
- Any graphics system has one or more types of primitive object that it can handle directly (triangles, etc..)
- More complex objects are then converted into these primitives


Sequence of Operations for Graphics Pipeline:

- Starts with objects
- ... (graphics pipeline)
- Ends by pixel update in image

- Feed Pipeline with **geometric objects** 
	- From an interactive application 
	- From a scene description file
	- Described by a set of vertices
- Operate vertices in **vertex processing stage**
- Send created primitives to **rasterization stage**
- Break each primitive into fragments by **rasterizer**
- Process final fragments in **fragment processing stage**
- Combine fragments for each pixel in **fragment blending stage**

## Rasterization

![[Pasted image 20241023133315.png|400]]

Rasterizer outputs a set of fragments, one fragment for each pixel covered by a primitive

## Line Drawing

- Line drawing takes two endpoints:
	- y = mx+b
		- $0 = (\Delta y)x -  (\Delta x)y + (\Delta x)b$ 
- Naive Approach
	- Set every pixel traversed by line
	- Thick and chunky lines
- Uniform Sampling
	- Sample Line at N equal intervals
	- Set pixels closest to each sample
	- Choosing N is critical
		- Too big means chunky
		- Too small causes gaps
		- Best N considers slope
- Digital Difference Analyzer (DDA)
	- Guarantees thinnest lines with no gaps
	- Samples at equal intervals, considering line slope
		- For slopes <1 samples once for each column of pixel
		- For slopes >1 samples once for each row of pixel
- Bresenham's Algorithm
	- Utilizing integer math, assuming endpoints are at integers
- Midpoint Algorithm
	- Let the slope be in range (0,1)
	- Approximate point is $P = (x,y)$
	- Next point can be $E = (x+1,y)$
	- $NE = (x+1,y+1)$
	- Calculate Midpoint $M = (x+1, \frac{y+1} 2)$
	- ![[Pasted image 20241023135701.png|150]]

## Circle Drawing

- Polygonal Approximation
	- Use straight lines
	- Generate points at increment around circle
	- More lines, more accuracy, slow
- Midpoint Circle algorithm
	- Assume circle is at origin 
	- $y = \sqrt{R^2 - x^2}$ (for example when region of $x<y$) 
	- Set one pixel for each column that the section intersects 
	- Current pixel $(i,j)$ means next pixel is either $(i+1,j)$ or $(i+1, j-1)$


## Triangle Rasterization

- Use a midpoint algorithm to draw outline
- Fill interior pixels

## Gourand Interpolation

- Color interpolation
- Vertices have colors $c_0, c_1, c_2$
- Color at point in triangle with barycentric coordinates $(\alpha, \beta, \gamma)$ 
	- $c = \alpha c_0 + \beta c_1 + \gamma c_2$ 


## Culling

- Culling is throwing away invisible geometry to save processing time
	- Early rejection
	- Anything can be culled
		- Pixels
		- Triangles
		- etc..

Types of Culling:
- View volume culling (clipping)
	-  Removal of geometry that is outside the view volume
- Occlusion Culling
	- Something occluded by object in front of it
- Backface Culling
	- Culling of non-visable primatives
	- ![[Pasted image 20241023182019.png|300]]



### Types of Clipping


Line-rectangle Clipping
- Brute-force approach
Cohen-Sutherland Clipping
- Breaks down space into 9 sections, with the borders being the view rectangles sides extended infinitely
- Each region gets a 4-bit value
- ![[Pasted image 20241023183648.png]]
- Allows for:
	- Fast Acception: both endpoints in rectangle
	- Fast Rejection: two endpoints are in the same half-space
	- If neither, then subdivide segment at clip edge
Cyrus-Beck Clipping
- For convex polygons
- More efficient than Cohen-Sutherland since repetitive loops are avoided 
	- Avoids floating point division for testing
- Steps:
	- Compute intersections of the line segment with all clipping edges
	- Determine the clipped segment based on a series of simple comparisons (parameter values)
- Polygon Clipping
	- Useful to clip polygons against other polygons
		- Clip polygon against window for display
		- Shadow generation
		- anti-aliasing
	- Brute force approach uses line segment clipping
		- Introduces issues for concave polygons
		- API can either subdivide concave polygon into series of convex polygons or just not allow them
- Sutherland-Hodgeman Clipping
	- Can clip a general polygon against any convex poly by decomposing problem into a series of simpler, smaller, identical problems
		- Recursive, base case is clipping a poly against a single edge
- Three-Dimensional Clipping
	- Lines clipped against a right parallelepiped volume
	- Previous equations work, but subdivision would occur into 27 regions with 6 bits for each, rather than 9 regions with 4 bits for each.
	