# Customizing the installation

The [default installation](https://github.com/olets/griid#typical-usage) from `.griid--install` will fit most needs, but you can also build a custom griid setup to support only the features your site uses. This keeps the compiled griid CSS weight to the lowest possible on a per-site basis

1. `.griid--base` is always required
2. `.griid--inline-alignment` adds support for using inline alignment classes. It's probably preferable to use [the alignment transformations](https://github.com/olets/griid#a-alignment) but just in case you really want to have it in your markup:
	- Add `.left`, `.center`, `.right` to a multi-row grid to override orphan alignment
	- Add `.left`, `.center`, `.right` to a cell to override the cell alignment
	- Add `.top`, `.middle`, or `.bottom` to a grid to control the default for its child cells
	- Add `.top`, `.middle`, or `.bottom` to a cell to control its vertical alignment
3. `.griid--single-row` adds support for single-row grids with equal-width, equal-height cells. By default these cells do NOT have gutters or row spacing
4. `.griid--space-single-row` (NOT included in [`.griid--install`](https://github.com/olets/griid#typical-usage)) adds gutters and row spacing (both @griid--gutter) to `.griid .cell*x` grids. Beware that this will frame the entire `.griid .cell*x` grids in a @griid-gutter space
5. `.griid--base`, with or without `.griid--inline-alignment` and`.griid--single-row`, still needs initialization.
  -            `.griid--initialize` gets you ready to go with all three grid types
  -          Or run any of `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row` if you don't need to support them all

6. `.griid .cell` grids do *not* have space around the cells by default. If you mix in `.griid--space-single-row`, these single-row grids will have gutters and row spacing *and a frame* of `@griid--gutter`
7. `griid--single-row-spacing` adds support for `.griid > .row*y > .cell*x`. This may be useful if you
  -	 want a grid with equal-height rows where that height is determined from the cell content
  -	 don't want to use a scripted solution (I love **[jquery-match-height](https://github.com/liabru/jquery-match-height)**)
  -  need to support orphan cells

	This will give you a multi-row grid where all cells are the full height of the row (aka it's styled as an equal-width-cells table). If your cells have similar content, this may even be a good-enough approximation of equal-height rows.
    
	Note that if last row is full this is exactly equivalant to `.griid*y > .cell*x` but with bulkier markup, and that if you don't need cells that are the full height of their row (or can achieve that matched height with a script) this has no advantage over `.griid-x .cell` while having several disadvantages (bulkier markup, and less easily manipulated by the griid functions we'll cover below).


**Note**:`.griid--install` is simply shorthand for `.griid--base;` + `.griid--inline-alignment;` + `.griid--initialize;`
