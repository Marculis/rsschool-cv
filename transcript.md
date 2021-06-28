Hi. In this video we are going to talking about CSS page layouts.
This is the list of CSS techniques:
• Normal flow
• The display property
• Flexbox
• Grid
• Floats
• Positioning
• Table layout

Each technique has its uses, advantages, and disadvantages, and no technique is designed to be used in isolation.
In particular we going to talk about CSS Grid Layout.

Basic Concepts of grid layout
CSS Grid Layout introduces a two-dimensional grid system to CSS. Grids can be used to lay out major page areas or small user interface elements.

CSS grid layout has the following features:
• Fixed and flexible track sizes
• Item placement
• Creation of additional tracks to hold content
• Alignment control
• Control of overlapping content

The Grid container
We create a grid container by declaring display: grid or display: inline-grid on an element. As soon as we do this, all direct children of that element become grid items.

In this example, I have a containing div with a class of wrapper and, inside are five child elements.
I make the .wrapper a grid container.
All the direct children are now grid items.

Grid tracks
We define rows and columns on our grid with the grid-template-columns and grid-template-rows properties. These define grid tracks. A grid track is the space between any two lines on the grid.

The fr unit
Tracks can be defined using any length unit. Grid also introduces an additional length unit to help us create flexible grid tracks. The new fr unit represents a fraction of the available space in the grid container.

Track listings with repeat() notation
Large grids with many tracks can use the repeat() notation, to repeat all or a section of the track listing.
In this example two different codes, but its have the same result.

Repeat notation takes the track listing, and uses it to create a repeating pattern of tracks.

Auto set
You can also define a set size for tracks created in the implicit grid with the grid-auto-rows and grid-auto-columns properties.

In the below example we use grid-auto-rows to ensure that tracks created in the implicit grid are 120 pixels tall.

Track sizing and minmax
When setting up an explicit grid or defining the sizing for automatically created rows or columns we may want to give tracks a minimum size, but also ensure they expand to fit any content that is added. For example, I may want my rows to never collapse smaller than 100 pixels, but if my content stretches to 300 pixels in height, then I would like the row to stretch to that height.
Grid has a solution for this with the minmax() function.

Positioning items against lines
In the following example I am placing the first two items on our three column track grid, using the grid-column-start, grid-column-end, grid-row-start and grid-row-end properties.

From left to right, the first item is placed against column line 1, and spans to column line 4, which in our case is the far-right line on the grid. It begins at row line 1 and ends at row line 3, therefore spanning two row tracks.
The second item starts on grid column line 1, and spans one track. This is the default so I do not need to specify the end line. It also spans two row tracks from row line 3 to row line 5. The other items will place themselves into empty spaces on the grid.

Gutters
Gutters or alleys between grid cells can be created using the column-gap and row-gap properties, or the shorthand gap.

Nesting grids
A grid item can become a grid container. In the following example, I have the three-column grid. In this case the first item has some sub-items. As these items are not direct children of the grid they do not participate in grid layout and so display in a normal document flow.

Nesting without subgrid
If I set box1 to display: grid I can give it a track definition and it will become a grid too. The items then lay out on this new grid.
In this case the nested grid has no relationship to the parent. As you can see in the example it has not inherited the gap of the parent and the lines in the nested grid do not align to the lines in the parent grid.

In the current specification, we would edit the above nested grid example to change the track definition of grid-template-columns: repeat(3, 1fr), to grid-template-columns: subgrid. The nested grid will then use the parent grid tracks to layout items. But This feature shipped in Firefox 71, which is currently the only browser to implement subgrid.

Overlapping without z-index
If we return to our example with items positioned by line number, we can change this to make two items overlap.
By changing values of second box
The item box2 is now overlapping box1, it displays on top as it comes later in the source order.

Grid cells
A grid cell is the smallest unit on a grid. Conceptually it is like a table cell. As we saw in our earlier examples, once a grid is defined as a parent the child items will lay themselves out in one cell each of the defined grid. In the below image, I have highlighted the first cell of the grid.

Grid areas
Items can span one or more cells both by row or by column, and this creates a grid area. Grid areas must be rectangular – it impossible to create an L-shaped area for example. The highlighted grid area spans two row and two column tracks.

Instead of defining rows and columns, we've laid out the whole grid visually with named grid areas. Each row is written as a string surrounded with double quotes, and each cell is given the name of the grid area it belongs to. If a cell doesn't need to belong to any area, just put a dot in that spot.

Once you've got your grid areas defined, you can attach your grid items to them by setting an item's grid-area rule to the name of the area where you want it to go!

You can also use the shorthand grid-template rule to define grid-template-columns and grid-template-rows at once. In this shorthand, you can optionally give each row a height immediately following its description, then if you want column sizes you can add a slash after the final row and specify column sizes at the end.

It’s looks more readable, visualizable, and ultimately maintainable for grid layouts with static items than long lists of explicit grid lines.

So, CSS Grid is powerful instrument of layout. It take us easy way to create flexible, responsive, beautiful layouts, and all without sacrificing well-structured, slim, semantically pure HTML.
