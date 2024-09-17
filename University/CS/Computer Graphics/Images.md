# Images
#cs 

### Representing Images

#### Raster Graphics
- Rectangular array of small, light-emitting pixels
	- Mixed intensity of RGB channels for colours

#### Raster Image
- A 2D array that stores pixel values for each pixel
- Displays do not have to have the same number of pixels as the image
	- Image pixels $\neq$ display pixels

#### Vector Images
- Store description of shapes
	- Areas of color bounded by lines and curves
	- No reference to a particular grid
	- Store instructions to display image
- Resolution Independent
- Good for high-res devices
- Have to be **rasterized** before display (converted to pixel array)
- Used in text, diagrams, etc..

#### Pixels
- Subpixels 
	- Red, Green, Blue
- Each emit light of different colours
- Eye cannot separate subpixels
	- Perceives a mix of RGB

#### Raster Displays (Bitmap, Pixmap)
- Bitmap:
	- Intensity for each pixel depends on the size of frame buffer
		- B&W System
		- One bit per pixel
- Pixmap
	- Multiple bits per pixel, can display grayscale or colour 


#### Resolution
- Dimensions of pixel grid

#### Pixels in 2D Space
- Pair $(i,j)$ indicates column ($i$) and row ($j$)
- Bottom left $(0,0)$
- Top right $(n_{x-1}, n_{y-1})$, for an $n_x \times n_y$  display


#### Pixel Coverage
- Fraction of pixel covered by foreground layer
- Namely, $\propto$
- Formula:
	- Foreground colour: $c_f$, background colour: $c_b$
	- $c = \propto c_f + (1 - \propto)c_b$

