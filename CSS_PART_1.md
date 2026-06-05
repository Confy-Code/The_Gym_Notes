## CASCADING STYLE SHEETS (CSS) PART 1

> In this file, we are going to focus on the concept of "Flexbox" and This layout modes is essential for creating responsive and flexible web designs. We assume the core basics of CSS are already known.
---
1. **CSS Layout modes**: These are the different ways in which elements can be arranged on a web page. The main layout modes include:
   - Block Layout: Elements are displayed as blocks, taking up the full width of their container and stacking vertically.
   - Inline Layout: Elements are displayed inline, taking up only as much width as necessary and flowing horizontally.
   - Flexbox Layout: A layout mode that allows for flexible and responsive arrangements of elements within a container.
   - Grid Layout: A layout mode that provides a two-dimensional grid-based structure for arranging elements in rows and columns.

---
2. **Flex directions**: In Flexbox, the `flex-direction` property defines the direction in which the flex items are placed in the flex container. The possible values are:
   - `row`: The default value. Flex items are arranged horizontally from left to right.
 
   - `column`: Flex items are arranged vertically from top to bottom.

---
3. **Primary and Cross axes**: In Flexbox, the primary axis is the main axis along which the flex items are laid out, determined by the `flex-direction` property. The cross axis is perpendicular to the primary axis. For example:
   - If `flex-direction` is set to `row`, the primary axis is horizontal, and the cross axis is vertical.
   - If `flex-direction` is set to `column`, the primary axis is vertical, and the cross axis is horizontal.
   - `Cross axis`: Children will stretch out to fill the entire container
   - `Primary axis`: Children will be bunched up at the start of the container
---
4. **Justify-content**: This property is used to align flex items along **the primary axis**. The possible values include:
   - `flex-start`: Aligns items to the start of the container (default).
   - `flex-end`: Aligns items to the end of the container.
   - `center`: Centers items within the container.
   - `space-between`: Distributes items evenly with the first item at the start and the last item at the end.
   - `space-around`: Distributes items evenly with equal space around them.
---
5. **Align-items**: This property is used to align flex items along **the cross axis**. The possible values include:
   - `stretch`: Stretches items to fill the container (default).
   - `flex-start`: Aligns items to the start of the cross axis.
   - `flex-end`: Aligns items to the end of the cross axis.
   - `center`: Centers items along the cross axis.
   - `baseline`: Aligns items along their baseline.
---
6. **Align-self**: Unlike justify-content and align-items, which apply to the entire flex container, `align-self` allows you to override the alignment for individual flex items along the cross axis. The possible values are the same as `align-items`:
   - `stretch`: Stretches the item to fill the container (default).
   - `flex-start`: Aligns the item to the start of the cross axis.
   - `flex-end`: Aligns the item to the end of the cross axis.
   - `center`: Centers the item along the cross axis.
   - `baseline`: Aligns the item along its baseline.
---
>Summary of Definitions so far:
   - `justify` — to position something along the primary axis.
   `align` — to position something along the cross axis.
   `content` — a group of “stuff” that can be distributed.
   `items` — single items that can be positioned individually.

   > There is no justify-self or justify-items because we have to think of the primary axis as a group (of items as slices of meat on kebab skewers) and not as individual items. The cross axis is the one that can be thought of as individual items.
---
7. **CSS as a collection of layout modes**: It is better to think of CSS as the collection of layout modes rather than collection of properties. For example, the property `width` behaves differently when used in `flow layout` (block layout) compared to when it is used in `flexbox layout`. In block layout, `width` defines the width of the element regardless of the parent capability to hold it, while in flexbox layout.
---


