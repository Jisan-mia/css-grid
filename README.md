## CSS GRid

**What's this?**
It's easier to create multi dimensional layouts with css grid. Eg. We can work both on X-axis and Y-axis at a time. In simplified term ->

Grid is a css box model to easily layout, align and distribute space among items withing a container both horizontally and vertically.

- Also its markup is more simpler
- CSS grid is more flexible in terms of responsive web design
- No need of frameworks for responsiveness 
- Good browser support

### Before get started we need to know some of the grid basics:

---

- In grid, the element or container which wraps all the children elements or items is called _flexbox container_ and childrens or each children elements/items are called _flexbox items_.
- Grid container has their own properties and values
- Same goes to children, also grid items/childrens has their own properties and values
- In flexbox, there are two axis, they are _Main axis_ and _Cross axis_.
- To make a grid container `display: grid;`

### Available properties for grid container:

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
  
- `grid-gap`: property combines **`grid**-row-gap` &  `grid-column-gap` and give gaps between ros and columns.
  - `grid-gap: 1rem;` (same gap between grid rows and columns)
  - `grid-gap: 5px 10px;` (first value for row gap and the second for column gap)
  
### Fractional units 

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


### Repeat Function

---

When we need so many columns and rows with same width or height we can use _repeat() function_. It takes two value as arguments, one is the number of time we want to repeat or how many columns or rows should be, second argument is the width or height value we want to give for every columns or rows.

- `grid-template-columns: repeat(4, 1fr);`
  - 4 column each has 1/4 width of full width or available width.
- `grid-template-rows: repeat(2, 120px)`
  - 2 rows each has 120px height


### Available properties for grid item or positioning  items: 

---

We can make a particular grid item or children to take full width or a two-column grid or take full height of row by using `grid-column` and `grid-row` property on a particular grid item. 

- `grid-column: 1/3;`
   - first part(1) is the value of `grid-column-start` defines where this particular column should start
   - second part(3) is the value of `grid-column-end` defines where this particular column should end.
   - more `grid-column: 1/-1 || 1/span 2` etc.
- `grid-row: 2/3;`
   - first part(2) is the value of `grid-row-start`, second(3) is for `grid-row-end`.
   - And same as `grid-column` first part defines the row starting point and second for row ending point

### grid-template-areas: 

---

with this property we can visually make our layout. Suppose we have 12 column grid(each width: 1fr), we want to make below layout:

** Layout picture **

- It's 12 column based grid layout. In the container we need to do:
```css 
   grid-template-areas: 
   ". h h h h h h h h h h ."
   "m m m c c c c c c c c c"
   ". f f f f f f f f f f ."

    /* 
   .(dot) means this column content is empty space, here
   h = header area
   m = menu area
   c = content area
   f = footer area
   */
```

- Now, we need to define h, m, c and f using `grid-area` property for teh particular item
```css
   .header{
      grid-area: h;
   }
   .menu{
      grid-area: m;
   }
   .content{
      grid-area: c;
   }
   .footer{
      grid-area: f;
   }
   /* that's it */
```

### auto-fit and minmax: 
---

- `grid-template-column: repeat(auto-fit, minmax(200px, 1fr));`
- _**minmax**_ is a function that takes a minimum value and a maximum value.
- _**auto-fit**_ if we don't want a fix number of columns or rows we can use *auto-fit*
- _**auto-fill**_ if we use *auto-fill* in the place of *auto-fit*, we will see a different scenario:
  - when each grid time comes in one line and we increase the browser width *grid-items* doesn't fit the browser width.

### implicit-rows or extra rows: 
---
When we define height only for 1 ***row***, other rows(if any) take its place automatically according to its height and width.
- We can control the height of these extra ***rows*** which are automatically taking place below the rows by/using:
  - `grid-auto-rows: 200px` (the height of extra rows will be 200px)


### Content/container alignment properties: 
---

- `justify-content`: property defines how the remaining space of content should be distributed in main-axis/row-direction:
  - `justify-content: start(default);`
  - `justify-content: right;` (align to the right)
  - `justify-content: center;` (align to the center)
  - `justify-content: space-between;` (give space between columns)
  - `justify-content: space-around;` (give space around columns equally)
  - `justify-content: space-evenly;`

- `align-content`: property defines how the remaining space of content should be distributed in cross-axis for rows.
  - It has same vales as `justify-content` has but it provides alignment in cross-axis
  - ***Note:*** `align-content: end`

### Items alignment properties: 
---
These properties should use in grid container 
- `justify-items: end;` (align item to the end of the item/box horizontally)
- `justify-items: center` (align item to the center of the item/box horizontally) 
- `align-items: end` (align item to the end of the item/box vertically)
- `justify-items: center` (align item to the center of the item/box vertically)

These properties should use in grid individual item:
- `justify-self`: is a grid-item property we can align individual item using this:
  - `justify-self: start | center || end;` (align to the start/center/end of the box only to the particular item) 


---
If you want to know whether the browser support css-grid or not, you can check it by-
```cs
@supports (display: grid) {
  // if support all the rules of grid will support code written here
}
```




