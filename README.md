#griid
###The greedy grid that tries to do it all with LESS

griid is a grid system with automatic rows. You can use the processed griid.css file on its own, but to take advantage its full usefulness you'll need LESS.

Supports IE > 8

griid supports [three grid types](https://github.com/olets/griid#markup-for-griids-three-grid-types): full-width single-row grids with cells of equal width and height; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, you can control the horizontal alignment of orphan cells (cells in non-full last rows), the space between all cells, and various other [parameters](https://github.com/olets/griid#griid-default-settings). Grids are infininely nestable. And griid comes with mixin LESS functions that make it easy to change a grid's layout on the fly (e.g. in media queries)!

Until [built](https://github.com/olets/griid#typical-usage), the griid LESS adds absolutely nothing to your compiled CSS -- include it in your default setup, and don't worry about adding bloat if you don't use it. In addition, all of griid's features are compartmentalized -- by [customizing your build](https://github.com/olets/griid#customizing-your-griid-installation), you can make sure that only the styles you need actually make it into your stylesheet.

Check out [the full suite of things griid can do](https://cdn.rawgit.com/olets/griid/bcb6ef678f7501d5d4304aee04e2493effc8aeca/tests/griid-tests.html)

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

 &nbsp;
 
---

&nbsp;

##markup for griid's three grid types:

Single-row grids with equal-width, equal-height cells look like `.griid > .cell`

Multi-row grids with equal-width cells look like
`.griid-x > .cell*n` (there will be x cells per row)

Multi-row grids with unequal-width cells look like
`.griid` for the grid, `.cell-n-d` for a cell n/d of the row width. Add `.row-end` to the last cell in each row. Full-width cells are `.cell-1-1` or `.cell-full`, and do not require `.row-end`

So

	<div class="griid">
		<div class="cell">1</div>
		<div class="cell">2</div>
		<div class="cell">3</div>
	</div>

will be

|- - -1- - -|- - -2- - -|- - -3- - -| (`.griid .cell`)

and

	<div class="griid">
		<div class="cell">4</div>
		<div class="cell">5</div>
		<div class="cell">6</div>
		<div class="cell">7</div>
	</div>


|- - 4- -|- - 5- -|- - 6- -|- - 7- -| (`.griid .cell` again, with a different cell count)

and

	<div class="griid-4">
		<div class="cell">1</div>
		<div class="cell">2</div>
		<div class="cell">3</div>
		<div class="cell">4</div>
		<div class="cell">5</div>
	</div>
	
will be 

|- - 1- -|- - 2- -|- - 3- -|- - 4- -| (`.griid-x .cell`)

|- - 5- -|

and 

	<div class="griid">
		<div class="cell-1-4">1</div>
		<div class="cell-3-4 row-end">2</div>
		<div class="cell-1-3">3</div>
		<div class="cell-1-2">4</div>
		<div class="cell1-6 row end">5</div>
	</div>

will be

|- - 1- -|- - - - - - 2 - - - - - - | (`.griid .cell-n-d`)

|- - 3 - - |- - - - 4 - - - -| - 5 -|


&nbsp;

## getting griid
Download and include **griid.less** and **griid-functions.less**.

Or add griid to your bower dependencies with
	
	bower install griid --save

Or it from the rawgit CDN (remember to update the URL to the latest version)

	https://cdn.rawgit.com/olets/griid/v2.1.8/griid.less
	https://cdn.rawgit.com/olets/griid/v2.1.8/griid-functions.less

&nbsp;

## using griid
###*griid* ***requires*** *initialization*



###griid default settings

At the top of griid.less are griid's default variables:

- For multi-row grids (`.griid-x .cell` and `.griid .cell-n-d`),
  - columns are separated by `@griid--gutter`
  - rows are separated by `@griid--row-spacing`,
  - and orphan cells are horizontally aligned following `@griid--orphan-h-align`

- In all cases, cells are vertically aligned by `@griid--item-v-align`.

- The base font size inside cells is `@griid--font-size`

&nbsp;

###Typical usage:
-    1. Definitely: run `.griid--install` to have full griid support, with the default `@griid--` values.
-    2. Likely: run adjustment functions in media queries to treat one grid as another in certain contexts ([see below](https://github.com/olets/griid#b-grid-transformations))
-    3. Possibly:
	- run `.griid--initialize` to revert any changes made by adjustment functions,
	- or if you only need to reset a particular type of grid, you can save a little weight by running `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row`
	- to have specific grids use a different baseline font size, you don't need to do a full new initialization. Just run `.griid--fz(@fontSize)`##griid LESS functions and mixins

griid has support for all sorts of adjustments. These are especially useful for media queries - turn your 1/3 - 2/3 layout into 1/2 - 1/2 [quickly and cleanly](https://github.com/olets/griid#2-adjusting-griid-cell-n-d-grids). [Progressively resize a grid](https://github.com/olets/griid#a-transformation-example-a-progressively-resposive-grid) first from 6 columns (the factory default max columns for griid) [to 5](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids), then 4, 3, 2, 1. Turn a [single-row grid into](https://github.com/olets/griid#1-adjusting-griid-cell-grids) a three-column grid. Pretty much anything you could want to do, you can.

&nbsp;

Explanations of all the adjustments are here. You might also **[check out the test suite](https://cdn.rawgit.com/olets/griid/bcb6ef678f7501d5d4304aee04e2493effc8aeca/tests/griid-tests.html) for an example of each available adjustment**.

&nbsp;

###A. Alignment
1. `.griid--vertical-align(@args:@griid--item-v-align)`

    Change the vertical alignment of cell contents
    Default re-initializes
	
	There are also shorthand mixins:
	`.griid--top` (shorthand mixin for `.griid--vertical-align(top)`)
	`.griid--middle` (shorthand mixin for `.griid--vertical-align(middle)`)
	`.griid--bottom` (shorthand mixin for `.griid--vertical-align(bottom)`)
	
1. `.griid--orphan-align(@alignment:@griid--orphan-h-align)`

    Change how orphan cells in multi-row grids are aligned
    Default re-initializes
    
    And shorthand mixins:
	`.griid--left` (shorthand mixin from `.griid--orphan-align(left)`)
	`.griid--center` (shorthand mixin from `.griid--orphan-align(center)`)
	`.griid--right` (shorthand mixin from `.griid--orphan-align(right)`)

&nbsp;

###B. Grid transformations

Note: *all transformation functions check markup, not styling*. When you target `.griid-x` grids with a certain column count, griid targets *ostensible* column counts, disregarding any transformations you may have done. For example: If you use  `.griid--drop-one(5);` to turn a five-column grid into four-column grid ([see below](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids)) and later want to turn it into a three-column grid, you'll need to do either `.griid--drop(2,5)` ("drop by 2 the column count of 5-column grids") or `.griid--resize-one(3,5)` ("resize to 3 columns all 5-column grids"). Don't be tricked into thinking you can do `.griid--drop-one(4)` - as far as `.griid--drop-one()` is concerned, this is still a `.griid-5`. Similarly, `.griid--drop; .griid-drop` is no different than `.griid--drop`. In practice this isn't a problem - there are enough options that you'll be able to easily do what you want.

####1. Adjusting `.griid .cell` grids

1. `.griid--resize-row(@treatAs:1)`
    Turn a single-row grid into a multi-row grid with a **@treatAs** number of cells per row
    Default turns the cells into blocks


####2. Adjusting `.griid .cell-n-d` grids
    
1. `.griid--resize-one-unequal((@treatAsNumerator:1, @treatAsDenominator:2,) @targetNumerator, @targetDenominator)`
Resize one fractional-width cell type
  - `.griid--resize-one-unequal(@targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` cells into `.cell-1-2`    
  - `.griid--resize-one-unequal(@treatAsNumerator, @treatAsDenominator, @targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` into `.cell-@treatAsNumerator-@treatAsDenominator`


1. `.griid--resize-unequal(@treatAsNumerator:1, @treatAsDenominator:2(, @numeratorOfLargest, @denominatorOfLargest))`
  -    Resize all fractional smaller than or equal to target
  -    Default turns all fractional widths into `.cell-1-2`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator)` turns all fractional widths into `cell-@treatAsNumerator-@treatAsDenominator`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator, @numeratorOfLargest, @denominatorOfLargest)` turns all fractions equal to or smaller than **@numeratorOfLargest**/**@denominatorOfLargest** into `cell-@treatAsNumerator-@treatAsDenominator`


####3. Adjusting `.griid-x .cell` grids

#####i. Resizing from one column count to any other arbitrary column count
1. `.griid--resize-one-equal((@treatAs:1,) @target)`
    Resize one equal width
    `.griid--resize-one-equal(@target)` will turn cells in an `.griid-@target` into blocks

1. `.griid--resize-equal(@treatAs:1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))`
    Change the column count of `.griid-x .cell` griids - optionally only targeting grids with a certain column count or targeting only grids with a column count within a certain range
    Default turns cells in *all* `.griid-x` grids into blocks
  -    `.griid--resize-equal(@treatAs)` turns all `.griid-x` grids into `.griid-@target` grids
  -    `.griid--resize-equal(@treatAs, @minColCount)` turns all `.griid-x` grids with at least **@minColCount** columns into `.griid-@treatAs`
  -    `.griid--resize-equal(@treatAs, @minColCount, @maxColCount)` turns all `.griid-x` grids with at least **@minColCount** and at most **@maxColCount** columns into `.griid-@treatAs`

  The resize functions can add or remove columns from a grid.

#####ii. Dropping the column count by one or more

1. `.griid--drop-one((@dropBy:1,) @target)`
    Drops one or more columns from "one" specified grid type.
  -    `.griid--drop-one(@target)` will turn `.griid-@target` into `.griid-(@target-1)`
  -    `.griid--drop-one(@dropBy, @target)` will turn `.griid-@target` into `.griid-(@target-@dropBy)`

1. `griid--drop(@dropBy: 1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))` 
    Default drops one column from all `.griid-x` grids
  - `griid--drop(@dropBy)` drops **@dropBy** columns from all `.griid-x` grids
  - `griid--drop(@dropBy, @minColCount)` drops  **@dropBy** columns `.griid-x` grids that have at least **@minColCount** columns
  - `griid--drop(@dropBy, @minColCount, @maxColCount)` drops **@dropBy** columns from grids with between **@minColCount** and **@maxColCount** columns (inclusive)


###4. Adjusting both `.griid-x .cell` and `.griid .cell-n-d` grids

1. `.griid--row`
    Turn a `.griid-x .cell` or `.griid .cell-n-d` grid into a `.griid .cell` grid
    
###5. Adjusting all grids (`.griid .cell`, `.griid-x .cell`, and `.griid .cell-n-d`)
1. `.griid--resize(@treatAs:1)`
    Turns *all* grids into `.griid-@treatAs` (and all `.cell-n-d` into `.cell`)
    
    Default turns all cells into blocks


&nbsp;

###A transformation example: A progressively resposive grid

Here's a simple example of how you might use [griid's `resize` function](https://github.com/olets/griid#3-adjusting-griid-x-cell-grids) to build a progressively responsive grid, targeting just a particular grid. (Note that the calculations aren't *perfect* if @griid--gutter is non-zero, but who's looking that closely?)

	.progressive-grid() {
	    @grid-items--max-width: [your site width];
	    
	    @max5: 5 * @griid--max-width / 6;
	    @max4: 2 * @griid--max-width / 3;
	    @max3: @griid--max-width / 2;
	    @max2: @griid--max-width / 3;
	    @max1: @griid--max-width / 6;
	    
	    @media(max-width: @max5) {
	        .griid--resize(5,5)
	    }
	    @media(max-width: @max4) {
	        .griid--resize(4,4)
	    }
	    @media(max-width: @max3) {
	        .griid--resize(3,3)
	    }
	    @media(max-width: @max2) {
	        .griid--resize(2)
	    }
	    @media(max-width: @max1) {
	        .griid--resize
	    }
	}
	#footer-grid {
		.progressive-grid
	}

&nbsp;

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
	                      (@largestDenominator: @griid--min-cols))))
	                 )

2.

	.griid--initialize-equal-cells(
	                              @fontSize: @griid--font-size,
	                               (@maxColCount: @griid--max-cols,
	                                (@minColCount:@griid--min-cols))
	                             )

3.

	.griid--initialize-unequal-cells(
	                                @fontSize: @griid--font-size, 
	                                 (@denominatorOfNarrowestCells: @griid--max-cols,
	                                  (@numeratorOfNarrowestCells: @griid--min-cols))
	                               )
	                               

.4. If you really want to, you can even do a custom `.griid--build`


	.griid--build(
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
