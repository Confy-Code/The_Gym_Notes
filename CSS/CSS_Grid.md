## CASCADING STYLE SHEETS (CSS) PART 1 B - CSS Grid
*Author: Confy-Code*
> In this file, we are going to focus on the concept of "CSS Grid" and This layout modes is essential for creating responsive and flexible web designs. We assume the core basics of CSS are already known.

>CSS Grid is the latest layout mode in CSS and it provides a powerful way to create complex and responsive web designs. It is already suppported in all modern browsers as it is 96% supported and only 0.5% less than Flexbox.
===
1. We opt in the CSS Grid layout by assigning the `display` property to `grid` on a container element. This will make all of its direct children become grid items.

```css.container {
  display: grid;
}
```
---

2. **GRID FLOW**
   - By default, CSS Grid uses a single column, and will create rows as needed, based on the number of children.
   - By default, the height of the grid parent is determined by its children
---

3. **GRID TEMPLATE COLUMNS AND ROWS**
   - We can define the number of columns and rows in a grid using the `grid-template-columns` and `grid-template-rows` properties.
   - These properties accept a list of values that specify the size of each column or row. For example, `grid-template-columns: 100px 200px;` will create two columns, the first one being 100 pixels wide and the second one being 200 pixels wide.
   - We can also use the `fr` unit to create flexible columns or rows that take up a **fraction** of the available space. For example, `grid-template-columns: 1fr 2fr;` will create two columns, where the first column takes up one-third of the available space and the second column takes up two-thirds of the available space.
---

4. `grid-gap` was renamed to `gap` in CSS Grid, and it is used to specify the spacing between grid items. This `grid` has been adopted in CSS Flexbox as well.
---

5. The `repeat()` method can be used over `grid-template-columns` property to do the job of copy-pasting for us. For example if we had to create seven 1fr-columns (say we want for example to make a seven-day calendar), instead of writing `grid-template-columns: 1fr 1fr 1fr 1fr ...` we can write `grid-template-columns: repeat(7, 1fr)`.

---
6. #### ASSIGNING COLUMNS AND ROWS STATICALLY
> By default, the grid item is given the first cell (first row first column) of the grid parent. However we can specify where our child sits buy using `grid-column` and `grid-row` properties.

```css
.parent {
    grid-template-columns: repeat (4, 1fr);
    grid-template-rows: repeat (4, 1fr);
}

.child-1{
    grid-column: 2;
    grid-row: 2; /*This child sits on row 2 column 2 (these numbers do not represent the indices) */
}

.child-2 {
    grid-column: 1/ 3; /*from column 1 to column 3 excluded (hence covers 2 columns only) */

    grid-row: 1 / -1; /* from row 1 to the first row from the bottom (4th row in our case, as we have 4 rows) */
}
```
---

7. ### ASSIGNING COLUMNS AND ROWS DYNAMICALLY

>Instead of just saying `grid-column: 2`, sometimes we don't know the column number (or a row number as well) on which we want our grid child to sit. To mitigate this we use `span`

**span**: When we want to assign a number of columns or rows to a child instead of specifying the column numbers on which it should sit on, we can for example, write `grid-column: span 2;` to give up *2 columns* to an element. We do not want to know which specific columns will cover that range.
---

> To Be Discussed Later: `grid-auto-flow: row dense | column dense ;`: This CSS property controls how the auto-placement algorithm works in CSS Grid, especially when the order of the grid children is not necessary.
---

8. ### GRID AREAS

Instead of using `grid-column` and `grid-row` repeatedly to define the layouts like the dashboard's, we can use pre-defined **Grid areas** using `grid-template-areas: sidebar | header | main ;` property. You can align the areas however you want.

> When we write `property: value 1 | value 2`, we mean that you can use either of the values. We just want to show you the possible values to that specific property.
---

9. ### DOM POSITION VS GRID POSITION

- The `reading-order: [number]` property in CSS manually overrides the order in which child elements are evaluated by screen readers and keyboard tab navigation. In other words, It allows you to specify the `Tab order` of each element.

> Note that this feature is only supported by Chrome and Edge as of May 2026. Follow this [link](https://caniuse.com/wf-reading-flow) to discover where it is supported.

- `reading-flow: grid-rows` is often used when we have used a standard grid layout, and we do not want to assign a `reading-order` number to every child. This automatically follows the visual grid placement row by row. Use `reading-flow: grid-columns` for column by column placement.

> if you decide to use `reading-order` over a grid child, set the `reading-flow: source-order` property for the parent, to tell the container to allow explicit child ordering modification. Lowest value of `reading-order` comes first.
---

10. ### ALIGNMENT OF GRID ELEMENTS (HORIZONTALLY)

- We use `justify-content: start | end | centre | stretch` to arrange the compartments of our grid, distributing them across the grid however we wish.

- If we want to align the items themselves within their columns, we can use the `justify-items` property.

- We can even control the alignment of a specific grid child using the `justify-self` property.

---
11. ### ALIGNMENT OF GRID ELEMENTS (VERTICALLY)

> CSS Grid provides an additional set of properties to align stuff in the vertical direction using `align-content: start | end | centre | space-between | space-around | space-evenly `, `align-items` and `align-self`.

* `align-content` is like `justify-content`, but it affects rows instead of columns. Similarly, `align-items` is like `justify-items`, but it handles the vertical alignment of items inside their grid area, rather than horizontal. That proportionality also goes for `align-self` and `justify-self` pair.

---

12. ### Two-line centering trick

To place an element onto the centre of our grid container, we can use:
```css
.parent {
    display: grid;
    justify-content: centre;
    align-content: centre;
}
```
However we have a shorthand for this. `place-content: centre` solves it all.
---

Credits: [Josh Comeau Blog post](https://www.joshwcomeau.com/css/interactive-guide-to-grid/)

===

**~END~**






