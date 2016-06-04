# markup for griid's three grid types

Single-row grids with equal-width, equal-height cells look like `.griid > .cell`

Multi-row grids with equal-width cells look like
`.griid-x > .cell*n` (there will be x cells per row)

Multi-row grids with unequal-width cells look like
`.griid` for the grid, `.cell-n-d` for a cell n/d of the row width. New rows will be made automatically, but if your grid has a gutter you'll need to add `.row-end` to the last cell in each row (this is not necessary if there's only one row). Full-width cells are `.cell-1-1` or `.cell-full`, and never require `.row-end`.

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
