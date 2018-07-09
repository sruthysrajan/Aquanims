# Aquanims
Animated transitions for statistical data graphics.

### Abstract
"Aquanims" is new design metaphors for animated transitions that preserve displayed areas during the
transformation. Animated transitions are used to facilitate understanding of graphical transformations between different
visualizations. As liquids are incompressible fluids, we use a hydraulic metaphor to convey the sense of area preservation during animated transitions. In aquanims, graphical objects can change shape, position, color and even connectedness but not displayed area, as for a liquid contained in a transparent vessel or transferred between such vessels communicating through hidden pipes.

### Design concept
In our physical analogy we consider that the equivalent to a bar or a tile is actually the liquid which takes the form of its graphical container. By so doing we transfer the semantic of the area of the graphical container to the one of the graphical fluid it contains. So we can change the shape of a set of containers, move the liquid from one container to another, or even let it be shared between several containers without changing its total volume. Thus the two fundamental principles underlying aquanims are:

- **First principle:** the liquid encodes the data. Data are mapped to the fluid content rather than to its container.

- **Second principle:** the liquid volume is constant, so is its area in the graphical representation. Pipes and containers can change the liquid’s shape but cannot change its total area.

As a main design guiding principle, aquanims should be designed so as to emphasize the hydraulic metaphor evoking liquid-coded data (First principle), in order to increase the perception of area invariance (Second principle).

As a consequence, because the container is not encoding data directly, the liquid itself must bear some identification mark. We use the color channel for this sake to fill the rectangles or color its edges.

Some of the design concepts we have used in implementing Aquanims are: 
- **Isolated container: empty/fill**
A container can be filled or emptied. We represent the container by an empty rectangle and the liquid by a partial filling of it as a smaller rectangle having 3 sides shared with the container.

- **Isolated container: shift**
The liquid in a container can be shifted, i.e. translated along the container axis, so the rectangle representing the liquid is translated while the container remains fixed in the underlying space.

- **Communicating segments: shift**
In a single container, two or more segments of the controlled liquid separated by segments of other liquids can be connected by hidden pipes following the same rules as communicating containers. The liquid transferred in the pipe changes the local segment area but preserves global area. The other liquids are shifted along the container.

### Implementation
![example](https://user-images.githubusercontent.com/40992880/42441215-6be88c96-8370-11e8-8795-3597b06af10e.JPG)

As a first step, we add the bounding box of both initial and final state rectangles and the side which is controlled (middle vertical line, red color in the second row) is interpolated linearly between initial (t'<sub>0</sub>) and final states (t'<sub>1</sub>). Then we remove these elements to render the final state. 

The underneath model (second row) shows that two sides of the inital rectangle are fixed (black dots), one is directly controlled (red line) and one is moved (green line) under the preserving-area constraint. The corners of the reshaped rectangle follow hyperbolic trajectories (light blue dashed lines). 

The bottom row shows that linear interpolation (purple box and dashed line) between initial and final positions of the vertices does not preserve area.

### Dependancy

Already included:
- d3.js http://d3js.org/ Copyright 2017, Michael Bostock Released under BSD licenses.
