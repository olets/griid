#griid
###The greedy grid that tries to do it all with LESS
v2.2.4

griid is a grid system with automatic rows. You can use the processed griid.css file on its own, but to take advantage its full usefulness you'll need LESS.

Supports IE > 8

griid supports [three grid types](https://github.com/olets/griid#markup-for-griids-three-grid-types): full-width single-row grids with cells of equal width and height; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, you can control the horizontal alignment of orphan cells (cells in non-full last rows), the space between all cells, and various other [parameters](https://github.com/olets/griid#griid-default-settings). Grids are infinitely nestable. And griid comes with mixin LESS functions that make it easy to change a grid's layout on the fly (e.g. in media queries)!

By default, griid LESS is fully built when included. If you don't want this, simply comment out line 1 of griid.less. If you do that, the griid LESS adds absolutely nothing to your compiled CSS until [built](https://github.com/olets/griid#typical-usage)-- include it in your default setup, and don't worry about adding bloat if you don't use it. In addition, all of griid's features are compartmentalized -- by [customizing your build](https://github.com/olets/griid#customizing-your-griid-installation), you can make sure that only the styles you need actually make it into your stylesheet.

Check out [the demo](http://olets.github.io/griid/) [the full suite of things griid can do](https://cdn.rawgit.com/olets/griid/v2.2.4/tests/griid-tests.html)

Here's [a demo pen](http://codepen.io/henry/pen/BKoNMq) with griid already imported - go play around!

######Henry Bley-Vroman, 2016
