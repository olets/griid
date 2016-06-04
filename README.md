#griid
###The greedy grid that tries to do it all with LESS
v2.2.4

griid is a grid system with automatic rows. You can use the processed griid.css file on its own, but to take advantage its full usefulness you'll need LESS.

Supports IE > 8

griid supports [three grid types](https://github.com/olets/griid#markup-for-griids-three-grid-types): full-width single-row grids with cells of equal width and height; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, you can control the horizontal alignment of orphan cells (cells in non-full last rows), the space between all cells, and various other [parameters](https://github.com/olets/griid#griid-default-settings). Grids are infinitely nestable. And griid comes with mixin LESS functions that make it easy to change a grid's layout on the fly (e.g. in media queries)!

By default, griid LESS is fully built when included. If you don't want this, simply comment out line 1 of griid.less. If you do that, the griid LESS adds absolutely nothing to your compiled CSS until [built](https://github.com/olets/griid#typical-usage)-- include it in your default setup, and don't worry about adding bloat if you don't use it. In addition, all of griid's features are compartmentalized -- by [customizing your build](https://github.com/olets/griid#customizing-your-griid-installation), you can make sure that only the styles you need actually make it into your stylesheet.

Check out [the demo](http://olets.github.io/griid/) [the full suite of things griid can do](https://cdn.rawgit.com/olets/griid/v2.2.4/tests/griid-tests.html)

Here's [a demo pen](http://codepen.io/henry/pen/BKoNMq) with griid already imported - go play around!

###Table of contents
- [Markup for griid's three grid types](https://github.com/olets/griid#markup-for-griids-three-grid-types)
- [Getting griid](https://github.com/olets/griid#getting-griid)
- [Using griid](https://github.com/olets/griid#using-griid)
  - [Default settings](https://github.com/olets/griid#griid-default-settings)
  - [Typical usage](https://github.com/olets/griid#typical-usage)
- [griid LESS functions and mixins](https://github.com/olets/griid#griid-less-functions-and-mixins)
  - [Alignment](https://github.com/olets/griid#a-alignment)
  - [Grid transformations](https://github.com/olets/griid#b-grid-transformations)
 	   - [Adjusting .griid .cell grids](https://github.com/olets/griid#1-adjusting-griid-cell-grids)
 	   - [Adjusting .griid .cell-n-d grids](https://github.com/olets/griid#2-adjusting-griid-cell-n-d-grids)
 	   - [Adjusting .griid-x .cell grids](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids)
	 	   - [Resizing to an arbitrary column count](https://github.com/olets/griid#i-resizing-from-one-column-count-to-any-other-arbitrary-column-count)
	 	   - [Dropping the column count by one or more](https://github.com/olets/griid#ii-dropping-the-column-count-by-one-or-more)
 	   - [Adjusting both .griid-x .cell and .griid .cell-n-d grids](https://github.com/olets/griid#4-adjusting-both-griid-x-cell-and-griid-cell-n-d-grids)
 	   - [Adjusting all grids (.griid .cell, .griid-x .cell, and .griid .cell-n-d)](https://github.com/olets/griid#5-adjusting-all-grids-griid-cell-griid-x-cell-and-griid-cell-n-d)
   - [A transformation example: A progressively resposive grid](https://github.com/olets/griid#a-transformation-example-a-progressively-resposive-grid)
- [Customizing your griid installation](https://github.com/olets/griid#customizing-your-griid-installation)
	- [Customizing the installation](https://github.com/olets/griid#a-customizing-the-installation)
	- [Overriding default variables](https://github.com/olets/griid#b-overriding-default-variables)
- [Contributing](https://github.com/olets/griid#contributing)
- [Acknowledgements](https://github.com/olets/griid#acknowledgements)



## Customizing your griid installation

### A. Customizing the installation
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

&nbsp;

###B. Overriding default variables

The [initialization functions](https://github.com/olets/griid#customizing-your-griid-installation) can be re-run at any point to re-initialize with new settings or to wipe over customizations.

1.

	.griid--initialize(
	                  @fontSize: @griid--font-size,
	                   (@maxColCount: @griid--max-cols,
	                    (@minColCount: @griid--min-cols,
	                     (@smallestDenominator: @griid--max-cols,
	                      (@largestDenominator: @griid--min-cols,
	                      	(@gutter: @griid--gutter)))))
	                 )

2.

	.griid--initialize-equal-cells(
	                              @fontSize: @griid--font-size,
	                               (@maxColCount: @griid--max-cols,
	                                (@minColCount:@griid--min-cols,
                                	 (@gutter: @griid--gutter))
	                             )

3.

	.griid--initialize-unequal-cells(
	                                @fontSize: @griid--font-size, 
	                                 (@denominatorOfNarrowestCells: @griid--max-cols,
	                                  (@numeratorOfNarrowestCells: @griid--min-cols,
	                                   (@gutter: @griid--gutter))
	                               )
	                               

.4. If you really want to, you can even do a custom `.griid--install`


	.griid--install(
	               @fontSize,
	                (@gutter,
	                 (@rowSpacing,
	                  (@orphanAlignment,
	                   (@contentAlignment,
	                    (@maxColCount,
	                     (@minColCount,
	                      (@smallestDenominator,
	                       (@largestDenominator))))))))
	              )
	
&nbsp;

##Contributing
Pull requests, a SASS version, etc etc are more than welcome. Please check your version against tests/griid-tests.html, and add any new functions to the test suite.

&nbsp;

##Acknowledgements
griid grew out of ideas in [@JoelSutherland's](https://github.com/JoelSutherland) **grid-items** LESS grid

&nbsp;

&nbsp;

######Henry Bley-Vroman, 2016
