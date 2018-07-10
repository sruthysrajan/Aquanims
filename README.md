# Aquanims
Area-preserving animated transitions based on a hydraulic metaphor.

## Abstract
"Aquanims" is a new design metaphor for animated transitions that preserve displayed areas during the transformation. Animated transitions are used to facilitate understanding of graphical transformations between different visualizations. As liquids are incompressible fluids, we use a hydraulic metaphor to convey the sense of area preservation during animated transitions. In aquanims, graphical objects can change shape, position, color and even connectedness but not displayed area, as for a liquid contained in a transparent vessel or transferred between such vessels communicating through hidden pipes.

## Design
In our physical analogy we consider that the equivalent to a bar or a tile is actually the liquid which takes the form of its graphical container. By doing so we transfer the semantic of the area of the graphical container to the one of the graphical fluid it contains. So we can change the shape of a set of containers, move the liquid from one container to another, or even let it be shared between several containers without changing its total volume. Thus the two fundamental principles underlying aquanims are:

- **First principle:** The liquid encodes the data. Data are mapped to the fluid content rather than to its container.

- **Second principle:** The liquid volume is constant, so is its area in the graphical representation. Pipes and containers can change the liquid’s shape but cannot change its total area.

As a main design guiding principle, aquanims should be designed so as to emphasize the hydraulic metaphor evoking liquid-coded data (First principle), in order to increase the perception of area invariance (Second principle).

As a consequence, because the container is not encoding data directly, the liquid itself must bear some identification mark. We use the color channel for this sake to fill the rectangles or color its edges.

Some of the design concepts we have used in implementing Aquanims are: 
- **Isolated container: empty/fill**
A container can be filled or emptied. We represent the container by an empty rectangle and the liquid by a partial filling of it as a smaller rectangle having 3 sides shared with the container.

- **Isolated container: shift**
The liquid in a container can be shifted, i.e. translated along the container axis, so the rectangle representing the liquid is translated while the container remains fixed in the underlying space.

- **Communicating segments: shift**
In a single container, two or more segments of the controlled liquid separated by segments of other liquids can be connected by hidden pipes following the same rules as communicating containers. The liquid transferred in the pipe changes the local segment area but preserves global area. The other liquids are shifted along the container.

## Implementation
![example2](https://user-images.githubusercontent.com/40992880/42474737-2a7e11de-83d1-11e8-809d-d09b04857277.JPG)

- **Initial state** In this step, the containers for the initial and final states are created by specifying attributes for dimensions such as height, width, x and y coordinates.
- **Transformation phase** Individual segments of the stacked bars are selected and fill out transitions are performed on these segments. Simultaneously, each individual bar of the grouped bars is selected and fill in transitions are performed. The time delay of execution for each segment is set in accordance to the time delay and duration of execution of the previous segment. Also, the time duration for each segment is set to be proportional to the height of data, i.e the amount of liquid contained in that segment.
The containers for the segments of the stacked bar are set to disappear after each transition.
- **Final state** In the final state, the stack element is completely removed, and only the grouped bars remain.

## Installation
Download the latest version here:
https://github.com/sruthysrajan/Aquanims/archive/master.zip

## How to run
The files can be opened and edited on:
- Brackets (recommended): https://github.com/adobe/brackets/releases/download/release-1.13/Brackets.Release.1.13.msi
- Sublime Text: https://download.sublimetext.com/Sublime%20Text%20Build%203176%20x64%20Setup.exe
- Any other text editor.

## Dependancy

Already included:
- d3.js http://d3js.org/ Copyright 2017, Michael Bostock Released under BSD licenses.
