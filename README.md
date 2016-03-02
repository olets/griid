#griid
###The greedy grid that tries to do it all with LESS

griid is a grid system with automatic rows. You can use the processed griid.css file on its own, but to take advantage its full usefulness you'll need LESS.

Supports IE > 8

griid supports three grid types: single full-width single-row grids  with cells of equal width; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, you can control the horizontal alignment of orphan cells (cells in non-full last rows)

---

##markup for griid's three grid types:

Single-row grids with equal-width, equal-height cells look like `.griid > .cell`

Multi-row grids with equal-width cells look like
`.griid-x > .cell*n` (there will be x cells per row)

Multi-row grids with unequal-width cells look like
`.griid` for the grid, `.cell-n-d` for a cell n/d of the row width. Add `.row-end` to the last cell in each row. Full-width cells are `.cell-1-1` or `.cell-full`, and do not require `.row-end`

So:

	<div class="griid">
		<div class="cell">1</div>
		<div class="cell">2</div>
		<div class="cell">3</div>
	</div>
	<div class="griid">
		<div class="cell">4</div>
		<div class="cell">5</div>
		<div class="cell">6</div>
		<div class="cell">7</div>
	</div>

will be

|- - -1- - -|- - -2- - -|- - -3- - -|

|- - 4- -|- - 5- -|- - 6- -|- - 7- -|

and

	<div class="griid-4">
		<div class="cell">1</div>
		<div class="cell">2</div>
		<div class="cell">3</div>
		<div class="cell">4</div>
		<div class="cell">5</div>
	</div>
	
will be 

|- - 1- -|- - 2- -|- - 3- -|- - 4- -|

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

|- - 1- -|- - - - - - 2 - - - - - - |

|- - 3 - - |- - - - 4 - - - -| - 5 -|
		

--

Bonus: the markup won't be as beautiful, but if
-	 you want a grid with equal-height rows where that height is determined from the cell content
-	 and you don't want to use a scripted solution (I love [jquery-match-height](https://github.com/liabru/jquery-match-height))
-    and your cells have roughly similar content,
-    and you need to support orphan cells

you *may* be able to get away with

    `.griid > .row*y > .cell*x`

