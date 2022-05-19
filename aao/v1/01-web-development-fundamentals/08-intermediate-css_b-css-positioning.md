# CSS Positioning

5 Values of Position

1. Static
2. Relative
3. Absolute
4. Fixed
5. Sticky

## Static Positioning

`position: static;`

The default position of page elements. Not considered positioned, since it will appear with established page flow. `top`, `bottom`, `left`, right`, and `z-index` don't effect static elements.

## Relative Positioning

`position: relative;`

Is offset from its original position using `top/right/bottom/left` properties. It is positioned `relative` to its original place in page flow.

Creates a stacking context for use with `z-index`. [read more about the stacking context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

## Absolute Positioning

`position: absolute;`

Removed from page flow and other elements act like it is not there. Element is positioned in relation to its closest positioned ancestor, or if it can not be found, the html document. It is offset from that position using `top/right/bottom/left` properties.

Creates a stacking context for use with `z-index`. [read more about the stacking context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

---
