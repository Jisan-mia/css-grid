## CSS GRid

**What's this?**
It's easier to create multi dimensional layouts with css grid. Eg. We can work both on X-axis and Y-axis at a time. In simplified term ->

Grid is a css box model to easily layout, align and distribute space among items withing a container both horizontally and vertically.

- Also its markup is more simpler
- CSS grid is more flexible in terms of responsive web design
- No need of frameworks for responsiveness 
- Good browser support

## Before get started we need to know some of the grid basics:

---

- In grid, the element or container which wraps all the children elements or items is called _flexbox container_ and childrens or each children elements/items are called _flexbox items_.
- Grid container has their own properties and values
- Same goes to children, also grid items/childrens has their own properties and values
- In flexbox, there are two axis, they are _Main axis_ and _Cross axis_.
- To make a grid container `display: grid;`

## Available properties for grid container:

---

- A grid container must have display property with grid value. It allows us to use others gird properties.
   - `display: grid`

- `grid-template-columns`: property allows us to implement how many columns we need and what size(width) each column should be.
    - `grid-template-columns: 100px 200px 100px;` we defined 3 colums with respective width.
- `grid-template-rows`: property allows us to implement how many rows we need and what size(height) each row should be
  - `grid-template-rows: 200px 200px;` we defined 2 ros with respective height.

- Note: We can use _auto_ as `grid-template-columns` value width which flexes or filed the available spaces.

- `grid-row-gap`: is use to give some gap between grid rows.
  - `grid-row-gap: 10px;`

- `grid-column-gap`: is use to gie some gap between grid columns. 
  - `grid-column-gap: 8px;`
  
- `grid-gap`: property combines `grid-row-gap` &  `grid-column-gap` and give gaps between ros and columns.
  - `grid-gap: 1rem;` (same gap between grid rows and columns)
  - `grid-gap: 5px 10px;` (first value for row gap and the second for column gap)
  
## Fractional units 

---

We can use fractional units as values of  `grid-template-columns` and `grid-template-rows` for more responsiveness.

```css
   grid-template-columns: 1fr 2fr; /* [fr = fraction] */
   grid-template-rows: 1fr 1fr
```
-  above code means.. 3fr(1fr + 2fr) is the full width or the available width for the grid container and 1fr of 3fr(1/3) is the first column width and remaining 2fr of 3fr(2/3) is the second column width.
- same goes for teh `grid-template-rows` difference is that in the place of _width_ there will be _height_
  
- We can use both `grid-template-columns` and `grid-template-rows` in one property. Below is an example:
  - `grid-template: 1fr 2fr / 1fr;` 
  - here first part(1fr 2fr) is the value of grid-template-columns
  - second part(1fr) is the value of grid-template-rows


## Repeat Function

---

When we need so many columns and rows with same width or height we can use _repeat() function_. It takes two value as arguments, one is the number of time we want to repeat or how many columns or rows should be, second argument is the width or height value we want to give for every columns or rows.

- `grid-template-columns: repeat(4, 1fr);`
  - 4 column each has 1/4 width of full width or available width.
- `grid-template-rows: repeat(2, 120px)`
  - 2 rows each has 120px height


## Available properties for grid item or positioning  items: 

---

We can make a particular grid item or children to take full width or a two-column grid or take full height of row by using `grid-column` and `grid-row` property on a particular grid item. 



