This will give you a multi-row grid where all cells are the full height of the row (aka it's styled as an equal-width-cells table). If your cells have similar content, this may be a good-enough approximation of equal-height rows.
    
Note that if last row is full, this is exactly equivalant to `.griid*y > .cell*x` but with bulkier markup

In most cases though you'll probably be better off using `.griid-x > .cell*(x*y)`

    
##Configuration

- For multi-row grids (`.griid-x .cell` and `.griid .cell-n-d`),
  - columns are separated by `@griid-gutter`
  - rows are separated by `@griid--row-spacing`,
  - and orphan cells are horizontally aligned following `@griid--orphan-h-align`

- If you run `.griid--space-single-row` (see below) single-row grids (`.griid .cell*x`) will have gutters and row spacing *and a frame* of `@griid--gutter`


- In all cases, cells are vertically aligned by `@griid--item-v-align`.

- The base font size inside cells is `@griid--font-size`

- You can optionally include support (with `.griid--inline-alignment`) for alignment classes to use in your markup. As we will see, there are functions for doing this in **griid-functions.less** (see below) but just in case you really want to have it in your markup:
	- Add `.left`, `.center`, `.right` to a multi-row grid to override orphan alignment
	- Add `.left`, `.center`, `.right` to a cell to override the cell alignment
	- Add `.top`, `.middle`, or `.bottom` to a grid to control the default for its child cells
	- Add `.top`, `.middle`, or `.bottom` to a cell to control its vertical alignment



##griid LESS

###*griid* ***requires*** *initialization*

###A. Typical usage:
-    1. Definitely: run `.griid--install` to have full griid support, with the default `@griid--` values.
-    2. Likely: run adjustment functions in media queries to treat one grid as another in certain contexts (using **griid-functions.less**; see below)
-    3. Possibly:
	- run `.griid--initialize` to revert any changes made by adjustment functions,
	- or if you only need to reset a particular type of grid, you can save a little weight by running `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row`


###B. Customizing your setup:

The default installation from `.griid--install` will fit most needs, but you can also build a custom griid setup:

1. `.griid--base` is always the first thing. It gives you support for multi-row grids, and is required by everything else
2. `griid--inline-alignment` adds support for using alignment classes in your markup
       `.top`, `.middle`, `.bottom` give you inline overrides for cell content vertical alignment
       `.left`, `.center`, `.right` give you inline overrides for (when applied to a grid) orphan alignment and (when applied to a cell) content alignment
3. `.griid--single-row` adds support for single-row grids with equal-width, equal-height cells. By default these cells do NOT have gutters or row spacing
4. `.griid--row-spacing` (NOT included in `.griid--install`) adds gutters and row spacing (both @griid--gutter) to `.griid .cell*x` grids. Beware that this will frame the entire `.griid .cell*x` grids in a @griid-gutter space
5. `.griid--base`, with or without `.griid--inline-alignment` and`.griid--single-row`, still needs initialization.
  -            `.griid--initialize` gets you ready to go with single-row and multi-row columns
  -          Or run any of `.griid--initialize-equal-cells`, `.griid--initialize-unequal-cells`, or `.griid--initialize-row`

	**Note**:`.griid--install` is simply shorthand for `.griid--base; .griid--inline-alignment; .griid--initialize`


###C. Overriding default variables

The initialization functions can be re-run at any point to re-initialize with new settings or two wipe over customizations.

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
	              
##griid LESS functions and mixins

griid has support for all sorts of adjustments. These are especially useful for media queries - turn your 1/3 - 2/3 grid into 1/2 - 1/2 quickly and cleanly. Progressively resize a grid first from 6 columns (the factory default max columns for griid) to 5, then 4, 3, 2, 1.

###A. Alignment
1. `.griid--vertical-align(@args:@griid--item-v-align)`
`.griid--top` (mixin)
`.griid--middle` (mixin)
`.griid--bottom` (mixin)
    Change the vertical alignment of cell contents
    Default re-initializes

2. `.griid--orphan-align(@alignment:@griid--orphan-h-align)`
`.griid--left` (mixin)
`.griid--center` (mixin)
`.griid--right` (mixin)
    Change how orphan cells in multi-row grids are aligned
    Default re-initializes

###Grid adjustment

####B. Adjusting `.griid .cell` grids
3. `.griid--row`
    Turn a multi-row grid into a single-row grid with equal-height and equal-width cells


4. `.griid--resize-row(@treatAs:1)`
    Turn a single-row grid into a multi-row grid with a **@treatAs** number of cells per row
    Default turns the cells into blocks


####C. Adjusting `.griid .cell-n-d` grids
5. `.griid--resize-one-unequal((@treatAsNumerator:1, @treatAsDenominator:2,) @targetNumerator, @targetDenominator)`
Resize one fractional width   
  - `.griid--resize-one-unequal(@targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` cells into `.cell-1-2`    
  - `.griid--resize-one-unequal(@treatAsNumerator, @treatAsDenominator, @targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` into `.cell-@treatAsNumerator-@treatAsDenominator`


6. `.griid--resize-unequal(@treatAsNumerator:1, @treatAsDenominator:2(, @numeratorOfLargest, @denominatorOfLargest))`
  -    Resize all fractional smaller than or equal to target
  -    Default turns all fractional widths into `.cell-1-2`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator)` turns all fractional widths into `cell-@treatAsNumerator-@treatAsDenominator`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator, @numeratorOfLargest, @denominatorOfLargest)` turns all fractions equal to or smaller than **@numeratorOfLargest/@denominatorOfLargest** into `cell-@treatAsNumerator-@treatAsDenominator`


####D. Adjusting `.griid-x .cell` grids

#####Resizing from one column count to another
7. `.griid--resize-one-equal((@treatAs:1,) @target)`
    Resize one equal width
    `.griid--resize-one-equal(@target)` will turn cells in an `.griid-@target` into blocks

8. `.griid--resize-equal(@treatAs:1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))`
    Resize all equal widths, optionally starting at a certain number or in a range
    Default turns cells in all `.griid-x` grids into blocks
    `.griid--resize-equal(@treatAs)` turns all `.griid-x` grids into `.griid-@target` grids

#####Dropping the column count by one or more

9. `.griid--drop-one((@dropBy:1,) @target)`
    Drops one or more columns from "one" specified grid type.
  -    `.griid--drop-one(@target)` will turn `.griid-@target` into `.griid-(@target-1)`
  -    `.griid--drop-one(@dropBy, @target)` will turn `.griid-@target` into `.griid-(@target-@dropBy)`

10. `griid--drop(@dropBy: 1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))`
    Make all equal widths a larger fraction of the whole,
    -    optionally by a certain number,
    -    by a certain number from a certain width
    -    or by a certain number within a certain width range

    Default makes all equal widths the next larger fraction  
  - `griid--drop(@dropBy)` drops **@dropBy** columns from all `.griid-x` grids
  - `griid--drop(@dropBy, @minColCount)` drops  **@dropBy** columns `.griid-x` grids that have at least **@minColCount** columns
  - `griid--drop(@dropBy, @minColCount, @maxColCount)` drops **@dropBy** columns from grids between `.griid-@minColCount` and `.griid-@maxColCount` (inclusive)

11. `.griid--resize(@treatAs:1)`
    Turns *all* grids (`.griid .cell`, `.griid-x .cell`, and `.griid .cell-n-d`) into `.griid-@treatAs`
    
    Default turns all cells into blocks
