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
